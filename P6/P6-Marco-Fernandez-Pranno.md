## Práctica 6 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**Creación de discos y conexión a la máquina virtual:**

Para empezar, en la configuración de VMWare añado dos discos virtuales de 100MB cada uno. Una vez dentro, haciendo uso del comando `fdisk -l` podemos ver sus características y su estado.

![alt text][fdisk]

**Configuración y creación del RAID:**

Antes que nada, instalamos mdadm con la orden `apt-get install mdadm`. Después, habiendo comprobado en el paso anterior
el nombre de ambos discos, con la siguiente orden creamos el raid en el dispositivo /dev/md0.

`mdadm -C /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb /dev/sdc`

Para darle formato al dispositivo: `mkfs /dev/md0`

El siguiente paso es crear el directorio sobre el que se montará el dispositivo: `mkdir /datos-raid`

Y lo montamos con: `mount /dev/md0 /datos-raid/`

![alt text][creacion-raid]





[fdisk]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/fdisk.png?raw=true
[creacion-raid]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/creacion-raid.png?raw=true
[detalles-raid]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/detalles-raid.png?raw=true
[generacion-fallo]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/generacion-fallo.png?raw=true
[aniadir-disco]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/aniadir-disco.png?raw=true
[disco-aniadido]: https://github.com/MarFerPra/SWAP15/blob/master/P6/imagenes/disco-aniadido.png?raw=true