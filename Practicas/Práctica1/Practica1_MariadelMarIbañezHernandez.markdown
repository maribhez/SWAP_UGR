 <b style='color:orange'> Practica 1. </b> 

 

<b style = 'color : orange'> Preparación de las prácticas y prepararación de las herramientas.  </b>

Esta práctica es meramente preparativa. Preparativa de cara a la siguientes prácticas, ya que vamos a dejar a punto todos las máquinas virtuales que nos van a hacer falta en un princpio. 

Ante las posibilidades de elección yo haré las prácticas bajo el software VMPlayer (VMWare), por cercanía al mismo. Dicho programa puede ser descargado del siguiente enlace: 

[Enlace a la descarga de VMPlayer](http://www.vmware.com/products/player/ "Enlace a la descarga de VMPlayer")

Por otro lado, aunque en el guión de esta práctica se facilitaba la dirección URL para *Ubuntu Server 12.04 1 LTS (32 bits)* yo estoy usando *Ubuntu Server 14.04 4*.


Así, para ir explicando y especificando todos los pasos seguidos para cumplimentar lo pedido separo todo el proceso en varios pasos explicados a continuación: 

* *Primer paso*: Instalación de las máquinas Linux con Ubuntu Server. 

*Máquina 1.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/InstalacionMV1.PNG)

*Máquina 2.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/InstalacionMV2.PNG)




Y por último, antes de seguir con el segundo paso adjunto la demostración de ambas máquinas en funcionamiento. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/maquinas_funcionando.PNG)

 * *Segundo paso*: Durante la instalación de esta máquina no apareció la opción de instalar LAMP, por lo que tuve que instalar de forma manual Apache, PHP y MySQL. 
 
*Máquina 1.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/LAMP_1.PNG)


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/m1-Final.PNG)

*Máquina 2.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/LAMP_2.PNG)


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/maquina2Ultimo.PNG)







* *Tercer paso:* Instalación de CURL (para comprobar que el servidor web está activo).

Tanto para la máquina 1 como para la segunda máquina el comando a ejecutar ha sido el mismo: ***sudo apt-get install curl*** (aceptando, como siempre, los requisitos de memoria que dicho programa necesita). 

* *Cuarto paso:* Crear archivo de prueba para comprobar que Apache está funcionando con el siguiente contenido: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/m1_hola.PNG)
       

* *Quinto paso:* Acceder a la página de prueba creada usando la URL de nuestro servidor. Adjunto captura de la demostración del funcionamiento en ambas máquinas: 


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/curl1.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Pr%C3%A1ctica1/Capturas/maquina2.PNG)


