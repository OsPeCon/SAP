---
title: Listado de Cuentas.
date: Last Modified
permalink: /Listado de Cuentas/
eleventyNavigation: 
    key: listadodecuentas
    order: 1
    title: Listado de Cuentas.
---
### Descripción breve del proceso:

Esta funcionalidad será utilizada para determinar los empleados que no tienen incorporado en el sistema el número de cuenta o el CBU al que se debe transferir el importe del sueldo neto. En base al mismo el Sector de Sueldos deberá incorporar a los legajos que no tengan esta información ingresando los datos correspondientes en el sistema SAP.


## Proceso paso a paso :

Transaccion ZCUENTASBANCO 

![img](../content/images/Listado_de_cuentas/hrldc1.jpg)


Datos a integrar:

Se debe ingresar los datos correspondientes ya sea por una División de Personal o para una determinados legajos de personal según corresponda y en un rango de fechas determinado.

Al ejecutar la transacción el sistema muestra la siguiente pantalla:

![img](../content/images/Listado_de_cuentas/hrldc2.jpg)

La información podrá exportarse a excel y filtrar el mismo de acuerdo a la informacón que se requiera:

![img](../content/images/Listado_de_cuentas/hrldc3.jpg)

Se podrá clasificar la misma de acuerdo a la información necesaria por ejemplo legajos sin CBU y se obtiene el listado con la  información requerida:

![img](../content/images/Listado_de_cuentas/hrldc4.jpg)

Transacción SAP:   PA30

Para dar de alta el CBU de los legajos correspondientes se deberá ingresar a esta transacción y el sistema muestra la siguiente pantalla:

![img](../content/images/Listado_de_cuentas/hrldc5.jpg)

Se deberá seleccionar el infotipo de Relación Bancaria y el sistema muestra la siguente pantalla:

![img](../content/images/Listado_de_cuentas/hrldc6.jpg)

Información a ingresar en esta pantalla:

DE: fecha a partir de la cual tiene vigencia la información
CL Clav. Datos Bancarios: Seleccionar la opción Relación bancaria principal
RECEPTOR: Nombre y apellido del empleado
CODIGO POSTAL Y LOCALIDAD: código correspondiente y nombre de la localidad
PAIS RECEPTOR Y BANCO. Argentina en todos los casos
CLAVE DE BANCO: el còdigo que corresponda 093 en el caso del Banco La Pampa
CUENTA BANCARIA Y CLASE: número de cuenta y la clase en este caso CA caja de ahorros
VA PAGO:  T   transferencia en todos los casos
CBU: el asignado al empleado por el Banco
MONEDA DE PAGO:  ARS moneda argentina

Al finalizar se debe grabar para que los datos queden incorporados en el sistema.


### Casos / Preguntas frecuentes


## Documentacion Técnica

