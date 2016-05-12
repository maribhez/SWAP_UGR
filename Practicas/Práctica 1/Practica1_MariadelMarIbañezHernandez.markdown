 <b style='color:orange'> Practica 1. </b> 

 

<b style = 'color : orange'> Preparación de las prácticas y prepararación de las herramientas.  </b>

Esta práctica es meramente preparativa. Preparativa de cara a la siguientes prácticas, ya que vamos a dejar a punto todos las máquinas virtuales que nos van a hacer falta en un princpio. 

Ante las posibilidades de elección yo haré las prácticas bajo el software VMPlayer (VMWare), por cercanía al mismo. Dicho programa puede ser descargado del siguiente enlace: 

[Enlace a la descarga de VMPlayer](http://www.vmware.com/products/player/ "Enlace a la descarga de VMPlayer")

Por otro lado, aunque en el guión de esta práctica se facilitaba la dirección URL para *Ubuntu Server 12.04 1 LTS (32 bits)* yo estoy usando *Ubuntu Server 14.04 4*.


Así, para ir explicando y especificando todos los pasos seguidos para cumplimentar lo pedido separo todo el proceso en varios pasos explicados a continuación: 

* *Primer paso*: Instalación de las máquinas Linux con Ubuntu Server. 

![Instalación de la primera máquina. ](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/InstalacionMV1.PNG "Instalación de la primera máquina.")

 * *Segundo paso*: Durante la instalación de esta máquina no apareció la opción de instalar LAMP, por lo que tuve que instalar de forma manual Apache, PHP y MySQL. 
 
![Instalación de LAMP](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/LAMP_2.PNG "Instalación de LAMP")

![ComprobacionServidorWeb](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/maquina2Ultimo.PNG "ComprobacionServidorWeb")

* *Tercer paso:* Instalación de CURL (para comprobar que el servidor web está activo).

Tanto para la máquina 1 como para la segunda máquina el comando a ejecutar ha sido el mismo: ***sudo apt-get install curl*** (aceptando, como siempre, los requisitos de memoria que dicho programa necesita). 

* *Cuarto paso:* Crear archivo de prueba para comprobar que Apache está funcionando con el siguiente contenido: 

       ![PruebaApache](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/m1_hola.PNG "PruebaApache")
       

* *Quinto paso:* Acceder a la página de prueba creada usando la URL de nuestro servidor. Adjunto captura de la demostración del funcionamiento en ambas máquinas: 


![PruebaCurlMaquina1](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/curl1.JPG "PruebaCurlMaquina1")

![Prueba del comando curl](C:/Users/Mmar/Desktop/Universidad/SWAP/Practicas/Practica1/Capturas/maquina2.PNG "Prueba del comando curl")

