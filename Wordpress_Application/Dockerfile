FROM wordpress:latest

WORKDIR /var/www/html


COPY . /var/www/html


EXPOSE 80


ENV WORDPRESS_DB_HOST db
ENV WORDPRESS_DB_USER wordpress
ENV WORDPRESS_DB_PASSWORD wordpress
ENV WORDPRESS_DB_NAME wordpress


CMD ["apache2-foreground"]
