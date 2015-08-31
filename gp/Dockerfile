# from https://www.drupal.org/requirements/php#drupalversions
FROM php:5.6-apache

RUN a2enmod rewrite

# install the PHP extensions we need
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libpq-dev git \
	&& rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql

WORKDIR /var/www

# Beginning here doesn't work
RUN git clone https://github.com/ckwright/geek-portland.git geekportland
RUN cd geekportland
RUN bin/install
RUN ln -s geekportland/drupal html
