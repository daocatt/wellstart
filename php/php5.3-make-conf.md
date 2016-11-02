#linux PHP编译安装


./configure \
--prefix=/usr/local/php53 \
--with-config-file-path=/usr/local/php53/etc \
--with-bz2 \
--with-curl \
--enable-ftp \
--enable-sockets \
--disable-ipv6 \
--with-gd \
--with-jpeg-dir=/usr/local \
--with-png-dir=/usr/local \
--with-freetype-dir=/usr/local \
--enable-gd-native-ttf \
--with-iconv-dir=/usr/local/libiconv \
--enable-mbstring \
--enable-calendar \
--with-gettext \
--with-libxml-dir=/usr/local \
--with-zlib \
--with-pdo-mysql=mysqlnd \
--with-mysqli=mysqlnd \
--with-mysql=mysqlnd \
--enable-dom \
--enable-xml \
--with-libdir=lib64 \
--enable-pdo \
--enable-fpm \
--disable-fileinfo \
--disable-debug