# Set master image
FROM php:7.2-fpm-alpine

# Set working directory
WORKDIR /var/www/html

# Install PHP Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy existing application directory permissions
COPY --chown=www-data:www-data . .

# Change current user to www
USER www-data