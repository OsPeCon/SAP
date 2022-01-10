---
title: DIGITALIZACION.
date: Last Modified
permalink: /DIGITALIZACION/
eleventyNavigation:
    key: digitalizacion
    order: 40
    title: DIGITALIZACION.
---
## **DIGITALIZACION DE DOCUMENTOS**

**Descripción breve del proceso:**

Emision , Impresion y envio de facturacion.

## Proceso paso a paso:

INSTALACION DE APLICATIVO PARA ESCANEAR

El aplicativo .net se instala en el perfil del usuario a escanear. 
\\uocradevnet\Librerias\Repositorios\SAPScanRecibos\Setup.exe
El programa está configurado para guardar los archivos según el perfil asociado al grupo de trabajo (RSARRA = CONTABLE, 	VLOSCOCCO = FINANZAS, RKRAISKI=CONTROLDEOBRAS)
\\uocrafs\SectorContable\aprocesar
\\uocrafs\SectorControldeobras\aprocesar
\\uocrafs\SectorFinanzas\aprocesar

![img](image/index/1628705225985.png)

2SAP - DIGITALIZACION DE DOCUMENTOS: FACTURAS  - RECIBOS – PRESUPUESTOS

Función para traer las órdenes de Pago a tener en cuenta y verificar cuales tiene recibo y cuales no:
Z_VERIFICA_ATTACH_GOS (tanto para cheque como transferencia).

CONFIGURACION ESTANDAR

Trx. SM31

![img](image/index/1628705242254.png)

Modificamos el nombre a:             

![img](image/index/1628706183893.png)


Trx. SM31

![img](image/index/1628706349801.png)


En esta vista, agregamos la entrada para “crear anexo” que vemos en la vista anterior y la ponemos DESACTIVAMOS.

![img](image/index/1628706349801.png)


Alta de Ruta destino Origen de archivos

Se16: V_FILEPATH
Se16: V_filenaci

Trx. FILE



COMPORTAMIENTO FUNCIONAL

Desde la Trx. FB02 o FB03
CREACION de Documento escaneado

![img](image/index/1628706349801.png)

Te lleva a esta pantalla: 

![img](image/index/1628706349801.png)


Título: por ejemplo Factura

Dirección: Click Derecho, Insertar Fichero.

Mediante un acceso directo en el escritorio  que apunta al Servidor, se selecciona el documento escaneado


![img](image/index/1628706349801.png)

VISUALIZACION de Documento escaneado

![img](image/index/1628706349801.png)

Te lleva el o los documentos

![img](image/index/1628706349801.png)

CARPETAS/ NOMBRES ARCHIVOS/ FORMATO/ TAMAÑO

Las carpetas a crear serán las siguientes

**	FACTURA DIGITAL
**	RECIBO DIGITAL


Nombre de las facturas a guardar: Cuit_Sociedad_nroDocSAP_Ejercicio_TipoDOC.pdf
•	Sociedad: 0100 OSPECON y 0200 UOCRA
•	Ejercicio: Año
•	NroDocSAP: de 10 dígitos (completar con ceros a la izq.).
Ejemplo: 20123415036_0100_0100003481_2017_R


PERMISOS

CARPETAS:

Sectores que realizaran el escaneo y carga de URL de recibos:
•	Finanzas
•	Contable

Sectores que realizaran el escaneo y carga de URL de facturas:
•	Contable
•	Cuentas a Pagar
•	Hospitales
•	Patrimonio
•	Control de Obas
•	Mesa de Entradas? (en función del circuito que se defina)


Estos sectores deberán tener acceso a las carpetas.
Solo los jefes podrán borrar y mover archivos creados (control total).
El resto de usuarios solo crear archivos.

SAP:
No tendrá determinación de permisos, ya que los usuarios que tengan acceso a los documentos van a poder crear la URL.

LISTADO		

Datos de Selección: Ejercicio y número de proveedor.

Posibilidad de sacar un listado de todas las órdenes de pago por proveedor, con la marca que  posee recibo escaneado.
INVESTIGAR COMO SE DETERMINA LA MARCA DE URL ASOCIADA

(Es muy complicado si el sistemas debe fijarse el número de proveedor por archivo escaneado).


TABLA QUE CONTIENE DOCUMENTOS DIGITALIZADOS:
SRGBTBREL






## **Casos / Preguntas frecuentes**

Caso 1:

Caso 2:

---

## Documentación Técnica
