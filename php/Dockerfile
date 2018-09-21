FROM php:7-fpm

RUN apt-get update && apt-get install -y \
curl \
wget \
git \
libfreetype6-dev \
libjpeg62-turbo-dev \
libxslt-dev \
libicu-dev \
libmcrypt-dev \
libxml2-dev \
libmcrypt-dev

RUN docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install xsl
RUN docker-php-ext-install soap

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD ./php.ini /usr/local/etc/php/conf.d/40-custom.ini

CMD ["php-fpm"]
