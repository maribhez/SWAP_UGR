#Práctica 5. 

##Replicación de bases de datos MySQL. 

A la hora de hacer copias de seguridad de nuestras bases de datos (BD) MySQL, una opción suele ser la réplica maestro-esclavo, de manera que nuestro servidor en producción hace de maestro y otro servidor de backup hace de esclavo. 

Tener una réplica añade fiabilidad ante fallos del sistema en producción. 

- Crear una BD e insertar datos. 

Para el resto de la prácitca hemos de crear una base de datos e introducir algunos datos, para así tener alguna información con la que poder hacer las copias de seguridad. 

Muestro las capturas de los comandos introducidos en la máquina principal: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/crearBD_1.JPG)


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/crearBD_2.JPG)


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/crearBD_3.JPG)

- Replicar una BD MySQL con  *mysqldump*. 

MySQL ofrece la herramienta **mysqldump** para clonar las BD que tengamos ya creadas en nuestra máquina. Puede usarse para volver una o varias BD para copia de seguridad o para transferir datos a otro servidor SQL. 

De esta forma, después de haber ejecutado el comando *flush tables with read lock;* podemos introducir el comando correspondiente a esta herramienta que estamos explicando (todo ello en la máquina principal).

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/mysqldump_.JPG)

Al haber bloqueado anteriormente las tablas ahora necesitamos desbloquearlas, para ello usamos *UNLOCK TABLES;*.


Es ahora cuando podemos ir a la máquina 2 y copiar el archivo que acabamos de crear: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/copiaBD.JPG)

Importamos la copia de seguridad en el esclavo (máquina secundaria), aunque para ello primero  
debemos crear la base de datos con el mismo comando usado al principio de la práctica (*create database 'nombre_baseD*). 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/copiaBD-2.JPG)

Tal y como se especifica en el guión podíamos haber realizado estos pasos en un solo comando: 

**mysqldump ejemplodb -u root -p | ssh equipodestino mysql**


- Replicación de BD mediante una configuración maestro-esclavo. 


Esto es una opción que automatiza y agiliza la copia realizada con el comando *mysqldump*, configurando el demonio para hacer replicación de las BD sobre un esclavo a partir de los datos que almacena el maestro. 

Hay que realizar configuaciones tanto en la máquina esclavo como en la máquina maestro. 

Por lo tanto, y sabiendo de antemano que tenemos las bases de datos clonadas vamos a configurar el mysql del maestro. En concreto, el archivo */etc/mysql/my.cnf*. 

Modificamos los siguiente parametros: 

1. Comentamos el parámestor bind-address que sirve para que escuche a un servidor. 

**#bind-address 127.0.0.1**

2. Establecemos el archivo donde se almacenarán los errores que vayan surgiendo: 

**log_error = /var/log/mysql/error.log**

3. Establecemos el idenficiador del servidor. **server-id = 1**

4. Establecemos el archivo del registro binario que contendrá toda la información que estará disponible en el registro de actualizaciones: **log_bin = /var/log/mysql/bin.log**

Ahora, reinicimos el sistema y si no hemos tenido ningún problema realizamos la misma modificación en la máquina esclavo, sabiendo que posteriormente vamos a tener que añadir información adicional (ya que por la versión de *mysql* no se permite añadirla al archivo de configuración).

Reiniciamos el servidor, y ya podremos crear un usuario en la máquina maestro y darle permisos de acceso para proceder a la replicación. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/configuracion_maestro.JPG)

 
Y es ahora cuando debemos volver a la máquina esclavo y darle la configuración que nos devuelva el comando **SHOW MASTER STATUS;** de la máquina principal. Así, añadimos la configuración y lanzamos el esclavo. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/configuracion_esclavo.JPG)

Una vez lanzado el esclavo comprobamos que el esclavo es correcto (con **SHOW SLAVE STATUS\G;), sabiendo que la variable "Seconds_Behind_Master" debe ser distinta de null. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/correcto_esclavo.JPG) 

Comprobamos el funcionamiento de la configuración añadiendo un dato en la máquina maestra y comprobando mediante los comandos oportunos que aparecen al momento en la esclavo. 


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/comprobacion_maestro_esclavo.JPG)



- Replicación de BD mediante una configuración maestro-maestro. 

Como tarea adicional se planteaba la configuración maestro-maestro. 

Para esto tan solo es necesario realizar los pasos que tuvimos que hacer para configurar la máquina esclavo (crear usuario y darle permisos, conocer los datos de la base de datos de la que vamos a copiar información y añadir la linea de comandos con toda la configuración creada y obtenida). 

La demostración aparece en las siguientes imágenes, creando datos en ambas máquinas y comprobando que se copian en ambos sentidos. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/pruebaMaestroMaestro_conCreaciondesdeMaquinaPrincipal.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica5/Capturas/pruebaMaestroMaestro_conCreaciondesdeMaquinaClonada.JPG)




