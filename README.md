wp-docker
=========

> https://hub.docker.com/_/wordpress

## ◯ How to use

### @docker-compose.yaml の中身

#### services
* 起動したい各コンテナの情報
* **image:** このイメージをもとにコンテナを作成
* **depends_on:** 依存関係の設定（WPはDBがないと機能しない）
* **environment:** 環境変数
* **volumes:** どこにマウントするかの設定
  * volumesの中にあるデータを参照できるようにする
  * コンテナは作って壊すというライフサイクルなので、volumesにデータを入れておくため

#### volumes
* データを入れておくところ

#### networks
* コンテナ同士を繋げる設定


### コンテナ起動

```
docker-compose up -d
```

* ```-d```: バックグラウンドで起動させる
* http://localhost:8080 で確認

### 停止

```
docker-compose stop
```

* コンテナは残る
* 後で up すればすぐ再開

### 不要になったら削除

```
docker-compose down
```

* 最初に停止
* コンテナ削除
* ネットワーク削除
* 環境リセット
* image と volume は削除されない


## ◯ 完全に削除する（DB含む）

テストや作り直し用。

```
docker-compose down -v
```

* volumeも削除
* DB初期化
* 完全クリーン


## ◯ Docker Desktop 終了コマンド

```
osascript -e 'quit app "Docker Desktop"'
```
