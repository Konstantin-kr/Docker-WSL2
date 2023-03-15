FROM php:8.1.16-fpm

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

# Теперь устанавливаем сами модули

    && docker-php-ext-install -j$(nproc) \
        iconv \
        mbstring \
        mysqli \
        pdo_mysql \
        zip \
        bcmath \
# Конфигурирование и затем установка gd	
    && docker-php-ext-configure gd \
          --enable-gd \
          --prefix=/usr --with-jpeg --with-freetype \          
          
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