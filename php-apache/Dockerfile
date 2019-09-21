FROM php:apache
RUN apt-get update
# Install php extensions
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN pecl install redis && docker-php-ext-enable redis

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
COPY ./conf/php-conf.ini $PHP_INI_DIR/conf.d/

ENV APACHE_DOCUMENT_ROOT /home/public_html

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# vinhjaxt
RUN sed -i -E 's/Listen\s+80([^0-9]|$)/Listen 8001\1/g' /etc/apache2/ports.conf /etc/apache2/sites-available/*.conf /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf /etc/apache2/sites-enabled/*.conf

RUN sed -i -E 's/(VirtualHost\s+.+)\:80([^0-9]|$)/\1:8001\2/g' /etc/apache2/ports.conf /etc/apache2/sites-available/*.conf /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf /etc/apache2/sites-enabled/*.conf

