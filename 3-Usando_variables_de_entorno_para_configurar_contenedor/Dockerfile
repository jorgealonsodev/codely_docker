# Extraido de https://hub.docker.com/_/php
FROM php:7.2-apache

LABEL maintainer="jorgealonsodev@gmail.com"
LABEL application="hello"

# Ejecutamos los siguiente comandos para instalar la extension
RUN pecl install xdebug-2.6.0
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-install pdo pdo_mysql

# Muestra el valor por defecto

ENV DISPLAY_ERRORS="On"

# Copiamos los siguientes archivos a la imagen
COPY php.ini /usr/local/etc/php/
COPY index.php/ /var/www/html/