*Alumna: Maria del Mar Ibáñez Hernández. Curso 2015-2016.*

 <b style='color:orange'>Ejercicio 1 (Tema 1) </b>

Buscar información sobre las tareas o servicios web para los que se usan más los siguientes programas: 

* **Apache.** 
Es un *servidor web HTTP* de código abierto para la creación de páginas y servicios web. Un servidor multiplataforma, gratuito, muy robusto y que destaca por su seguridad y rendimiento.

* **Nginx.** ES un *servidor web/proxy* inverso ligero de alto rendimiento y un *proxy* para protocolos de correo electrónico (IMAP/POP3). Este siestema es usado por sitios tan conocidos como GitHub, WordPress, Netflix, WordPress o SourceForge. 

* **Httpd.** Es un programa que corre de fondo en un servicio web y espera peticiones de entrada para darles respuesta. Puede referirse, entre otros, a: Servidor Apache HTTP, Servidor Nginx HTTP y Servidor Lighttpd HTTP. 

* **Cherokee.** Es un servidor web multiplataforma, cuyo objetivo es ser rápido y funcional sin dejar de ser ligero con respecto a los otros servidores web. Se dice que es hasta 6 veces más rápido que el arriba descrito (Apache). Al igual que Nginx, puede ser implementado como balanceador de carga para otros servidores web como Apache o Nginx. 

* **Node .js**. Es un entorno de ejecución multiplataforma, de código abierto, para la capa del servidor (pero no limitándose a ello) basado en ECMAScript. 

-**Diferencias entre Node .js y otros servidores web.**

Por ejemplo, Apache crea un hilo por cada conexión cliente-servidor, y esto funciona bien sólo para pocas conexiones, pero crear hilos nuevos es algo costoso, asi como los cambios de contexto. A partir de un determinado número de conexiones simultaneas el número de segundos necesarios para atender las peticiones crece considerablemente. Sin embargo, éste es uno de los puntos fuertes de Node, su capacidad para mantener conexiones abiertas y esperando. 
Una aplicación para Node se programa en un solo hilo. Si en la aplicación existe una operación bloqueante (por ejemplo I/O) Node creará otro hilo en segundo plano, pero no lo hara sistemáticamente por cada conexión. Por lo tanto, Node es bueno en aquellas aplicaciones necesarias de una conexión persistente con el navegador del cliente, siendo ejemplos de estos juegos online, gestores de correo online, chats, redes sociales y herramientas de traducción en tiempo real. 

