# itop-docker
php7.2-apache2镜像的itop2.6安装环境。

dockerfile脚本如下：

FROM php:7.2-apache
RUN apt-get update && apt-get install -y \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpng-dev \
	libmcrypt-dev \
	libxml2-dev \
	libldap2-dev \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install soap \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install ldap \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd \
	&& rm -rf /var/lib/apt/lists/*
