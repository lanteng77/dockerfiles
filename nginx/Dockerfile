FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos:latest
MAINTAINER zrd 295201600@qq.com

RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel
ADD http://nginx.org/download/nginx-1.21.6.tar.gz .
RUN tar zxvf nginx-1.21.6.tar.gz && mkdir -p /usr/local/nginx && cd nginx-1.21.6 && ./configure --prefix=/usr/local/nginx && make && make install && rm -fv /usr/local/nginx/conf/nginx.conf && mkdir -p /usr/local/nginx/conf/server
COPY test.conf /usr/local/nginx/conf/server/test.conf
COPY nginx.conf /usr/local/nginx/conf/nginx.conf
