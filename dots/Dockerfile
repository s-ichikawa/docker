FROM centos:6.7

RUN yum update -y && \
    yum clean all

##############
# Repository #
##############
# remi repo
RUN yum install -y http://rpms.famillecollet.com/enterprise/remi-release-6.rpm && \
    yum clean all

##############
# Middleware #
##############
# nginx
RUN yum install -y nginx

# mariadb

# redis

# php
RUN yum install -y --enablerepo=remi --enablerepo=remi-php56 \
        php \
        php-opcache \
        php-mbstring \
        php-devel \
        php-mcrypt \
        php-mysqlnd \
        php-phpunit-PHPUnit \
        php-pecl-xdebug \
        php-pecl-xhprof \
        php-fpm
CMD php -v

# composer

