# ユーザーの追加方法

VPSサーバーに新規ユーザーを作成する手順

## ユーザーに頼むこと

1. 追加対象のユーザーに公開鍵と秘密鍵を作成してもらう
2. サーバーに追加するユーザー名とパスワードを決めてもらう（英数の任意の名前とパスワード）
3. 公開鍵と，パスワードをもらう

## サーバー上ですること

1. ユーザーを追加する

```sh
sudo adduser {ユーザー名}
```

2. パスワードを聞かれるので，決めてもらったパスワードを設定する．（確認用に2回入力させられる）

```sh
su {ユーザー名}
```

でユーザーを切り替える

3. 適当な場所にもらった公開鍵を配置する

4. `.ssh`ディレクトリと`authorized_keys`ファイルを作成する

```sh
mkdir -p ${HOME}/.ssh
cat {秘密鍵のパス}.pub >> ${HOME}/.ssh/authorized_keys
chmod 600 ${HOME}/.ssh/authorized_keys
chmod 700 ${HOME}/.ssh
```

5. `exit`で元のユーザーに戻る

6. 追加したユーザーをsudoersとdockerグループに追加する

```sh
sudo gpasswd -a {ユーザー名} sudo
sudo gpasswd -a {ユーザー名} docker
```

7. dockerデーモンを再起動する

```sh
sudo service docker restart
```
