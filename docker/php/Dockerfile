FROM php:7.3.2-fpm-alpine3.9

WORKDIR /var/www/src

# 設定ファイルをコンテナ内にコピー
COPY ./php.ini /usr/local/etc/php/

RUN apk update && apk add --no-cache \
  emacs \
  libpng-dev \
  nodejs-npm \
  tzdata \
  && docker-php-ext-install \
     mysqli \
     pdo_mysql \
  && : "タイムゾーン設定(必要なファイルだけ抜き取る)" \
  && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  && : "不要パッケージの削除" \
  && apk del libpng-dev tzdata \
  && : "composerインストール" \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
