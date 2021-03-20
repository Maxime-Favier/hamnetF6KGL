FROM php:7.3-apache

# install all dependency
RUN apt-get update && apt-get install --no-install-recommends -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
	rrdtool \
	cron 

# install php gd module
RUN docker-php-ext-configure gd --with-freetype-dir=/usr --with-jpeg-dir=/usr --with-png-dir=/usr \
 && docker-php-ext-install -j$(nproc) gd

COPY src/ /var/www/html/

# RUN php /var/www/html/check.php

# production build
COPY hide_errors.ini /usr/local/etc/php/conf.d/
COPY 000-default.conf /etc/apache2/sites-enabled/

# set permission for editor.php
RUN chown -R www-data /var/www/html/configs/ \
	&& chmod -R u+w /var/www/html/configs

# Copy networkWeathermap-cron file to the cron.d directory
COPY networkWeathermap-cron /etc/cron.d/networkWeathermap-cron
 

RUN touch /var/log/cron.log && \
	chmod 0644 /etc/cron.d/networkWeathermap-cron && \
	crontab /etc/cron.d/networkWeathermap-cron

CMD cron && service apache2 start && tail -f /var/log/cron.log
