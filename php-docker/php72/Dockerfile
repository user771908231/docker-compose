FROM php:7.2-cli
# redis
# xdebug
RUN pecl install redis-4.0.1 \
    && pecl install xdebug-2.6.0 \
    && docker-php-ext-enable redis xdebug
# 增加 gd 扩展
RUN apt-get update && \
    apt-get install -y --no-install-recommends libfreetype6-dev libjpeg62-turbo-dev libpng-dev && \
    rm -r /var/lib/apt/lists/* && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd
# 1.0.21 增加 Memcached 扩展
RUN apt-get update && \
    apt-get install -y --no-install-recommends zlib1g-dev libmemcached-dev && \
    rm -r /var/lib/apt/lists/* && \
    pecl install memcached && \
    docker-php-ext-enable memcached

EXPOSE 9000