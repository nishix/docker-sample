FROM php:7.4.10-fpm-buster
COPY ./container/php/php.ini /usr/local/etc/php/php.ini
RUN apt-get update \
    && apt-get -y install git zip unzip vim libpq-dev 
RUN apt-get install -y zlib1g-dev \ 
    libzip-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev
RUN docker-php-ext-configure \
    gd --with-freetype=/usr/include --with-jpeg=/usr/include
RUN docker-php-ext-install pdo_pgsql pdo_mysql zip gd

#nodejs14インストール
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
RUN apt install -y nodejs

# composerインストール
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

WORKDIR /var/www/html
