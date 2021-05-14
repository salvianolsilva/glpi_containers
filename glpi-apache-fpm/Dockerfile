FROM php:8.0.6-apache-buster
LABEL mantainer="Salviano lima da Silva"
WORKDIR /var/www/html
RUN curl -Lo glpi.tgz https://github.com/glpi-project/glpi/releases/download/9.5.5/glpi-9.5.5.tgz&& \
tar -xvf glpi.tgz&& \
mv glpi/* ./ && \
rm -rf ./glpi.tgz && \
 rm -rf ./glpi && \
 chown www-data:www-data files/ -R &&\
 chown www-data:www-data marketplace/ -R&&\
 chown www-data:www-data config/ -R 
RUN apt-get update&&\
apt-get install -y libxml2-dev libbz2-dev libkf5ldap-dev libzip-dev libicu-dev bzip2&&\
apt-get install -y zlib1g zlib1g-dev &&\
apt-get install -y libfreetype6-dev libjpeg62-turbo.dev libpng-dev&&\
docker-php-source extract &&\
 docker-php-ext-install mysqli &&\
 docker-php-ext-install gd &&\
 docker-php-ext-install ldap && \
 docker-php-ext-install intl exif bz2 && \
 pecl install apcu-5.1.20 xmlrpc-1.0.0RC2&&\
 curl -LO https://github.com/apereo/phpCAS/releases/download/1.3.8/CAS-1.3.8.tgz &&\
 pear install  ./CAS-1.3.8.tgz &&\
 rm -rf ./CAS-1.3.8.tgz &&\
 docker-php-ext-enable apcu xmlrpc &&\
 echo "extension=apcu.so" > /usr/local/etc/php/php.ini &&\
 echo "apc.enable_cli=1" > /usr/local/etc/php/php.ini &&\
 echo "apc.enable=1" > /usr/local/etc/php/php.ini &&\
 docker-php-ext-install opcache zip &&\
 docker-php-source delete
 USER www-data
