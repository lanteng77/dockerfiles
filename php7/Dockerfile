FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos
MAINTAINER zrd <295201600@qq.com>

#RUN yum install -y libicu-devel pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf

#ADD http://download.icu-project.org/files/icu4c/62.1/icu4c-62_1-src.tgz .
#RUN tar xf icu4c-62_1-src.tgz && cd icu/source && ./configure --prefix=/usr/local/icu && make && make install

ADD http://ca1.php.net/distributions/php-7.4.29.tar.gz .
RUN yum install -y libicu-devel pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf
&& tar zxvf php-7.4.29.tar.gz \
&& mkdir -p /usr/local/ \
&& cd php-7.4.29 \
&& ./configure --prefix=/usr/local/php7 --enable-fpm --with-curl --with-openssl --with-gd --enable-intl --enable-mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd \
&& make && make install \
&& cp php.ini-production /usr/local/php7/lib/php.ini \
&& cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf \
&& cp /usr/local/php7/etc/php-fpm.d/www.conf.default /usr/local/php7/etc/php-fpm.d/www.conf \
&& sed -i 's/;pid = run\/php-fpm.pid/pid = run\/php-fpm.pid/' /usr/local/php7/etc/php-fpm.conf \
&& sed -i 's/;error_log = log\/php-fpm.log/error_log = log\/php-fpm.log/' /usr/local/php7/etc/php-fpm.conf \
&& /usr/local/php7/bin/pecl install redis \
&& /usr/local/php7/bin/pecl install swoole \
&& sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini
