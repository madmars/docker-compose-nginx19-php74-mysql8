FROM php:7.4.0-fpm-alpine

RUN apk update --no-cache && \
  apk upgrade --update-cache --available && \
  apk add git oniguruma-dev libressl-dev zlib-dev libpng-dev libxml2-dev autoconf gcc g++ make imagemagick imagemagick-dev libzip libzip-dev nodejs nodejs-npm

RUN pecl install apcu-5.1.18 && \
  docker-php-ext-enable apcu && \
  docker-php-ext-install gd && \
  docker-php-ext-install mysqli && \
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
  docker-php-ext-install zip

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
  php -r "if (hash_file('sha384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"  && \
  php composer-setup.php  && \
  php -r "unlink('composer-setup.php');" && \
  mv composer.phar /usr/local/bin/composer

RUN npm i -g yarn
