FROM php:8.1-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql

ENV COMPOSER_ALLOW_SUPERUSER=1

COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer

COPY ./app .

RUN composer install --optimize-autoloader

RUN chown -R www-data:www-data /var/www/html

RUN chmod -R 755 /var/www/html

RUN chmod -R 777 /var/www/html/storage

RUN chmod -R 777 /var/www/html/bootstrap/cache

# RUN php artisan migrate