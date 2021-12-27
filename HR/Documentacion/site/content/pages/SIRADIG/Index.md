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

- Sociedad,
- Nro de Personal
- Ruta Archivo, donde se encuentra el XML.

![img](../content/images/SIRADIG/s2.jpg)

Primero lo ejecutamos en modo test, para verificar que no se encuentren errores en el archivo.

Luego Ejecutar

![img](../content/images/SIRADIG/s3.jpg)

Vamos a log

![img](../content/images/SIRADIG/s4.jpg)

Para este caso, no se encontraron errores, el log esta vacío:

![img](../content/images/SIRADIG/s5.jpg)

Ya podemos procesar sin el modo test, quitamos el check:

![img](../content/images/SIRADIG/s6.jpg)

Y ejecutamos

![img](../content/images/SIRADIG/s7.jpg)

Se muestra el siguiente reporte

![img](../content/images/SIRADIG/s8.jpg)

El campo Acción, indica:

A – Cuando se van a dar de alta los registros.

B – Se borran registros, en este caso, aparecen cuando se vuelve a reprocesar el archivo y se borran lo datos que ya estaban y se vuelven a crear. Es decir, que en el reporte se verán los registros a Borrar (B) y luego los registros a Insertar (A).

Una vez que se verifican los valores, ejecutar:

![img](../content/images/SIRADIG/s8.jpg)

Se mostrará un log con el resultado

![img](../content/images/SIRADIG/s9.jpg)

Luego  en la vista de presentaciones (ZARPY_TAB_OSP019), queda actualizado el empleado procesado.
Se ingresa con la transacción ZHR_PRESENT_SIRADIG

Ejemplo:

![img](../content/images/SIRADIG/s10.jpg)

En el caso de querer volver a procesar el mismo archivo, será necesario, eliminar este registro, accediendo por la SM30.
Luego verificar que los datos en los infotipos 0390 y 0391, hayan sido actualizados correctamente:

![img](../content/images/SIRADIG/s11.jpg)

La interfaz interactúa con las siguientes tablas

1. ZARPY_TAB_OSP017– Tabla de desglose Motivo deducción 99

![img](../content/images/SIRADIG/s12.jpg)

2. ZARPY_TAB_OSP018 – Tabla de equivalencias AFIP 0390 Y 0391

![img](../content/images/SIRADIG/s13.jpg)

3. ZARPY_TAB_OSP019- Tabla de Presentaciones:  esta tabla se completa cuando se ejecuta la interfaz del Siradig.
   Cuando se quiere reprocesar el archivo, se tendrá que eliminar el registro correspondiente de dicha tabla.
