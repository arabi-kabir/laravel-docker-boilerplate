FROM php:8.1-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html

USER www-data

# Permission for storage
#RUN chmod 775 -R www-data:www-data /var/www/html/storage

#COPY --chown=nginx:nginx . /var/www
#RUN chown -R nginx:www-data /var/www/html/storage
#RUN chmod -R 777 /var/www/storage
#RUN chmod -R 755 /var/www/html/storage
#RUN chmod -R 755 /var/www/storage/logs
#RUN chmod -R 755 /var/www/storage/logs/laravel.log

#RUN chown -R www-data /var/www/html/storage

#ADD . /var/www/html
#RUN chown -R www-data:www-data /var/www/html/storage
