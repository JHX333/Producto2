FROM php:8.2-apache

RUN apt-get update && apt-get install -y \
    libzip-dev unzip git curl

RUN docker-php-ext-install pdo pdo_mysql zip

RUN a2enmod rewrite

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

COPY . .

COPY apache/000-default.conf /etc/apache2/sites-available/000-default.conf

RUN composer install

RUN chown -R www-data:www-data /var/www/html