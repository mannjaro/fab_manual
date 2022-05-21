<!-- omit in toc -->
# 運用サーバーへの接続方法

サーバーの接続には[SSH](https://webkaru.net/linux/ssh-command/)という方式を用います．  
公開鍵認証方式を用いるので，以下の手順で公開鍵・秘密鍵を設定してください．

## 公開鍵と秘密鍵を作る

### 鍵の作成(Windows)

```bash
ssh-keygen -t rsa -b 4096
```

保存場所を聞かれるのでデフォルト(C:\Users\{ユーザー名}/\.ssh/id_rsa)でよければそのままエンター

パスフレーズはサーバーの接続時に聞かれるので，適当に設定しておく(面倒であれば空白でも可)

### 鍵を移す

C:\Users\{ユーザー名}/\.ssh/にid_rsaとid_rsa.pubファイルがあるので，**id_rsa.pub**を管理者に渡し登録してもらう

!> **id_rsaは秘密鍵なので絶対に外部に漏らさないこと**

### Mac/Linix

基本的にはWindowsの場合と同様に行う
ファイルの保存先がWindowsと異なるので注意すること

- Mac: `/Users/{ユーザー名}/.ssh/id_rsa`
- Linux: `/home/{ユーザー名}/.ssh/id_rsa`

## 接続する

管理者からもらったユーザー名とパスワードを用いて接続を行う

```bash
ssh -i ~/.ssh/id_rsa {ユーザー名}@www.monodukuri.kit.ac.jp
```

例: someuserというユーザーで接続する場合）

```bash
ssh -i ~/.ssh/id_rsa someuser@www.monodukuri.kit.ac.jp
```

また，sshで接続する際はconfigファイルを設置すると簡単に接続が可能になる  
configファイルは~/.ssh/configに配置する  
ユーザー名は適宜変更すること

```ini
Host kit_factory
  HostName www.monodukuri.kit.ac.jp
  User {ユーザー名}
  Port 22
  IdentityFile ~/.ssh/id_rsa
```

以降，接続時は

```bash
ssh kit_factory
```

と打つだけで接続が可能となる

以上が完了すると以下のようなファイル構成になる

```bash
.ssh
├── config
├── id_rsa
└── id_rsa.pub
```
