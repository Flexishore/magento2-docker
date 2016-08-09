FROM php:7-fpm

MAINTAINER Kos Rafał <rafal.k@flexishore.com>

RUN apt-get update \
    && apt-get install -y zlib1g-dev libjpeg-dev libpng-dev libfreetype6-dev

RUN pecl install redis mhash soap zip iconv \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable zip

RUN docker-php-ext-install mysqli pdo pdo_mysql     

# Install bc-math
RUN apt-get install -y mcrypt libmcrypt-dev
RUN docker-php-ext-configure mcrypt
RUN docker-php-ext-install mcrypt
    
# Install intl
RUN apt-get install -y libicu-dev
RUN docker-php-ext-install intl

# Install bc-math
RUN docker-php-ext-configure bcmath
RUN docker-php-ext-install bcmath

# Install GD
RUN docker-php-ext-configure gd --with-freetype-dir=/usr
RUN docker-php-ext-install gd exif