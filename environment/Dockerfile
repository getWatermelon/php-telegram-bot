FROM php:7.4-apache

RUN apt update \
	&& apt install -y libicu-dev \
		git \
		wget \
		zlib1g-dev \
        libzip-dev \
        openssh-client

RUN curl -s https://getcomposer.org/installer > composer-setup.php \
       && php composer-setup.php --install-dir=/usr/bin --filename=composer

RUN pecl install xdebug-2.8.1 \
	&& docker-php-ext-enable xdebug \
	&& a2enmod rewrite \
	&& docker-php-ext-install pdo_mysql intl zip opcache

COPY ./environment/php.ini $PHP_INI_DIR/php.ini
