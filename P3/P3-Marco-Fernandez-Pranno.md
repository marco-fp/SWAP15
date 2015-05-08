## Práctica 3 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**1. Instalación de Nginx y Haproxy:**
En ambos casos he realizado la instalación tal y como se indica en el guión de la práctica.
Haproxy directamente escribiendo en un terminal:

`sudo apt-get install haproxy`

Y por otro lado, Nginx primero descargando la clave pública y posteriormente añadiendo los repositorios al archivo sources.list de apt:

Descarga de la clase:

`wget http://nginx.org/keys/nginx_signing.key
 apt-key add /tmp/nginx_signing.key`

Añadiendo repositorio:

`echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
 echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list`

Por último:

`apt-get update
apt-get install nginx`
