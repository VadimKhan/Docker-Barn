FROM php:8.2-fpm-alpine

RUN apk --no-cache add \
    build-base \
    wget \
    grep \
    libmemcached-dev \
    libmcrypt-dev \
    libxml2-dev \
    imagemagick-dev \
    pcre-dev \
    libtool \
    autoconf \
    unzip \
    libzip-dev \
    supervisor \
    libjpeg-turbo-dev \
    libpng-dev \
    libwebp-dev \
    freetype-dev \
&& rm -rf /var/cache/apk/* 

RUN docker-php-ext-install \
    pdo \
    pdo_mysql \
    mysqli \
    pcntl \
    gd \
    exif \
    zip \
    soap \
    && docker-php-ext-enable mysqli

COPY --from=composer /usr/bin/composer /usr/bin/composer

ARG USER=docker
ARG UID=1000

RUN addgroup -g $UID -S $USER && adduser -u $UID -S $USER -G $USER

USER $USER
