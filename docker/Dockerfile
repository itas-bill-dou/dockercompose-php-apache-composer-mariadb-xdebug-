# PHP Version Support - https://xdebug.org/docs/compat#versions
# Be careful the compatibility issue between Xdebug version and PHP version

ARG PHP_VERSION=8.1
# Use the official PHP image as the base image
FROM php:${PHP_VERSION}-apache

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    unzip \
    git \
    && docker-php-ext-install pdo pdo_mysql zip

# Install PHP extensions
RUN docker-php-ext-install zip

# Enable Apache modules
RUN a2enmod headers ssl rewrite \
    && mkdir -p /etc/apache2/ssl

# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Without a specified version, it will install the latest version - https://xdebug.org/download/historical
# PHP8
RUN pecl install xdebug && docker-php-ext-enable xdebug

# PHP7
# RUN pecl install xdebug-3.1.6 && docker-php-ext-enable xdebug

# Configure Xdebug
COPY xdebug.ini /usr/local/etc/php/conf.d/

# Copy SSL certificates and Apache configuration
COPY ssl/cert.pem /etc/apache2/ssl/cert.pem
COPY ssl/cert-key.pem /etc/apache2/ssl/cert-key.pem
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Set the working directory
WORKDIR /var/www/html

# Copy your application code into the container
COPY ../ /var/www/html

# Set ownership to www-data for all files and folders
RUN chown -R www-data:www-data /var/www/html

EXPOSE 443