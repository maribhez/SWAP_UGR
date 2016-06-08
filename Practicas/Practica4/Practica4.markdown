#Practica 4. 

## Comprobar el rendimiento de servidores web. 

El objetivo de esta práctica, tal y como se puede entender por el enunciado es medir el rendimiento de nuestros servidores web. 

Aunque se puede realizar ocn herramienta basadas en interfaz de línea de comandos y de interfaz gráfica nosotros nos vamos a centrar en interfaces de líneas de comandos. 

Por otro lado, aunque se pueden ejecutar las pruebas en máquinas pertenecientes a la granja web que vamos a analizar es conveniente hacerlo desde una máquina ajena, para de esta forma no sobrecargar el sistema y obtener datos erróneos. 

A la hora de observar los datos y sacar conclusiones sobre los mismos hemos de saber que: 

 1. Se añaden latencias adicionales por las comunicaciones que deben realizarse al realizar las pruebas de forma remota. 

 2. Las pruebas pueden dar como resultado valores diferentes porque el servidor puede tener un número diferente de procesos ejecutándose en cada momento, siendo por ello por lo que se realizar varias pruebas y se calcular la media y la desviación estándar para cada métrica recogida. 


- Herramienta número 1. **Apache Benchmark.**

La prueba se va a realizar bajo el siguiente archivo: 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/1.JPG)

Y metemos en la terminal creada para esta práctica el siguiente comando, sabiendo que había que repetir el proceso para cada una de las máquinas independientes y la máquina balanceadora (por esto los datos se almacenan en *m1_3.txt*, pues es la tercera iteración sobre la IP de la primera máquina). 

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/ejecuciones_bm_servidorm1.JPG)

Se realizan 1000000 peticiones de 100 en 100 peticiones concurrentes. 

*Nota:* Los datos no son mostrados, pero sí podemos observarlo gráficamente.

 
*Segundos necesarios para la ejecución comppleta. Media y desviación típica.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/GraficoMedias_AB.JPG)


![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/desv_tipica_TiempoNecesario_AB.JPG)



- Herramienta número 2. **Siege**

Esta es una herramienta de generación de carga HTTP para benchmarking, de interfaz similar a AB pero de opciones de ejecución diferentes.

Aquí muestro las gráficas obtenidas para estas comprobaciones. 


*Tiempo transcurrido.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/ElaspedTimeSiege.JPG)

*Tasa de transacción.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/TransactionRate_siege.JPG)

*Operación más larga.*

![img](https://github.com/maribhez/SWAP_UGR/blob/master/Practicas/Practica4/Capturas/LorgestTransaction.JPG)

*Nota:* Hay datos que no aparecen representados en estas gráficas y es por haber obtenido como resultado el mismo valor para todos (por ejemplo, ningún fallo para ninguna de las ejecuciones).






