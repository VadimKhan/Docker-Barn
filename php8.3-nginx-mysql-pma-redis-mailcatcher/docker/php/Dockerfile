FROM php:8.3-fpm-alpine

RUN apk add --no-cache \
    wget \
    grep \
    build-base \
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
    zip \
    libjpeg-turbo-dev \
    libpng-dev \
    libwebp-dev \
    freetype-dev \
    nodejs \
    npm \
  && docker-php-ext-install \
    pdo \
    pdo_mysql \
    mysqli \
    pcntl \
    gd \
    exif \
    zip \
    soap \
  && pecl install -o -f redis \
  && rm -rf /tmp/pear \
  && docker-php-ext-enable redis \
  && rm -rf /var/cache/apk/*

COPY --from=composer /usr/bin/composer /usr/bin/composer

ARG USER=docker
ARG UID=1000
RUN addgroup -g $UID -S $USER \
  && adduser -u $UID -S $USER -G $USER \
  && mkdir -p /var/www \
  && chown -R $USER:$USER /var/www

USER $USER
