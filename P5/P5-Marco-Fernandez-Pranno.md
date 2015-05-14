## Práctica 5 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**Creación de la tabla en la base de datos - Servidor Maestro:**

La creación de la tabla se realiza primeramente en el servidor que va a actuar como maestro, con las siguientes órdenes:

`mysql -u root -p`
`create database contactos;`
`create table datos(nombre varchar(100),tlf int);`

Insertamos una entrada con: 

`insert into datos(nombre,tlf) values ("K.Mitnick",13371337);`












[creacion-tabla]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/creacion-tabla.png?raw=true
[manual-slave]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/manual-slave.png?raw=true
[manual-master]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/manual-master.png?raw=true
[automatico-master-slave]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/automatico-master-slave.png?raw=true
[automatico-prueba]: https://github.com/MarFerPra/SWAP15/blob/master/P5/imagenes/automatico-prueba.png?raw=true
