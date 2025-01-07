#################################################################
## Lemonade payments
## Devops Engineer - Technical Assessment - submission
### Submitted by: Zack Mwangi [ zackmwangi@gmail.com ]
### Date: Jan 07, 2025

#---

#    ### Section 2: Coding Challenge
#    #### Q10: Write a Dockerfile to containerize a Laravel application.
#    > ##### Ans:
###################################################################
#
#
#
# Set the PHP Version to use for the Laravel installation
# Ensure this matches with your dev environment or the official Lemonade dev version
FROM php:8.3-fpm-alpine3.21

# Set the working directory
WORKDIR /var/www

#Install system dependencies
RUN apk --no-cache add \
    build-base \
    libpng-dev \
    libjpeg-turbo-dev \
    libwebp-dev \
    libxpm-dev \
    freetype-dev \
    libzip-dev \
    zip \
    unzip \
    git \
    bash \
    fcgi \
    libmcrypt-dev \
    oniguruma-dev \
    postgresql-dev

# Clear cache
RUN rm -rf /var/cache/apk/*

# Install PHP extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql mbstring zip exif pcntl bcmath opcache

    # Install composer related(using definitions in composer config)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-install pdo mbstring

# Copy over application code
COPY . /var/www

#Adjust directory permissons
COPY --chown=www-data:www-data . /var/www

# Change current user to www
USER www-data

# Expose port - Ensure local or Kubernetes service config has the relevant port mapping to expose traffic
# Default 8181 for artisan
EXPOSE 8181

# Run the app when container launches and serve with php-fpm
CMD php artisan serve --host=0.0.0.0 --port=8181