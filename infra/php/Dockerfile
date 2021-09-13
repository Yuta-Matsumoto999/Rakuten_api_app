FROM php:8.0-fpm-buster

SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

# CORY php.ini
COPY ./php.ini /usr/local/etc/php/php.ini

# Composer install
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

# install Node.js
COPY --from=node:14.17 /usr/local/bin /usr/local/bin
COPY --from=node:14.17 /usr/local/lib /usr/local/lib

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath

WORKDIR /work