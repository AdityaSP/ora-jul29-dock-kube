FROM alpine
RUN apk update \
    && apk add apache2 
COPY mypage.html /var/www/localhost/htdocs
CMD ["httpd", "-D", "FOREGROUND"]
