FROM php:7.2-apache

COPY . /var/www/html

RUN docker-php-ext-install pdo pdo_mysql
RUN a2enmod rewrite
RUN rm -rf /var/www/html/var/cache/prod \
    && rm -rf /var/www/html/var/cache/dev
RUN chown -R www-data /var/www
RUN chmod -R 777 /var/www

COPY ./php-conf/php.ini /usr/local/etc/php/php.ini
COPY ./apache/000-default.conf /etc/apache2/sites-enabled/

RUN service apache2 restart

EXPOSE 80