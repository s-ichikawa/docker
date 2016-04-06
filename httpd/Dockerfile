FROM ubuntu:latest
MAINTAINER shingo.ichikawa.0829

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y apache2
RUN apt-get install -y curl git autoconf
RUN apt-get install -y aptitude autotools-dev libltdl-dev autoconf autopoint
RUN aptitude install -y libtool

RUN git clone https://github.com/icing/mod_h2
RUN cd ./mod_h2
RUN autoreconf -i
RUN automake
RUN autoconf
RUN ./configure --enable-sandbox
RUN make
RUN cp ./mod_h2/.libs/mod_h2* ./gen/install/modules/

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2

ADD ./htdocs /var/www

EXPOSE 80

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
