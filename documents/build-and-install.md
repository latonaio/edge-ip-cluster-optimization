# ビルドとインストール

- 公式リポジトリからソースコードを取得します。

```bash
git clone https://github.com/SoftEtherVPN/SoftEtherVPN.git
cd SoftEtherVPN
git submodule update --init --recursive
```

- (オプション) [softether-latona.patch](../softether-latona.patch) パッチを適用します。このパッチには以下の機能が含まれています。

	- オープンソース版で無効化されている機能の有効化
	- ダイナミック DNS 機能の無効化
		- Latona の環境では必要ないためです。
	- DHCP パケットからのデフォルトゲートウェイの削除機能 (`RemoveDefGwOnDhcp`) の追加
		- Latona ではリモートアクセス用 VPN を想定して構築しており、VPN 経由のインターネットアクセスは不要なためです。このような運用の場合にこのオプションを有効にすると、インターネット接続による不要な帯域の消費を防ぐことができます。

- ビルドを実行します。

(SoftEther VPN は root 権限で動作するため、リスク軽減のためのオプション等を付加しています。)

```bash
CMAKE_INSTALL_PREFIX=/opt/softether \
CFLAGS="-march=native -mtune=native -pipe -fno-plt -fstack-protector-strong -Wl,-O1,--sort-common,--as-needed,-z,relro,-z,now" \
./configure

VERBOSE=1 make -C build -j$(nproc)
```

- インストールを行います。

```bash
sudo make -C build install
```

- Jetson 端末起動時に自動で起動するよう設定し、SoftEther VPN Server を起動します。

```bash
sudo mkdir -p /etc/systemd/system/softether-vpnserver.service.d
sudo bash -c 'cat <<EOF > /etc/systemd/system/softether-vpnserver.service.d/override.conf
[Unit]
Wants=NetworkManager-wait-online.service
After=NetworkManager-wait-online.service
EOF
'

sudo systemctl daemon-reload
sudo systemctl enable --now softether-vpnserver.service
```
