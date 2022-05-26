# FROM php:8.0-fpm

# ENV TZ Asia/Tokyo

# RUN apt-get update && \
# 	apt-get install -y \
#     git \
#     unzip \
#     libzip-dev \
#     libicu-dev libonig-dev && \
# 	docker-php-ext-install pdo_mysql zip bcmath

# COPY ./docker/app/php.ini /usr/local/etc/php/php.ini

# COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

# WORKDIR /var/www

FROM php:7.4.9-fpm

COPY php.ini /usr/local/etc/php/

RUN apt update \
    && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip \
    && docker-php-ext-install pdo_mysql zip

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

WORKDIR /var/www