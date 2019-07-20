# 参考
https://qiita.com/tomitz/items/722960b124600391f491

# 前提
この時点で`docker-compose`などはインストールされていたので省略

# docker-compose.yml作成
```
version: '3'
services:
  app:
    build:
      context: ../
      dockerfile: ./docker/Dockerfile
    image: python:3.7
    volumes:
      - '../:/var/www/html'
    container_name: python
    tty: true
    working_dir: '/var/www/html'
```

# Dockerfile作成
```
FROM python:3.7
ADD . /var/www/html
WORKDIR /var/www/html
RUN pip install -r ./requirements.txt
```

# ビルド
`$ docker-compose up -d --build`

# PyCharmからDockerにつないでみる

# hello.py実行してみる
