FROM ghcr.io/ftpcory/docker-php-cli:7.4.x-dev
MAINTAINER corycollier@corycollier.com

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp

COPY config/custom.php.ini /usr/local/etc/php/conf.d/custom.php.ini
COPY config/cron-wordpress /app/cron-wordpress
COPY dotfiles/.* /root/
COPY scripts/* /usr/local/bin

USER www-data
RUN crontab /app/cron-wordpress

WORKDIR /app

USER root
CMD cron -f
