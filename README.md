## 設定

- .env.sample を.env に書き換える
  - 必要に応じて mysql や postgresql のユーザ名パスワードを変更する。
- docker-compose.yml は必要な Container のコメントアウトを外す
  - web → nginx
  - php → laravel
  - python → fastapi
  - db1 → postgres
  - db2 → mysql
  - pgadmin → postgres を GUI 管理
- Dockerfile
  - 例えば./container/python であれば、requirements.txt に入れたいパッケージ記載
  - python のバージョンを変えたかったら、Dockerfile の python:3.11 を変える
  - デフォルトは fastapi 入れてるので、必要に応じて変更する
  - php は laravel を想定
- Container が起動すると src フォルダと work フォルダが作られる
  - src フォルダは python と php のソースコードを格納
    - src/python src/php と自動的に作成されるので、ここでプロジェクトを作成する
  - work は各コンテナ間からアクセスできる共有ディレクトリを想定

## 起動方法

```bash
1.ビルドする
docker compose build

２．起動する
docker compose up -d

3.Containerに直接はいる場合は、container_nameを指定。
  例えばプロジェクトを作ったりpipで追加パッケージを入れるとか
docker compose exec python bash

4. Container停止
docker compose stop

※Containerを削除する場合は
docker compose down

※コンテナ再起動(停止と起動を同時に)
docker stop $(docker compose ps -a -q) && docker compose up -d
```
