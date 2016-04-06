FROM centos:6
MAINTAINER shingo.ichikawa.0829

RUN yum install -y httpd httpd-devel
RUN yum install -y http://dl.fedoraproject.org/pub/epel/6/x86_64/imlib2-1.4.2-5.el6.x86_64.rpm\
	http://dl.fedoraproject.org/pub/epel/6/x86_64/imlib2-devel-1.4.2-5.el6.x86_64.rpm
RUN yum install -y wget tar gcc ImageMagick-devel ImageMagick

RUN cd /usr/local/src/ && \
    wget http://smalllight.googlecode.com/files/mod_small_light-1.1.1.tar.gz && \
    tar xzf mod_small_light-1.1.1.tar.gz && \
    cd mod_small_light-1.1.1 && \
    ./configure --with-apxs=/usr/sbin/apxs --with-imlib2-config=/usr/bin/imlib2-config --with-Wand-config=/usr/bin/MagickWand-config && \
    sed -E "s/\\$\(WAND_INCLUDES\)/-I\/usr\/include\/ImageMagick/" Makefile > Makefile.new && \
    mv -f Makefile.new Makefile && \
    make && make install

RUN mkdir /var/www/html/images
RUN cd /var/www/html/images/ && wget https://baitalk.jp/img/company/1/php29Hefo.jpg

COPY small_light.conf /etc/httpd/conf.d/
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
EXPOSE 80
