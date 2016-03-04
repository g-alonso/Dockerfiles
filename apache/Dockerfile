FROM       galonso/ubuntu:14.04
MAINTAINER Gabriel Alonso <gbr.alonso@gmail.com>

RUN sudo apt-get update -qq -y
RUN sudo apt-get install -qq -y \
    libapr1-dev                 \
    libaprutil1-dev

ENV HTTPD_MIRROR http://mirrors.dcarsat.com.ar
ENV HTTPD_VERSION 2.4.18

RUN cd /tmp;                                                   \
    curl -LO $HTTPD_MIRROR/apache/httpd/httpd-$HTTPD_VERSION.tar.bz2; \
    tar xvjf *.tar.bz2; rm -f *.tar.bz2;                       \
    cd httpd-*;                                                \
    ./configure                                                \
      --prefix=/usr/local                                      \
      --with-config-file-path=/www                             \
      --enable-so                                              \
      --enable-cgi                                             \
      --enable-info                                            \
      --enable-rewrite                                         \
      --enable-deflate                                         \
      --enable-ssl                                             \
      --with-mpm=prefork                                       \
      --enable-mime-magic                                      \
      ;                                                        \
    make && make install;                                      \
    cd; rm -rf /tmp/httpd-*

ADD www /www

EXPOSE 8080
CMD    [ "apachectl", \
         "-d", "/usr/local", \
         "-f", "/www/httpd.conf", \
         "-DFOREGROUND" ]