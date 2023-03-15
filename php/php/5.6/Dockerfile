FROM php:5.6-fpm

# Устанавливаем вначале зависимости для модулей
RUN apt-get update && apt-get install -y \
        curl \
        wget \
        git \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libonig-dev \
        libzip-dev \
        libmcrypt-dev \
#        && pecl install mcrypt-1.0.3 \

# Теперь устанавливаем сами модули

#    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) \
        iconv \
        mbstring \
        mysqli \
        pdo_mysql \
        zip \
        bcmath \
# Конфигурирование и затем установка gd	
    && docker-php-ext-configure gd \
          --with-freetype-dir \
          --with-jpeg-dir \
    && docker-php-ext-install -j$(nproc) gd 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Добавим свой php.ini
ADD php.ini /usr/local/etc/php/php.ini

# Указываем рабочую директорию для PHP
WORKDIR /var/www

# Запускаем контейнер
# Из документации: The main purpose of a CMD is to provide defaults for an executing container. These defaults can include an executable, 
# or they can omit the executable, in which case you must specify an ENTRYPOINT instruction as well.
CMD ["php-fpm"]




#==================================================
#=== Установленные расширения
#==================================================

# bcmath
# Core
# ctype
# curl
# date
# dom
# ereg
# fileinfo
# filter
# ftp
# gd
# hash
# iconv
# json
# libxml
# mbstring
# mhash
# mysqli
# mysqlnd
# openssl
# pcre
# PDO
# pdo_mysql
# pdo_sqlite
# Phar
# posix
# readline
# Reflection
# session
# SimpleXML
# SPL
# sqlite3
# standard
# tokenizer
# xml
# xmlreader
# xmlwriter
# zip
# zlib
