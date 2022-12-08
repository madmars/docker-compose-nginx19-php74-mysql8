FROM php:7.4.0-fpm-alpine

RUN apk update --no-cache && \
  apk upgrade --update-cache --available && \
  apk add git mysql-client oniguruma-dev libressl-dev zlib-dev libpng-dev libxml2-dev autoconf gcc g++ make imagemagick imagemagick-dev libzip libzip-dev

RUN pecl install apcu-5.1.18 && \
  docker-php-ext-enable apcu && \
  docker-php-ext-install gd mysqli tokenizer json xml ctype bcmath opcache pdo_mysql pdo mbstring iconv phar zip

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
  php composer-setup.php  && \
  php -r "unlink('composer-setup.php');" && \
  chmod +x composer.phar && \
  mv composer.phar /usr/local/bin/composer

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
  && chmod +x wp-cli.phar \
  && mv wp-cli.phar /usr/local/bin/wp \
  && wp package install wp-media/wp-rocket-cli:trunk --allow-root
