# サーバーの基本情報

大学で借りられるパブリッククラウドVPSを利用しています.  
[パブリッククラウドVPSサービス(学内専用)](https://www.cis.kit.ac.jp/services/public_cloud_vps/)

## 接続先(SSH)

- Hostname: www.monodukuri.kit.ac.jp
- Port: 22

## ファイル構成

Wordpressのファイルやdocker-compose.ymlなど，運用に必要なファイルは全て
`/usr/local/workspace`にあります

```sh
.
├── backup
│   ├── 2022-05-21_12-10-22_UODLPAXB01.tar.gz <- バックアップファイル
│   ├── 2022-05-21_20-55-33_RCDLPAW601.tar.gz
│   ├── index.php
│   └── kit_factory_wordpress.sql <- データベースがダンプされたファイル．基本的に触らない
├── cis_cert
│   ├── certs <- 証明書が入ってる
│   ├── chain <- 中間証明書が入ってる
│   ├── conf.d <- sslのコンフィグが入ってる
│   └── private <- 秘密鍵が入ってる
├── cron
│   ├── crontab <- 定期実行の定義が入ってる
│   └── Dockerfile <- 触らない
├── docker-compose.yaml <- wordpressやデータベースを管理するファイル．基本的に触らない
├── kit_factory_wordpress.sql <- データベースのダンプファイル．
├── kit-wp
│   ├── wp-config.php <- 設定に問題がある場合に編集する．あまり触らない
│   └── wp-content <- テーマなどが格納されているフォルダ．まあまあ触る
└── wordpress
    └── Dockerfile <- wordpressのイメージを定義しているファイル．基本的に触らない
```

### テーマファイルの中身

テーマファイルは`/usr/local/workspace/kit-wp/wp-content/themes/Factory`にあります．  
表示に関わる部分なので，ある程度編集する機会があると思います．

```sh
/usr/local/workspace/kit-wp/wp-content/themes/Factory

.
|-- archive.php
|-- css
|   `-- styles.css
|-- footer.php
|-- functions.php
|-- gulpfile.js
|-- header.php
|-- img -> ./src/img
|-- index.php
|-- js
|   |-- bundle.js
|   `-- bundle.min.js
|-- package.json
|-- package-lock.json
|-- page_home.php <- トップページに関するファイル．Wordpressの管理画面では編集できないので，ここを直接弄ることになる．
|-- page_home.php.old
|-- page.php
|-- single.php <-　記事の表示に関わるページ
|-- src
|   |-- img <- ここにある画像が参照されるので，差し替える場合は名前に注意
|   |   |-- Document.jpg
|   |   |-- Factory.jpg
|   |   |-- Lathe.jpg
|   |   |-- Logo.ai
|   |   |-- Logo.png
|   |   |-- Map.ai
|   |   |-- Staff_Working.jpg
|   |   |-- StudentStaff.jpg
|   |   |-- temp_image.jpg
|   |   `-- \343\202\242\343\202\273\343\203\203\343\203\210\ 1.svg
|   |-- js
|   |   `-- main.js
|   `-- scss
|       |-- archive.scss
|       |-- colors.scss
|       |-- footer.scss
|       |-- page_home.scss
|       |-- page_staff.scss
|       |-- single.scss
|       |-- styles.scss
|       `-- variable.scss
`-- style.css
```

## その他

### スペック

- CPU: 仮想3コア
- ストレージ: SSD100GB
- メモリ: 2GB

### OS

```bash
$ bat -p /etc/os-release
NAME="Ubuntu"
VERSION="20.04.4 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.4 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```
