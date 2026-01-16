FROM serversideup/php:8.4-frankenphp

USER root

# add additional extensions here:
RUN install-php-extensions \
    pdo_mysql \
    gd \
    intl \
    zip \
    opcache \
    redis

USER www-data
COPY --chown=www-data:www-data . /var/www/html
