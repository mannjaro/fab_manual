# Dockerに関するコマンド

Wordpressの運用環境としてDocker Composeを利用しています．
DockerとDocker composeについてはここで説明しないので以下のサイトを参照してください．  
保守だけならこれらを理解しなくても多分なんとかなります．

- [Docker入門 - さくらのナレッジ](https://knowledge.sakura.ad.jp/13265/)
- [docker docs](https://docs.docker.com/)
- [Docker Compose - さくらのナレッジ](https://knowledge.sakura.ad.jp/16862/)
- [クィックスタート: Compose と WordPress](https://docs.docker.jp/compose/wordpress.html)

## 起動・停止に関するコマンド

> 以下のコマンドは`docker-compose.yml`ファイルがあるディレクトリ上(/usr/local/workspace)でのみ機能します

```bash
cd /usr/local/workspace
```

### Wordpressサーバーの起動

```bash
sudo docker-compose up -d
```

### Wordpressサーバーの停止

```bash
sudo docker-compose down
```

### Wordpressサーバー状態の確認

```bash
sudo docker-compose ps
```

### Wordpressサーバーの再ビルド

```bash
sudo docker-compose build
```

キャッシュを用いずにビルドする場合

```bash
sudo docker-compose build --no-cache
```

### 永続データの削除(使用する前にバックアップを確認すること！)

```bash
sudo docker volume rm workspace_db_data
sudo docker volume rm workspace_wp-content
```

## コマンドの利用ケース

### 作業のために一旦Wordpressサーバーを止める場合

```bash
cd /usr/local/workspace
sudo docker-compose down
```

作業が終わったら，サーバーを起動させる

```bash
sudo docker-compose up -d
```

### WordpressやPHPのバージョンを上げる場合

```bash
sudo docker-compose down
sudo docker-compose build --no-cache
sudo docker-compose up -d
```

### サーバー上から全てのデータを削除する場合

```bash
sudo docker-compose down
sudo docker volume rm workspace_db_data
sudo docker volume rm workspace_wp-content
```
