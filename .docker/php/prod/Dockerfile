FROM php:7.4-fpm

# Copy composer.json
COPY ./src/composer.json /var/www/html/

# Set working directory
WORKDIR /var/www/html

# Install dependencies
RUN apt-get update
RUN apt-get install -y npm
RUN apt-get install -y build-essential
RUN apt-get install -y libonig-dev
RUN apt-get install -y libpng-dev
RUN apt-get install -y libjpeg62-turbo-dev
RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y locales
RUN apt-get install -y libzip-dev
RUN apt-get install -y zip
RUN apt-get install -y jpegoptim optipng pngquant gifsicle
RUN apt-get install -y unzip
RUN apt-get install -y curl
RUN apt-get install -y libicu-dev

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install zip
RUN docker-php-ext-install exif
RUN docker-php-ext-install pcntl
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install gd
RUN docker-php-ext-install intl

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy existing application directory contents
COPY ./src /var/www/html

# Copy existing application directory permissions
COPY --chown=www:www ./src /var/www/html

# Change current user to www
USER www

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]