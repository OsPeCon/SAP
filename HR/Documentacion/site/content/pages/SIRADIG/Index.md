---
title: Siradig.
date: Last Modified
permalink: /SIRADIG/
eleventyNavigation:
    key: siradig
    order: 4
    title: Siradig.
---
# Tecnología de la Información

## SIRADIG

Instructivo para Ejecutar la nueva interfaz del SIRADIG

## Proceso paso a paso:

Transacción: ZARPY_TRX_NVA_SIRAD
Programa: ZARPY_PRO_IN_OSP_SIRADIG
Se ejecuta la Transacción : ZARPY_TRX_NVA_SIRAD y se muestra la siguiente pantalla:

![img](../content/images/SIRADIG/s1.jpg)

Luego, se ingresan los datos:
-	Sociedad,
-	Nro de Personal
-	Ruta Archivo, donde se encuentra el XML.

![img](../content/images/SIRADIG/s2.jpg)

Primero lo ejecutamos en modo test, para verificar que no se encuentren errores en el archivo.
Ejecutar  

![img](../content/images/SIRADIG/s3.jpg)

Vamos a log

![img](../content/images/SIRADIG/s4.jpg)

Para este caso, no se encontraron errores, el log esta vacío:

![img](../content/images/SIRADIG/s5.jpg)

Ya podemos procesar sin el modo test, quitamos el check:

![img](../content/images/SIRADIG/s6.jpg)

Y ejecutamos  
Se muestra el siguiente reporte

![img](../content/images/SIRADIG/s7.jpg)

El campo Acción, indica: 
A – Cuando se van a dar de alta los registros.
B – Se borran registros, en este caso, aparecen cuando se vuelve a reprocesar el archivo y se borran lo datos que ya estaban y se vuelven a crear. Es decir, que en el reporte se verán los registros a Borrar (B) y luego los registros a Insertar (A).
Una vez que se verifican los valores, ejecutar:

![img](../content/images/SIRADIG/s8.jpg)

![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)
![img](../content/images/SIRADIG/s1.jpg)




## Proceso paso a paso:
