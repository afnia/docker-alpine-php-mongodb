# Docker - Alpine php-mongodb

Container Image:
```
afnia/docker-alpine-php-mongodb
```


Dockerfile

```
FROM alpine:3.9

# Install packages
RUN apk --update --no-cache add php7 php7-fpm php7-json php7-openssl php7-curl \
    php7-xml php7-phar php7-intl php7-xmlreader php7-ctype php7-bcmath \
    php7-mbstring php7-gd php7-pear php7-dev \
    autoconf g++ gcc make pkgconf openssl-dev

RUN pecl install mongodb \
    pecl clear-cache

COPY ./config/php.ini /etc/php7/php.ini

```

php.ini

```
extension=mongodb.so

memory_limit = 512M
post_max_size = 200M
max_file_uploads = 2000

[Date]
date.timezone="UTC"
```