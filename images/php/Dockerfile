FROM php:7.0-fpm
MAINTAINER jorah <xxxx@xx.net>

# install extension
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install gd pdo_mysql zip opcache

COPY ./config/php.ini /usr/local/etc/php/conf.d/

# copy opcahe.ini to docker container
COPY ./config/opcache-recommended.ini /usr/local/etc/php/conf.d/
