## ユーザアカウントの追加

VPN を利用するために必要なユーザアカウントを作成する手順です。

- 管理ツールを起動します。

```bash
/opt/softether/bin/vpncmd localhost -server -password:[管理用パスワード]
```

- 操作対象の仮想 HUB を指定します。

```
Hub [ハブ名]
```

- ユーザアカウントを作成します。

```
UserCreate [アカウント名] /realname:[アカウント名] /group:default /note:
```

- ユーザアカウントにパスワードを設定します。

```
UserPasswordSet [アカウント名] /password:[パスワード]
```

- 他にもユーザアカウントが必要な場合、UserCreate と UserPasswordSet の手順を繰り返してください。

- 管理ツールを終了します。

```
exit
```
