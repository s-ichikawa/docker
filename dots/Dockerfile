FROM centos:6.8

RUN yum update -y && \
    yum clean all

##############
# Repository #
##############
# remi, epel repo
RUN rpm --import http://rpms.famillecollet.com/RPM-GPG-KEY-remi
RUN rpm --import http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-6
RUN yum install -y http://rpms.famillecollet.com/enterprise/remi-release-6.rpm \
    epel-release && \
    yum clean all

##############
# Middleware #
##############
# nginx
RUN yum install -y nginx

# mariadb
RUN rpm --import https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
COPY ./etc/yum.repo.d/mariadb.repo /etc/yum.repos.d/mariadb.repo
RUN yum install -y --enablerepo=mariadb MariaDB-devel MariaDB-client MariaDB-server

# redis
RUN yum install -y redis

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
        php-redis \
        php-fpm

# composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

##############
# CMD        #
##############
CMD service nginx start
CMD service php-fpm start
CMD service mysql start
CMD service redis start
