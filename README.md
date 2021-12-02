# edge-ip-cluster-optimization

edge-ip-cluster-optimization は、リモートアクセス用 VPN としての SoftEther VPN Server の Jetson 上でのセットアップと運用方法について記載しています。

## SoftEther VPN について

SoftEther VPN は、オープンソースの VPN ソフトウェアです。([GitHubリンクはこちら](https://github.com/SoftEtherVPN))

SoftEther VPN Server は多くのプロトコルに対応しており、公式クライアントだけではなく、その他のプロトコルのクライアント等様々なソフトウェア・端末から接続できます。

また、SSL/TLS を活用した VPN プロトコルをサポートしているため、ファイアウォール等の制限の厳しい環境からでも高い接続性を発揮します。

以上のように、他のソフトウェア・ハードウェアベースの VPN と比較して高い柔軟性を有します。

## 目次

- [ビルドとインストール](./documents/build-and-install.md)
- [初期設定](./documents/initialization.md)
- [ユーザアカウントの追加](./documents/user-account.md)
- [ポート開放の設定](./documents/open-ports.md)

## 参考

- [公式サイト](https://ja.softether.org/)