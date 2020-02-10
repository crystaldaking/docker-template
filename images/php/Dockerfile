# Main image
FROM php:7.2-fpm
# Author
MAINTAINER crystaldaking <crystal@crystalapps.by>
 
# Update and install modules for php and other
RUN apt-get update && apt-get install -y \      
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && apt-get install -y wget zip unzip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd pdo pdo_mysql
     
# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
 
# Install git
RUN apt-get install -y git
 
# Install phpunit
RUN wget https://phar.phpunit.de/phpunit-6.5.phar && \
        chmod +x phpunit-6.5.phar && \
        mv phpunit-6.5.phar /usr/local/bin/phpunit
 
 
# Install codecept
RUN wget http://codeception.com/codecept.phar && \
        chmod +x codecept.phar && \
        mv codecept.phar /usr/local/bin/codecept
  
 
# Workdir for php
WORKDIR /var/www
 
# Run container
# The main purpose of a CMD is to provide defaults for an executing container. These defaults can include an executable, 
# or they can omit the executable, in which case you must specify an ENTRYPOINT instruction as well.
CMD ["php-fpm"]