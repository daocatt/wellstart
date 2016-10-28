#PHP-fpm设置开机启动


#启动脚本
file:/etc/rc.d/init.d/php-fpm

```
#! /bin/sh
#chkconfig: 2345 60 90
## vi /opt/php/etc/php-fpm.conf  #uncomment pid under [global]  #pid = run/php-fpm.pid
## vi /etc/rc.d/init.d/fpm
## chmod +x /etc/rc.d/init.d/fpm
## chkconfig --add fpm
## chkconfig fpm on
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="php-fpm daemon"
NAME=php-fpm
INSTALLDIR=/opt/php
DAEMON=$INSTALLDIR/sbin/$NAME
CONFIGFILE=$INSTALLDIR/lib/$NAME.conf
PIDFILE=$INSTALLDIR/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
set -e
[ -x "$DAEMON" ] || exit 0
do_start() {
    $DAEMON -D || echo -n "php-fpm already running"
}
do_stop() {
    kill -INT `cat $PIDFILE` || echo -n "php-fpm not running"
}
do_test() {
    $DAEMON -t || echo -n "php-fpm can't test"
}
case "$1" in
    start)
        echo -n "Starting $DESC: $NAME"
        do_start
        echo "."
    ;;
    stop)
        echo -n "Stopping $DESC: $NAME"
        do_stop
        echo "."
    ;;
    restart)
        echo -n "Restarting $DESC: $NAME"
        do_stop
        do_start
        echo "."
    ;;
    test)
        echo -n "Testing $DESC: $NAME"
        do_test
        echo "."
    ;;
    *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|test}" >&2
    exit 3
    ;;
esac
exit 0
```


#设置开机启动
vi /etc/rc.d/init.d/php-fpm
chmod +x /etc/rc.d/init.d/php-fpm
chkconfig --add php-fpm
chkconfig php-fpm on


