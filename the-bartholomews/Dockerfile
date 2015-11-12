FROM ubuntu:trusty

RUN apt-get update && \
  apt-get install -y \
  curl \
  php5 \
  php5-curl \
  php5-gd \
  php5-imagick \
  php5-mcrypt \
  php5-memcached \
  php5-mysql \
  php5-redis


RUN rm /var/www/html/index.html
RUN a2enmod rewrite
RUN php5enmod mcrypt
COPY ./config/php/* /etc/php5/apache2/conf.d/
COPY ./config/apache2/* /etc/apache2/conf-enabled/

# Install node and some dependencies, for running Grunt to build the assets
RUN curl -o /tmp/node.tar.gz https://nodejs.org/download/release/v0.12.7/node-v0.12.7-linux-x64.tar.gz
RUN tar -xvzf /tmp/node.tar.gz -C /opt
ENV PATH=$PATH:/opt/node-v0.12.7-linux-x64/bin
RUN npm install -g grunt-cli bower

COPY src /var/www/
RUN cd /var/www && npm start
RUN chown -R www-data:www-data /var/www

EXPOSE 80
CMD apache2ctl -D FOREGROUND
