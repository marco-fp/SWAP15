# Práctica 1: Servidores Web de Altas Prestaciones-

1. Instalación de Ubuntu Server + LAMP
    Durante la instalación cometí un error y no pude instalar LAMP junto con el SO,
    de manera que lo hice mediante la línea de comandos:

    `sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-mysql`

    Pese a estar reflejado en las capturas de pantalla, he generado el archivo p1.html
    en el directorio /var/www/html del servidor con las salidas de las órdenes
    `apache2 -v` y  `ps aux | grep apache`. El resultado es el siguiente:

    > Server version: Apache/2.4.10 (Ubuntu)
    > Server built:   Mar  5 2015 18:13:03
    > root       1484  0.0  2.1 278892 21816 ?        Ss   09:10   0:00 /usr/sbin/apache2 -k start \n
    > www-data   1488  0.0  0.7 278916  7528 ?        S    09:10   0:00 /usr/sbin/apache2 -k start
    > www-data   1489  0.0  0.7 278916  7528 ?        S    09:10   0:00 /usr/sbin/apache2 -k start
    > www-data   1490  0.0  0.7 278916  7528 ?        S    09:10   0:00 /usr/sbin/apache2 -k start
    > www-data   1491  0.0  0.7 278916  7528 ?        S    09:10   0:00 /usr/sbin/apache2 -k start
    > www-data   1492  0.0  0.7 278916  7528 ?        S    09:10   0:00 /usr/sbin/apache2 -k start
    > root       1776  0.0  0.2  11996  2172 tty1     S+   09:13   0:00 grep --color=auto apache
