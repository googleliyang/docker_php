FROM php:7.2
MAINTAINER joah <xxxxx@xx.com>


# 常用工具
RUN apt-get update && apt-get install -y libzip-dev git curl wget cron vim locales libfreetype6-dev mariadb-client \
  && rm -rf /var/lib/apt/lists/* \
  && pecl install zip \
  && docker-php-ext-enable zip \
  && docker-php-ext-install mysqli pdo_mysql gd bcmath

# Node
RUN add-apt-repository ppa:chris-lea/node.js \
    && apt-get update \
    && apt-get install nodejs \
    && apt install nodejs-legacy \
    && npm install n -g

# 安装与配置 composer
# Composer 官方安装脚本 https://getcomposer.org/download/
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer \
    && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
    && . ~/.bashrc \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com


# 配置 git
# RUN git config --global user.name "ubuntu" \
#   && git config --global user.email "xxxx@xx.com"
