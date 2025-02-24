# Docker Image
FROM amazonlinux:2023

RUN yum update -y \
&& yum install -y httpd \
libedit ncurses-compat-libs \
freetype \
libjpeg-turbo \
t1lib \
libXpm \
harfbuzz \
libtiff \
fontconfig \
libtool-ltdl \
libxslt \
libicu \
vim \
less \
git \
zip \
unzip \
procps \
libxml2 \
php8.2.x86_64 \
php8.2-bcmath.x86_64 \
php8.2-cli.x86_64 \
php8.2-common.x86_64 \
php8.2-devel.x86_64 \
php8.2-gd.x86_64 \
php8.2-fpm.x86_64 \
php8.2-mbstring.x86_64 \
php8.2-pdo.x86_64 \
php8.2-xml.x86_64 \
php8.2-mysqlnd.x86_64 \
php8.2-intl.x86_64 \
php8.2-intl.x86_64 \
php-pear.noarch \
php8.2-zip.x86_64 

# zip install
RUN yum install -y php8.2-devel php-pear libzip libzip-devel \
    && pecl install zip

# postfix config
ADD main.cf /etc/postfix/main.cf
RUN chown -R root:root /etc/postfix/ \
&& chmod 644 /etc/postfix/main.cf

# apache config
ADD httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf
ADD httpd/conf.d/app.conf /etc/httpd/conf.d/app.conf

# Log directory
ENV APACHE_LOG_DIR /var/log/httpd
# Start httpd service with systemctl
RUN systemctl enable httpd.service

RUN yum clean all && rm -rf /var/cache/yum/*

EXPOSE 8000

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

#COPY entrypoint.sh /usr/bin
#RUN chmod +x /usr/bin/entrypoint.sh
#ENTRYPOINT ["/usr/bin/entrypoint.sh"]
#EXPOSE 3000