FROM alpine
RUN apk update \
    && apk add apache2 
COPY mypage.html /var/www/localhost/htdocs
COPY docker-entrypoint.sh /bin 
RUN chmod +x /bin/docker-entrypoint.sh
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["httpd", "-D", "FOREGROUND"]
ENV APACHE_PORT 80
