FROM php:7.4-fpm

RUN apt-get update

#zip unzipインストール
RUN apt-get install -y zip unzip

#pdoインストール
RUN docker-php-ext-install pdo_mysql

#composerインストール
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN composer config -g repos.packagist composer https://packagist.jp

#gitインストール
RUN apt-get update
RUN apt-get install -y git

#npmインストール
RUN apt-get install -y nodejs
RUN apt-get install -y npm

#xdebugインストール
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

#phpredisインストール
RUN git clone https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis
RUN docker-php-ext-install redis

#GDインストール
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
        && docker-php-ext-install gd

#PHP zip extension有効化
RUN apt-get update && apt-get -y install libzip-dev
RUN docker-php-ext-install zip
