FROM php:7.4-apache

RUN apt-get update && \
    apt-get install -y git zip unzip vim libpng-dev libpq-dev && \
    docker-php-ext-install pdo_mysql

RUN cd /usr/bin && \
    curl -s http://getcomposer.org/installer | php && \
    ln -s /usr/bin/composer.phar /usr/bin/composer

ADD ./php.ini /usr/local/etc/php/
ADD ./000-default.conf /etc/apache2/sites-enabled/

RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite

WORKDIR /var/www/html/app

ADD ./src /var/www/html/app
