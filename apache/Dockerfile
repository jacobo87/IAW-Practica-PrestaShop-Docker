FROM ubuntu:local

LABEL author="Jacobo Azmani"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update \
    && apt install apache2 -y\
    && apt install php -y\
    && apt install libapache2-mod-php -y \
    && apt install php-mysql -y

RUN apt install git -y \
    && cd /tmp \
    && git clone https://github.com/jacobo87/IAW-Practica-PrestaShop-Docker \
    %% mv /tmp/IAW-Practica-PrestaShop-Docker/* /var/www/html \
    && sed -i 's/localhost/mysql/' /var/www/html/config.php \
    && rm /var/www/html/index.html

EXPOSE 80

CMD ["usr/sbin/apache2ctl", "-D", "FOREGROUND"]
