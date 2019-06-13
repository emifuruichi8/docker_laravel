FROM php:7.3.2-fpm-alpine3.9

WORKDIR /var/www/src

# 設定ファイルをコンテナ内にコピー
COPY ./php.ini /usr/local/etc/php/

RUN apk update && apk add --no-cache \
  freetype-dev \
  libjpeg-turbo-dev \
  libpng-dev \
  libmcrypt-dev \
  git \
  vim \
  emacs \
  unzip \
  tzdata \
  libltdl \
  nodejs-npm \
  && docker-php-ext-install \
     pdo_mysql \
     mysqli \
     mbstring \
     gd \
     iconv \
  && : "タイムゾーン設定" \
  && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  && apk del tzdata \
  && : "composerインストール" \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
