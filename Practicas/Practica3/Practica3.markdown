#Práctica 3. 

## Balanceo de carga. 


En esta práctica nos dedicaremos a balancear (mediante soluciones software) la carga de los servidores HTTP que tenemos configurados. 

Dejaremos de lado el balanceo por DNS por los inconvenientes que presenta y usaremos las siguientes opciones:

- **Nginx.** 

##Instalación. 
Servidor ligero de alto rendimiento. 

El servidor con la IP pública ejecuta el nginx, que se ocupa de redirigir el tráfico a los servidores finales, y estos servidores pueden servir su contenido web con cualquier servidor (Apache, por ejemplo). 

Para instalar se hace uso del apt-get, no sin antes importar la clave del repositorio de software: 

*cd /tmp/
wget http://nginx.org/keys/nginx_signing.key 
apt-key add /tmp/nginx_signing.key
rm -f /tmp/nginx_signing.key*

A continuación, añadimos el repositorio al fichero */etc/apt/sources.list*, y para ello ejecutamos las siguientes órdenes: 



*echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list*

Ahora, ya sí podemos instalar el paquete del nginx usando *apt-get update* y *apt-get install nginx*.

##Balanceo de carga. 