FROM centos:7
RUN yum update -y

# install leatest apache2.4.*
# RUN yum -y install wget epel-release
# RUN yum install -y vim;
# RUN yum remove -y php-*
# RUN yum install -y --enablerepo=epel,remi,remi-safe,remi-php72 php php-mbstring php-mysql php-pdo
# RUN yum install -y php

RUN yum -y install wget epel-release vim

RUN wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN rpm -Uvh ./remi-release-7.rpm
RUN sed -i '4a priority=1' /etc/yum.repos.d/remi-php74.repo
RUN yum -y install --enablerepo=remi-php74 php php-fpm php-mcrypt php-cli php-common php-devel php-gd php-mbstring php-mysqlnd php-opcache php-pdo php-pear php-pecl-apcu php-pecl-zip php-process php-xml
RUN yum clean all

RUN yum install -y httpd;

COPY docker.conf /etc/httpd/conf.d/docker.conf

# dockre can not use systemd without permission, apahce is started with httpd
CMD ["/usr/sbin/httpd", "-DFOREGROUND"]