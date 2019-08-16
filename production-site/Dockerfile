FROM richarvey/nginx-php-fpm
RUN set -ex
RUN docker-php-ext-install pdo pdo_mysql
COPY composer.json ./
COPY composer.lock ./
RUN composer install --no-scripts --no-autoloader

COPY . ./

COPY nginx.conf /etc/nginx/sites-enabled/default.conf
RUN composer dump-autoload --optimize

RUN chown www-data -R storage/ bootstrap/ vendor/

CMD ["/start.sh"]