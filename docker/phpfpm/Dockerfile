FROM bitnami/php-fpm

RUN apt-get update && \
    apt-get install -y git autoconf gcc make vim
RUN git clone https://github.com/phpredis/phpredis.git && \
    cd phpredis && \
    git checkout php7 && \
    phpize && \
    ./configure && \
    make && make install && \
    cd .. && \
    rm -rf phpredis
    
RUN echo 'extension=/opt/bitnami/php/lib/php/extensions/no-debug-non-zts-20151012/redis.so' >> /opt/bitnami/php/lib/php.ini
RUN echo 'extension=/opt/bitnami/php/lib/php/extensions/no-debug-non-zts-20151012/redis.so' >> /bitnami/php-fpm/conf/php.ini
RUN echo 'opcache.enable=0' >> /bitnami/php-fpm/conf/php.ini