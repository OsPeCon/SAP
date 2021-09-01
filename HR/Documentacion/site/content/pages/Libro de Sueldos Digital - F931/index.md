---
title: Libro de Sueldos Digital.
date: Last Modified
permalink: /Libro de Sueldos Digital - F931/
eleventyNavigation: 
    key: librosdesueldos
    order: 1
    title: Libro de Sueldos Digital.
---



Descripcion breve del proceso:

Esta funcionalidad será utilizada para completar las nóminas
equivalentes de la AFIP con las que estamos utilizando en SAP, como así también
tildar para cada nómina el casillero que corresponda de los distintos conceptos.
Una vez subida y conformada esta información con la AFIP se está habilitada para
utilizar el LSD.

En base a la tarea detallada anteriormente se deberá cargar en
forma mensual la liquidación de los sueldos en la AFIP.

---

---

## Proceso paso a paso:


**Metodologia** 

Transacción  :   PC00_M29_CLSD

Datos a ingresar:

Código de la AFIP para LSD: se seleccionará el equivalente del mismo para el detalle de la

Código nómina de SAP que  figura en la pantalla y de deberá tildar los  casilleros que correspondan de los distintos conceptos.

El sistema muestra lasiguiente pantalla:

![img](../content/images/Libro_de_Sueldos_Digital_F931/1630424321657.png)


Datos a integrar:

Código de la AFIP para LSD: se seleccionará el equivalente del mismo para el detalle de la

Código nómina de SAP que  figura en la pantalla y de deberá tildar los                                                 casilleros
que correspondan de los distintos conceptos

Una vez que se termina de trabajar asociando códigos de AFIP con nóminas propias y verificado
que no hay errores, marcando la línea correspondiente y luego dar un clic en el
icono “verificar entradas” como se muestra en la siguiente pantalla:

![img](../content/images/Libro_de_Sueldos_Digital_F931/1630432400509.png)


Si no hay errores para ir guardando la información se deberá dar un clic en el ícono de Generar TXT de acuerdo a lo
siguiente:

![](file:///C:\Users\mprager\AppData\Local\Temp\msohtmlclip1\01\clip_image002.jpg)![](../content/images/Libro_de_Sueldos_Digital_F931/1630432478029.png)


1 - A continuación se procederá a guardar el mismo:
![img](../content/images/Libro_de_Sueldos_Digital_F931/1630432503637.png)

Cuando se retoma la tarea para seguir asociando nóminas de AFIP con las propias se deberá
dar clic en el ícono “Cargar TXT” de acuerdo a la siguiente pantalla

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432535758.png)

Se deberá colocar l nombre del archivo que se guardó la información ya creada y el
sistema mostrará la pantalla con los datos incorporados anteriormente de
acuerdo a lo siguiente:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432556419.png)


Luego de incorporada nueva información y para
guardar la misma se deberá proceder de acuerdo a lo detallado en el
punto 1.

Esta asociación de las nóminas es muy importante y se deberá prestar especial
atención en hacer una correcta equivalencia para evitar errores al procesar la
información en el aplicativo de la AFIP para generar en forma correcta el
archivo de la Seguridad Social y efectuar el pago de aportes y contribuciones.


Detalle del proceso: 

Para la emisión del Libro Digital se efectuará en forma mensual este proceso en donde
se detallan los distintos conceptos liquidados a los empleados

Transacción SAP: PC00_M29_F931

Mostrará lasiguiente pantalla que a título de ejemplo es el proceso de un empleado:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432596580.png)

Al ejecutar la misma muestra la siguiente información en donde se detalla
que la persona ha sido procesada en forma correcta:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432616231.png)![](../content/images/Libro_de_Sueldos_Digital_F931/1630432616231.png)

Al abrir el detalle de los distintos conceptos el sistema muestra la
siguiente información



En el Reg 1 “Datos referenciales del envío” Nro. De CUIT del empleador

En el Reg 2  “Datos de la liquidación”
muestra los datos del empleado de acuerdo a la siguiente información:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432657633.png)

Al dar clic
en Registro 3 “Detalle de los conceptos” muestra el detalle la liquidación como
se muestra a continuación:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432678100.png)![](../content/images/Libro_de_Sueldos_Digital_F931/1630432678100.png)


Al dar clic en Regi 4 “Datos del trabajador” el sistema muestra la
siguiente información:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432694990.png)

Esto es el detalle de la liquidación efectuada a un empleado en sus
distitntos conceptos y que fue procesada en forma correcta al ejecutar esta
transacción.

Para procesar
el archivo y subirlo a la AFIP se deberá:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432734310.png)

Si está todo correcto se debe dar clic en Archvio Temse y el sistema
muestra la siguiente pantalla:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432749083.png)![](../content/images/Libro_de_Sueldos_Digital_F931/1630432749083.png)

Se deberá dar clic en la lupa y el sistema mostrará la siguiente
información:

![](../content/images/Libro_de_Sueldos_Digital_F931/1630432773888.png)


Hacer
el Download para guardar el archivo y subirlo a la AFIP.

Dentro del módulo de Liquidaciones y DDJJ se deben cumplir los
siguientes procesos:

- Cargar Liquidación
- Validar la Liquidación
- Aceptar la liquidación
- Generar Libro de sueldos
- Presentar la Declaración Jurada
  F931

Documentación Técnica:

Nota SAP 2770358

Manual SAP Nota 2770358

Manual Libro de Sueldos Digital  de
la AFIP

Manual de Libro Digital de empresa especializada en HR



### Casos / Preguntas frecuentes

No existen casos a la fecha

---

---

## Documentacion Técnica

**En SAP:**

* TRANSACCION: PC00_M29_CLSD - Asignacion de nominas a conceptos
* TRANSACCION: PC00_M29_F931 - Generacion de Libro Digital
