# Tecnología de la Información
## Documento Tecnico

**Envío automático vía mail de notas de débito y credito propias** 

**Área de aplicación:**	Cuentas a Pagar y Hospitales

**Fecha:** 08/06/21

**Dirigida a:**	Diego Tamargo, Luis Rodriguez, OScar Burgos, Esteban Lucano

**CC.**	Tecnologia de la Informacion

**Confeccionada por:** Mariela Etcheverry

***

# Objetivo
Envio de 

# Especificacion
•	FORMULARIO:  ZSF_DEB_CRED (smart form) 
Emisión de notas de débito propias registradas en SAP: Clase de clases de documento son KB y KD.

•	TRANSACCION: ZFI_ENVIO_ND ,,,,,,,
PROGRAMA: ZFI_ENVIO_MAIL_DEB_CRED

Datos de selección del programa:
•	Nro. débito SAP:
•	Fecha de entrada:
•	Fecha de contabilización
•	Nro. legal factura
•	Nro. factura SAP 
•	Proveedor

Envío de mail con las notas de débito adjuntas, más la hoja resumen emitida desde presmed.
	Ejecución automática: diaria,  schedulleada para las 23 hs todos los días.
	Opción de Ejecución manual 
La opción automática controlara la duplicidad del envío, no siendo así para la ejecución manual.



Mail: 
•	Remitente:
•	Título: 
•	Cuerpo del mail: SO10, TEXTO “ZFI_MAIL_ND


Tabla de control de envios realizados: 
	
Campos:
	Sociedad: BESEG BUKRS
	Nro. Documento:  BESEG BELNR
	Referencia: BKPF XBLNR
	Proveedor: BSEG LIFNR
	Mail: programa
	Fecha de envio: programa
	Usuario documento: usuario envio mail (si fue enviado por el programa schedulleado, que indique “AUTOMATICO”; sino que indique el usuario que ejecuto el programa en forma manuak


•	OTROS: 
	Creación de carpeta uocrafs/prodpresmed/expediente. OK
	Alta en SAP transacción ZFI_ENVIO_ND en el rol simple:  RS9999_FI-AP_PRESMED
	Alta Matriz
	Alta Inventario Z
	Schedulleo de Programa ZFI_ENVIO_MAIL_DEB_CRED







# Ejemplo con viñetas

* Lista 1
  * Lista 1.1
  * Lista 1.2
  * Lista 1.3
* Lista 2
  * Lista 2.1
  * Lista 2.2