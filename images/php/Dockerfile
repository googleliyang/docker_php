FROM php:7.2-fpm
MAINTAINER jorah <xxxx@xx.net>


# install redis extension
ENV PHPREDIS_VERSION 3.0.0
RUN mkdir -p /usr/src/php/ext/redis \
    && curl -L https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
    && echo 'redis' >> /usr/src/php-available-exts \
    && docker-php-ext-install redis

# install extension
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev  \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr  --with-freetype-dir=/usr/freetype2 \
    && docker-php-ext-install gd pdo_mysql zip opcache
    # && docker-php-ext-enable gd



COPY ./config/php.ini /usr/local/etc/php/conf.d/

# copy opcahe.ini to docker container
COPY ./config/opcache-recommended.ini /usr/local/etc/php/conf.d/
