FROM php:7.2-fpm


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
        libxml2 \
        libxml2-dev \
        libxslt1-dev \
        nodejs \
        npm \
        && pecl install mcrypt-1.0.3 \

# Теперь устанавливаем сами модули

    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) \
        iconv \
        mbstring \
        mysqli \
        pdo_mysql \
        zip \
        bcmath \
        soap \
# Конфигурирование и затем установка gd	
    && docker-php-ext-configure gd \
          --with-freetype-dir \
          --with-jpeg-dir \
    && docker-php-ext-install -j$(nproc) gd \ 

    && docker-php-ext-configure intl \ 
    && docker-php-ext-install intl \ 
    && docker-php-ext-install sockets \ 
    && docker-php-ext-install xsl


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Протетсировать это
# npm rebuild node-sass


# Указываем рабочую директорию для PHP
WORKDIR /var/www

# Запускаем контейнер
# Из документации: The main purpose of a CMD is to provide defaults for an executing container. These defaults can include an executable, 
# or they can omit the executable, in which case you must specify an ENTRYPOINT instruction as well.
CMD ["php-fpm"]