#Práctica 6. 

## Discos en RAID.

- Introducción. 

Sabemos de RAID que es una forma de distribuir datos en varios discos y que puede ser gestionado por hardware dedicado o software, además de que existen diversos tipos de RAID. 

En esta práctica el primer paso para poder trabajar y poder observar como funciona esta tecnología se configruan dos discos RAID 1, de forma que en total tendremos 3 discos. 

Pongo aquí la captura que demuestra que al arrancar el sistema podemos ver los tres discos: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/Captura.JPG)

- Configuración del RAID por software. 

Arrancamos la máquina e instalamos el software necesario para el raid usando el comando *sudo apt-get install mdadm*. 
 
Buscamos la información que nos va a ser necesaria con el comando *sudo fdisk -l*. 

Ahora ya es momento de crear el RAID 1 usando el dispositivo /dev/md0 e indicando el número de dispositivos y su ubicación. De esta manera, el comando queda de la siguiente manera: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/creado_dm0.JPG)

Usamos *sudo mkfs /dev/md0* para darle formato al mismo. 

Creamos el directorio en el que se montará la unidad RAID: 

**sudo mkdir /dat**
**sudo mount /dev/md0 /dat**

Ahora, para configurar el sistema para que monte el dispositivo RAID al arrancar el sistema añadimos a */etc/fstab* la linea siguiente (habiendo obtenido el valor de nuestro RAID con *ls -l /dev/disk/by-uuid/*): 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/linea_a%C3%B1adida.JPG)

- Simulación de fallos, retiradas y añadidos en caliente. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/estado_md0.JPG)

Una vez que esté funcionando el dispositivo RAID podemos simular un fallo de la siguiente forma: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/simula_fallo.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/comprobacion_fallo.JPG)

De la misma forma que podemos retirar el disco en caliente y solucionar cualquier tipo de problema que pudiera surgir. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/retira_disco.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/comprobacion_retirado.JPG)

Por último, una vez hemos retirado el disco podemos introducir un nuevo disco que reemplace al disco dañado y retirado.

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/poneDisco.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica6/Capturas/comprobacion_a%C3%B1adido.JPG)
