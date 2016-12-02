FROM php:7.0.13-fpm
MAINTAINER "Eduardo Leal" <me@lealeduardo.com>

RUN docker-php-ext-install pdo pdo_mysql


RUN apt-get update && apt-get install -y \
        libicu-dev libmcrypt-dev libxslt-dev zlib1g-dev \
    && docker-php-ext-install -j$(nproc) intl mcrypt xsl zip

# Install gd
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd



CMD ["php-fpm"]
