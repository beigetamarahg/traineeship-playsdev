# minimal base image
FROM nginx:alpine

LABEL maintainer="beigetamarah@gmail.com"
LABEL description="Nginx server with reverse proxy."

# Install image filter module
RUN apk add --no-cache nginx-mod-http-image-filter

ADD ./letsencrypt/ /etc/letsencrypt
ADD ./html/ /var/www/html
ADD ./sites-enabled/ /etc/nginx/sites-enabled

RUN chown -R nginx:nginx /var/cache/nginx
RUN chown -R nginx:nginx /etc/letsencrypt

RUN mkdir /var/run/nginx
RUN chown -R nginx:nginx /var/run/nginx

# Open HTTP and HTTPS ports
EXPOSE 80 443

# Switch to a non-root user
USER nginx

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
