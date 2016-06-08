#Práctica 2. 

##Clonar la información de un sitio web. 

1. Instalar la herramienta rsync. 

Para sincronizar grandes cantidades de información entre varias máquinas contamos con la herramiena *rsync*, sabiendo de antemano que para instalarla basta con usar el comando **sudo apt-get install rsync**. 

Antes de seguir, hemos de saber que es conveniente activar la cuenta de root para trabajar con todos los permisos y que para ello ejecutaremos **sudo passwd root**, proporcionándole la clave correspondiente y así podremos trabajar de la forma más adecuada (aunque éste es un paso que parece olvidé a la hora de realizar las pruebas). 

De todas formas, probamos el funcionamiento de la herramienta en cuestión con el siguiente comando que se muestra en la imagen. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/rsync_de2a1.JPG)

Se nos pedirá la clave root en la máquina principal y después de unos segundos comprobaremos que el directorio escogido para clonar aparece en ambas máquinas, manteniendo los permisos y dueños de la máquina origen. 

![Prueba ls -la /var/www de la primera máquina.](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ls_la1.JPG)

![Prueba ls -la /var/www de la segunda máquina.](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ls_la2.JPG)
