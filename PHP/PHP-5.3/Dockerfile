FROM ubuntu:12.04

RUN echo "deb http://ppa.launchpad.net/sjinks/x3m/ubuntu precise main" >> /etc/apt/sources.list 
RUN echo "deb-src http://ppa.launchpad.net/sjinks/x3m/ubuntu precise main" >> /etc/apt/sources.list 

RUN gpg --keyserver keys.gnupg.net --recv-key 67C617E5 
RUN gpg -a --export 67C617E5 | apt-key add -

RUN apt-get update

# wordpress php deps
RUN apt-get -y install php5 php5-cli php5-fpm php5-mysql php5-curl php5-gd php5-intl 

RUN sed -e 's/.*daemonize.*/daemonize = no/' -i /etc/php5/fpm/php-fpm.conf
RUN sed -e 's/.*cgi.fix_pathinfo.*/cgi.fix_pathinfo=0/' 
RUN sed 's/.*listen =.*/listen = 0.0.0.0:9000/' -i /etc/php5/fpm/pool.d/www.conf
RUN sed -e 's/.*listen =.*/listen = 0.0.0.0:9000/' -e 's/.*catch_workers_output.*/catch_workers_output = yes/' -i /etc/php5/fpm/pool.d/www.conf 

RUN echo "php_admin_value[error_log] = stdout\nphp_admin_flag[log_errors] = on" >> /etc/php5/fpm/pool.d/www.conf

EXPOSE 9000

CMD ["/usr/sbin/php5-fpm"]
