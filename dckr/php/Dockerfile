# TODO latest php (lots of things isn't compatible yet)
FROM php:7.1-apache

# Installing necessary packages
# TODO latest php - remove libpng12-dev, libmcrypt-dev
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y curl git zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libicu-dev libmcrypt-dev && \
    curl -sL https://deb.nodesource.com/setup_8.x | bash && \
    apt-get install -y nodejs

# Enabling php extension
# TODO latest php - remove mcrypt
RUN docker-php-ext-install mysqli && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd && \
    docker-php-ext-install zip && \
    docker-php-ext-install intl && \
    docker-php-ext-install mcrypt && \
    docker-php-ext-install bcmath

# Setting apache + installing composer
RUN a2enmod rewrite && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    composer global require "hirak/prestissimo" && \
    composer global require "sllh/composer-versions-check"

#Cleaning mess
RUN apt-get clean -y && apt-get autoclean -y && apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

WORKDIR /var/www/html/
