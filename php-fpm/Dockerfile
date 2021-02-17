FROM php:7.4-fpm

RUN apt-get update

#zip unzipインストール
RUN apt-get install -y zip unzip

#pdoインストール
RUN docker-php-ext-install pdo_mysql

#composerインストール
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

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
