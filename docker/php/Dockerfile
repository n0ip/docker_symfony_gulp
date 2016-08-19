FROM php:5.6-fpm

ENV TERM xterm

ARG UID
ARG GUID
RUN usermod -u $UID www-data
RUN groupmod -g $GUID www-data

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    apt-utils

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y \
        bash \
        vim \
        mc \
        cron \
        libmagickwand-dev \
        libmagickcore-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        librabbitmq-dev \
        libmcrypt-dev \
        libpng12-dev \
        libpq-dev \
        imagemagick \
        libcurl4-gnutls-dev \
        zlib1g-dev \
        libicu-dev \
        g++ \
#        php5-gd \
#        php5-imagick \
#        php5-pgsql \
#        php5-mcrypt \
        && pecl install imagick \
        && docker-php-ext-enable imagick \
        && pecl install amqp \
        && docker-php-ext-enable amqp \
        && docker-php-ext-install -j$(nproc) bcmath curl json xml iconv mcrypt pdo_pgsql opcache \
        && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
        && docker-php-ext-install -j$(nproc) gd \
        && docker-php-ext-configure intl \
        && docker-php-ext-install intl \
        && rm -rf /var/lib/apt/lists/*

ADD symfony.ini /usr/local/etc/php/conf.d

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

EXPOSE 9000