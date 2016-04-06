FROM ubuntu:latest
MAINTAINER shingo.ichikawa.0829

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y nginx

ADD server.conf /etc/nginx/conf.d/server.conf
ADD ./htdocs /var/www

EXPOSE 80

CMD /usr/sbin/nginx -g "daemon off;"
