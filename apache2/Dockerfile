# minimal base image
FROM httpd:alpine

LABEL maintainer="beigetamarah@gmail.com"
LABEL description="Apache2 server."

ADD ./html/apache/ /var/www/apache
ADD ./html/blue/ /var/www/blue
ADD ./html/red/ /var/www/red
ADD ./sites-enabled/ /usr/local/apache2/sites-enabled

RUN apk add php php-apache2

RUN mkdir /var/www-data
RUN mkdir /var/www-data/log

RUN chown -R www-data:www-data /var/www-data
RUN chown -R www-data:www-data /var/www
RUN chmod 750 -R /var/www-data


COPY ./ports.conf /usr/local/apache2/conf/ports.conf
COPY ./apache2.conf /usr/local/apache2/conf/httpd.conf

# Open HTTP and HTTPS ports
EXPOSE 8080
EXPOSE 8081
EXPOSE 8082

# Switch to a non-root user
USER www-data

CMD ["httpd", "-D", "FOREGROUND"]
