# プロジェクトのはじめ方

## コードディレクリを初期化する

coposer dockerイメージを使って、wwwディレクリを初期化します。

```
mkdir www
docker run --rm -v $(pwd):/app composer/composer require "laravel/lumen-installer"
mkdir public
```

または、


```
docker run --rm -v $(pwd):/app composer/composer create-project --prefer-dist laravel/lumen www
```





# docker runする場合

## docker build

Dockerfileから、dockerイメージをビルドします。

```
docker build -t php-lumen .
```

## docker run

docker runコマンドで、起動します。

```
docker run -p 8080:80 -w /var/www/public -d -v ./www:/var/www -name webapp php-lumen
```


# docker-composeする場合

## docker-compose.yml

```
version: '2'
services:
  php-laravel:
    build: admin
    ports:
      - 8082:80
    volumes:
      - ./admin/www:/var/www
    working_dir: /var/www/public
```


## docker-compose build

```
docker-compse build
```

## docker-compose up -d

```
docker-compose up -d
```

