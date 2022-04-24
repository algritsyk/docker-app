FROM php:8.1-fpm

# APT Packages
RUN apt-get update \
    && apt-get install -y \
    zip git

# CacheTool for OPCACHE
RUN apt-get clean all
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.3.5
RUN curl -o /usr/local/bin/cachetool http://gordalina.github.io/cachetool/downloads/cachetool.phar

EXPOSE 9000
