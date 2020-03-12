FROM php:7.3-fpm

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


