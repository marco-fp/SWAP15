## Práctica 2 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**1. Prueba de funcionamiento de la copia de archivos por ssh:**

El envío de un fichero por ssh se realiza mediante la compresión del mismo primero y después con un cauce hacia la ejecución del ssh con un cat como argumento. La orden a introducir en el terminal sería: 

` tar czf - directorio_envio_comprimido | ssh root@192.168.24.129 'cat > ~/tar.tgz' `

Posteriormente introducimos la contraseña del usuario seleccionado para el login, en este caso el root. Y podemos ver como se ha enviado correctamente mediante el listado de elementos en el fichero del otro servidor.

![alt text][envio-por-ssh]

**2. Clonado de una carpeta entre las dos máquinas**

Para el clonado de un fichero entre dos máquinas he utilizado la orden rsync, sincronizando el directorio home de el servidor 1 en el directorio home del el servidor 2. Para hacerlo, he utilizado la siguiente orden lanzada desde el servidor 2:

` rsync -avc -c ssh user01@192.168.24.128:/home/user01/ /home/user02/ `

![alt text][envio-fichero]

**3. Configuración de ssh para acceder sin que solicite contraseña.**

Debido a que me ha sido imposible configurar la conexión sin contraseña por ssh con usuario root, he realizado el ejercicio mediante un usuario normal. Por otro lado, los pasos a seguir en ambos casos han sido los mismos:

  * Generación de claves en ambas máquinas mediante la orden ` ssh-keygen -t dsa ` tal y como se muestra en las siguientes capturas:
  
  Como usuario:
  ![alt text][generacion-claves] 
  Como root:
  ![alt text][generacion-claves-root]

  
  * Posteriormente he llevado a cabo el envío de las claves públicas de una máquina a otra con la orden 
    ` ssh-copy-id -i nombre-de-la-clave.pub nombre-usuario@ip-de-la-maquina-receptora `. Tal y como se refleja en las      capturas:
    
    Como usuario:
    ![alt text][envio-claves]

    Como root:
    ![alt text][envio-claves-root]

**4. Establecer una tarea en cron que se ejecute cada hora para mantener actualizado el contenido del directorio /var/www entre las dos máquinas.**



[envio-claves]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/envio-claves.png?raw=true
[envio-claves-root]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/envio-claves-root.png?raw=true
[envio-por-ssh]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/envio-por-ssh.png?raw=true
[envio-fichero]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/envio_fichero.png?raw=true
[generacion-claves]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/generacion-claves.png?raw=true
[generacion-claves-root]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/generacion-claves-root.png?raw=true
[permitir-acceso-root]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/permitir-acceso-root.png?raw=true
[update-www]: https://github.com/MarFerPra/SWAP15/blob/master/P2/imagenes/update-www-de-02.png?raw=true
