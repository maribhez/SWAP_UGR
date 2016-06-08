#Práctica 3. 

## Balanceo de carga. 


En esta práctica nos dedicaremos a balancear (mediante soluciones software) la carga de los servidores HTTP que tenemos configurados. 

Dejaremos de lado el balanceo por DNS por los inconvenientes que presenta y usaremos las siguientes opciones:

- **Nginx.** 

##Instalación. 
Servidor ligero de alto rendimiento. 

El servidor con la IP pública ejecuta el nginx, que se ocupa de redirigir el tráfico a los servidores finales, y estos servidores pueden servir su contenido web con cualquier servidor (Apache, por ejemplo). 

Para instalar se hace uso del apt-get, no sin antes importar la clave del repositorio de software: 

*cd /tmp/*

*wget http://nginx.org/keys/nginx_signing.key*

*apt-key add /tmp/nginx_signing.key*

*rm -f /tmp/nginx_signing.key*

A continuación, añadimos el repositorio al fichero */etc/apt/sources.list*, y para ello ejecutamos las siguientes órdenes: 



*echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list*

*echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list*

Ahora, ya sí podemos instalar el paquete del nginx usando *apt-get update* y *apt-get install nginx*.

##Balanceo de carga. 

Como ya sabemos, la configuración básica de nginx corresponde a la funcionalidad de un servidor web, asi que debemos configurar su fichero de configuración /etc/nginx/conf.d/default.conf para poder usarlo. 

Eliminamos el contenido que hubiera anteriormente y añadimos el que nos haga falta: definimos las máquinas que forman nuestro cluster (en *upstream*), y le indicamos en *server* cuál es el grupo de IPs que debe usar para balancear (entre otras cosas).

Quedaría la configuración del servicio de la siguiente manera. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/upstream_nginx.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/server_nginx_1.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/server_nginx_2.JPG)

Una vez que lo tenemos configuramos, iniciamos el servicio del balanceador y pasamos a probarlo usando *curl 192.168.89.131*, siendo ésta la dirección de la máquina del balanceador. 

a prueba de que cada vez que accede a la página te redirige a una máquina diferente aparece en las siguientes capturas. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/prueba_balanceador1.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/prueba_balanceador2.JPG)



- Haproxy.

##Instalación: 
    
 ![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/instalacion_haproxy.JPG)

##Configuración: 

    Una vez instalado debemos modificar el archivo de configuración para obtener así un correcto funcionamiento según lo que queremos.     

*cd /etc/*
*cd /haproxy/*
*sudo nano haproxy.cfg*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/conf_haproxy.JPG)


##Balanceo de carga. 

El primer paso sería lanzar Haproxy, usando para ello el siguiente comando: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/lanzar_haproxy.JPG)

 Ahora, de la misma forma que probamos el balanceador Nginx podemos comprobar este (usando *curl httl://192.168.89.131*). 
 
Prueba 1: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/haproxy_maq1.JPG)

Prueba 2: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/haproxy_maq2.JPG)

- Varnish. 

Como parte opcional en esta práctica 3 yo he llevado a cabo la instalación, configuración y prueba del balanceador Varnish, opción dada en la lista de balanceadores al principio del guion. 

##Instalación. 

Igual que hemos tenido que hacer con anteriormente para otras opciones, a la hora de instalar Varnish es necesario añadir el repositorio, y en este caso se hace mediante el siguiente comando: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/aniadir_repositorio_0_varnish.JPG)

Y una vez añadido a nuestra lista de repositorios, y antes de proceder al uso del comando *apt-get* es necesario usar lo siguiente para añadir el repositorio a la lista de fuestes:

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/repositorio_varnish.JPG)



##Configuración. 

Paramos el servicio: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/varnish_opcional_pararservicio.JPG)

Ahora, editamos el fichero de configuración */etc/default/varnish*.

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/configuracion_varnish.JPG)


##Prueba. 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/funcionando_varnish_1.JPG)

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica3/Capturas/funcionando_varnish_2.JPG)

