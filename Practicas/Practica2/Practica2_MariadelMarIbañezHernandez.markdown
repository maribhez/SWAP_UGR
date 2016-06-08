#Práctica 2. 

##Clonar la información de un sitio web. 

1. Instalar la herramienta rsync. 

Para sincronizar grandes cantidades de información entre varias máquinas contamos con la herramiena *rsync*, sabiendo de antemano que para instalarla basta con usar el comando **sudo apt-get install rsync**. 

Antes de seguir, hemos de saber que es conveniente activar la cuenta de root para trabajar con todos los permisos y que para ello ejecutaremos **sudo passwd root**, proporcionándole la clave correspondiente y así podremos trabajar de la forma más adecuada (aunque éste es un paso que parece olvidé a la hora de realizar las pruebas). 

De todas formas, probamos el funcionamiento de la herramienta en cuestión con el siguiente comando que se muestra en la imagen. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/rsync_de2a1.JPG)

Se nos pedirá la clave root en la máquina principal y después de unos segundos comprobaremos que el directorio escogido para clonar aparece en ambas máquinas, manteniendo los permisos y dueños de la máquina origen. 

*Prueba en la primera máquina (máquina principal). *
![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ls_la1.JPG)

*Prueba en la siguiente máquina.*
![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ls_la2.JPG)

2. Acceso sin contraseña para ssh. 

Aunque *rsync* puede ser de mucha ayuda es realmente costoso tener que mantener a mano la información que se vaya actualizando en las máquinas y queramos tener actualizada. 

Es por ello que debemos configurar *ssh* para que no necesite esperar contraseña y así agilizar el proces ode copia. 

Para ello se suele usar autenticación con un par de claves pública-privada. 

Y es así como mediante *ssh-keygen -t dsa* vamos a generar la clave.

En la máquina secundaria ejecutamos el comando especificado una línea más arriba, dejando en blanco la contraseña que se nos pide ya que es eso lo que andamos buscando (no tener que introducir contraseña alguna para la copia de archivos mediante ssh).
![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ssh_withoutpassword.JPG)

A continuación se copiará la clave pública creada a la máquina principal, a la que se quiere acceder) usando el comando *ssh-copy-id* integrando en ssh.  

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/ssh_withoutpassword_2_desdeMV1.JPG)

Y ya podremos conectarnos a dicho equipo sin problema. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/comprobacion_sincontrase%C3%B1a.JPG)


3. Programar tareas con contrab.  

Una vez tengamos configurado el uso de ssh sin necesidad de contraseña vamos a poder ejecutar scripts con el comando *rsync* para mantener actualizada la información de ambas máquinas.

**Cron** es un administrador de procesos que ejecuta procesos en el instante que indica el fichero crontab (en */etc/crontab*). 

Por lo tanto, debemos editar el fichero /etc/crontab añadiendo las tareas que creamos necesarias pero teniendo en cuenta la forma en la que están orgenizados los campos de las líneas de dichos ficheros. 

*Script que ejecutará la orden rsync.*
![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/script_ssh.JPG)

*Archivo /etc/crontab/ actualizado para que ejecute el script mostrado arriba.*
![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/crontab.JPG)

He aquí una prueba del funcionamiento de la tarea especificada en cron. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica2/Capturas/pureba_crontab.JPG)