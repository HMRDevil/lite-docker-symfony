FROM php:8.1-fpm

# set main params
ENV APP_HOME /var/www/html
ENV USERNAME=www-data

# install dependencies and enable PHP modules
RUN apt-get update && apt-get install -y zlib1g-dev g++ git libicu-dev libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

# put php config for Symfony
COPY ./docker/nginx/www.conf /usr/local/etc/php-fpm.d/www.conf
COPY ./docker/nginx/php.ini /usr/local/etc/php/php.ini

# set working directory
WORKDIR $APP_HOME

USER ${USERNAME}

# copy source files
COPY --chown=${USERNAME}:${USERNAME} . $APP_HOME/

USER root
