FROM php:5.6-apache

COPY config/php.ini /usr/local/etc/php/
COPY sources.list /etc/apt/

# 安装并配置GD库和imagemagick
RUN apt-get update && apt-get install -y \
	bzip2 \
	libcurl4-openssl-dev \
	libfreetype6-dev \
	libicu-dev \
	libjpeg-dev \
	libpng12-dev \
	libpq-dev \
	libxml2-dev \
	imagemagick \
	libmagickwand-dev \
	&& rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd mbstring intl mysql pdo_mysql zip exif

# PECL extensions
RUN pecl install imagick \
	&& docker-php-ext-enable imagick

RUN a2enmod rewrite


