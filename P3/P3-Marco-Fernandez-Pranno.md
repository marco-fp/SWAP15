## Práctica 3 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**1. Instalación de Nginx y Haproxy:**

En ambos casos he realizado la instalación tal y como se indica en el guión de la práctica.
Haproxy directamente escribiendo en un terminal:

`sudo apt-get install haproxy`

Y por otro lado, Nginx primero descargando la clave pública y posteriormente añadiendo los repositorios al archivo sources.list de apt:

Descarga de la clave:

`wget http://nginx.org/keys/nginx_signing.key
 apt-key add /tmp/nginx_signing.key`

Añadiendo repositorio:

`echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
 echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list`

Por último:

`apt-get update
apt-get install nginx`

**2. Configuración de los balanceadores de carga:**

Para empezar, cambiado el index.html de ambos servidores apaches podemos identificar desde que máquina se está
respondiendo a la petición de `curl` desde el host.

![alt text][index-html]

He instalado en la misma máquina tanto haproxy como nginx, deteniendo el servicio de nginx (y el apache anteriormente instalado) para ejecutar haproxy.

* Nginx como balanceador - Round Robin.

  En este caso la configuración es una copia de lo propuesto en el guión de prácticas, el método de balanceo es round robin entre los servidores.

![alt text][nginx-round]

* Nginx - Con peso 3 - 1 entre servidores.

![alt text][nginx-weight]

  En este caso, con la sentencia weight el balanceador cada 4 peticiones le envía 3 al servidor primario y 1 al secundario.
  El resultado del envío de peticiones al balanceador es el siguiente:

![alt text][cultnginx-weight]

* Haproxy - Round Robin.

![alt text][haproxy-roundrobin]

* Haproxy - Con peso 2 - 1 entre servidores.

![alt text][haproxy-weight]
