FROM php:8.0-fpm


RUN apt-get update && apt-get install -y \
     sqlite3 \
     libfreetype6-dev \
     libjpeg62-turbo-dev \
     libpng-dev \
     libgmp-dev \
     apt-utils \
     libpq-dev \
     libpng-dev \
     libzip-dev \
     zip unzip \
     git && \
     docker-php-ext-configure gd --with-freetype --with-jpeg && \
     docker-php-ext-install -j$(nproc) gd && \
     docker-php-ext-install pdo_mysql && \
     docker-php-ext-install bcmath && \
     docker-php-ext-install pdo  gmp  pcntl  sysvmsg exif  && \
     docker-php-ext-install zip && \
     apt-get clean && \
     rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./_docker/app/php.ini /usr/local/etc/php/conf.d/php.ini
#COPY ./_docker/app/php.ini /usr/local/etc/php/conf.d/php.ini

# Install composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
   --filename=composer \
   --install-dir=/usr/local/bin

WORKDIR /var/www

