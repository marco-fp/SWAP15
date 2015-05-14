## Práctica 5 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**Creación de la tabla en la base de datos - Servidor Maestro:**

La creación de la tabla se realiza primeramente en el servidor que va a actuar como maestro, con las siguientes órdenes:

`mysql -u root -p`
`create database contactos;`
`create table datos(nombre varchar(100),tlf int);`

Insertamos una entrada con: 

`insert into datos(nombre,tlf) values ("K.Mitnick",13371337);`

El resultado es el siguiente:

![alt text][creacion-tabla]

**Copia de seguridad manual entre máquinas de la base de datos:**

La copia de seguridad la realizamos con las siguientes órdenes (en la máquina Maestro), siguiendo los pasos indicados en el guión de prácticas:

`mysqldump contactos -u root -p > /root/contactos.sql`

Antes de la órden anterior, hay que salvar las tablas con un lock de lectura para que los datos no se alteren en el proceso de salvado. Y al finalizar la ejecución de mysqldump, desbloquearlas.
En mysql:

`mysql> FLUSH TABLES WITH READ LOCK;`
`mysql> UNLOCK TABLES;`

Ahora, desde la máquina esclavo, accedemos por ssh (usando scp) a la máquina maestro para copiar el archivo contactos.sql. Antes de ésto, es necesario crear la base de datos:

`mysql> create database contactos;`

Y por último:

`mysql -u root -p contactos < /root/contactos.sql`

Tal y como se refleja en las siguientes capturas:

(En el Maestro)

![alt text][manual-master]

(En el Esclavo)

![alt text][manual-slave]








[creacion-tabla]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/creacion-tabla.png?raw=true
[manual-slave]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/manual-slave.png?raw=true
[manual-master]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/manual-master.png?raw=true
[automatico-master-slave]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/automatico-master-slave.png?raw=true
[automatico-prueba]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/automatico-prueba.png?raw=true

