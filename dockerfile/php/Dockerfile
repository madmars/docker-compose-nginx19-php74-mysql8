FROM php:7.4.0-fpm-alpine

RUN apk update --no-cache && \
  apk upgrade --update-cache --available && \
  apk add git oniguruma-dev libressl-dev zlib-dev libpng-dev libxml2-dev autoconf gcc g++ make

RUN docker-php-ext-install mysqli && \
  docker-php-ext-install tokenizer && \
  docker-php-ext-install json && \
  docker-php-ext-install xml && \
  docker-php-ext-install ctype && \
  docker-php-ext-install bcmath && \
  docker-php-ext-install opcache && \
  docker-php-ext-install pdo_mysql && \
  docker-php-ext-install pdo && \
  docker-php-ext-install mbstring && \
  docker-php-ext-install iconv && \
  docker-php-ext-install phar && \
  docker-php-ext-install gd && \
  pecl install apcu-5.1.18 && \
  docker-php-ext-enable apcu
