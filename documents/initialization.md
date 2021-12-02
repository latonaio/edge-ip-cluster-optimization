## 初期設定

- SoftEther VPN の CLI 設定ツールを起動します。

```bash
/opt/softether/bin/vpncmd -server localhost
```

- サーバ管理パスワードを設定します。

```
ServerPasswordSet [パスワード]
```

- デフォルトで存在する仮想 HUB を無効にします。

```
Hub DEFAULT
Offline
```

- リモートアクセス用の仮想 HUB を作成します。

```
HubCreate [ハブ名] /password:[ハブ管理パスワード]
```

- この仮想 HUB とローカル LAN をブリッジ接続させます。

```
BridgeCreate [ハブ名] /device:[LAN カード名 (eth0 等)]
```

- 操作対象の仮想 HUB を指定します。

```
Hub [ハブ名]
```

- 仮想 HUB 名を知らなければアクセスできないよう設定します。(未認証ユーザにこの仮想 HUB の存在を開示しないことにより、セキュリティが向上します)

```
SetEnumDeny
```

- ユーザが所属するグループを作成します。(ここではグループ名は default としています)

```
GroupCreate default /realname:default /note:
```

- (オプション) アカウントに強力なパスワードを強制する場合など、ユーザによるパスワードの変更機能を無効化するには、次のコマンドを実行します。

```
GroupPolicySet default /name:FixPassword /value:yes
```

- (オプション: パッチを適用した場合) VPN クライアントが LAN 内にしか接続されないよう (WAN 側・インターネット側に抜けないよう) 設定します。

※ このオプションはセキュリティ向上のためのものではありません。このオプションを有効にしても、ユーザがデフォルトゲートウェイを手動で設定すれば WAN 側にも接続できます。

```
ExtOptionSet RemoveDefGwOnDhcp /value:1
```

- 一旦管理ツールを終了させます。

```
exit
```
