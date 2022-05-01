FROM php:8.1-fpm

# APT Packages
RUN apt-get update \
    && apt-get install -y \
    zip git

RUN apt-get install -y \
             libpq-dev

# PHP-Extenions
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pgsql pdo_pgsql

# CacheTool for OPCACHE
RUN apt-get clean all
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.3.5
RUN curl -o /usr/local/bin/cachetool http://gordalina.github.io/cachetool/downloads/cachetool.phar

# NodeJs
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

# Xdebug
RUN pecl install xdebug

COPY ./php-ini-overrides.ini /usr/local/etc/php/conf.d/php-ini-overrides.ini
COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

EXPOSE 9000
