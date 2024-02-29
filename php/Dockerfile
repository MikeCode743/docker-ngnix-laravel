FROM php:8.2-fpm

WORKDIR /var/www
ADD . /var/www

RUN apt-get update -y --fix-missing && apt upgrade -y 

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www
COPY --chown=www:www . /var/www

# Install useful tools
RUN apt-get -y install apt-utils nano wget dialog vim

# Install important libraries
RUN echo "Install important libraries"
RUN apt-get -y install --fix-missing \
    apt-utils \
    build-essential \
    git \
    curl \
    libcurl4 \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libzip-dev \
    zip \
    libbz2-dev \
    locales \
    libmcrypt-dev \
    libicu-dev \
    libonig-dev \
    libxml2-dev \
    libpq-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libmagickwand-dev \ 
    && rm -rf /var/lib/apt/lists/*

RUN echo "Install dependencies docker"
RUN docker-php-ext-install \
    exif \
    pcntl \
    bcmath \
    ctype \
    curl \
    iconv \
    xml \
    soap \
    pcntl \
    mbstring \
    bz2 \
    zip \
    intl \
    pdo \
    pdo_pgsql \ 
    pgsql \ 
    -j$(nproc) gd

RUN pecl install imagick

# Install Postgre PDO
RUN docker-php-ext-configure \
    pgsql -with-pgsql=/usr/local/pgsql 
RUN docker-php-ext-configure \
    gd --with-freetype --with-jpeg 


#composer install
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-enable imagick

# RUN composer require simplesoftwareio/simple-qrcode

# RUN php artisan vendor:publish --provider="SimpleSoftwareIO\QrCode\QrCodeServiceProvider"

# RUN apt-get update && \
#     apt-get install -y libmagickwand-dev --no-install-recommends && \
#     rm -rf /var/lib/apt/lists/* && \
#     pecl install imagick && \
#     docker-php-ext-enable imagick

# ENTRYPOINT ["composer install"]