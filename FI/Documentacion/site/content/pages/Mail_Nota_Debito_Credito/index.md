# Envío Automático de Mail de NC y ND

## Descripcion breve del proceso:
Envío automático por mail a los prestadores, del detalle de Notas de Crédito y Notas de Débito propias tanto médicas como administrativas.
Los adjuntos al mail serán los formularios de ND y NC y la hoja de detalle de débitos generada por Presmed.

***
***

## Proceso paso a paso:
Si bien la transaccion de envio de mail con los adjuntos se ejecuta en forma automatica todos los dias, existe la forma de que el usuario la ejecute en forma manual, la cual se explica a continuacion:

ENVIO MANUAL POR EL USUARIO:

**TRANSACCION: ZFI_ENVIO_ND**

Datos de selección del programa: 
* Sociedad: 0100
* Nº Nota D/C: indicar el nro de debito o credito por el que va a enviarse el mail
* Proveedor: indicar el proveedor
* Fecha de registracion: fecha de registracion del debito o credito
* Fecha de documento: fecha de documento del debito o credito
* Fecha de facturacion: fecha de la factura
* Factura: nro. SAP de factura
* Observaciones: si se tilda este campo, se imprimira al pie del formulario de la ND el texto determinado en la configuracion.
* Resumen Expediente Presmed: Indicar si el debito sap se envia con o sin la hoja resumen de presmed.

Los mails se enviaran desde las siguientes casillas de correo: 
- Para Sucursal 0004: noreply-hospitales@uocra.org 
- Para Sucursal 0002: noreply-cuentasapagar@uocra.org

Si el envio es para una nota de credito, el mail no llevara hoja resumen de presmed

Si es ND, tiene que tener adjunto de hoja resumen de Presmed

**Transaccion de reporte envios: ZFI_ENVIO_ND_L**

Esta trasnacción se podra utilizar para analizar los envios de mails realizados.


### Casos / Preguntas frecuentes
No existen casos a la fecha 

***
***
## Documentacion Técnica

**En Presmed:**

•	Generación y guardado de hoja resumen de débitos médicos y administrativos en el directorio: uocrafs/prodpresmed/expediente 

•	Nombre del archivo: EXP_XXXXXXXXXX.pdf (siendo XXXXXXXX el nro. de expediente generado en Presmed) 

•	Actualización  la hoja resumen en función de la generación de débitos subsiguientes.

•	Generación de hoja resumen por expediente “desde - hasta”.


**En SAP:** 

* TRANSACCION: ZFI_ENVIO_ND

* PROGRAMA: ZFI_ENVIO_MAIL_DEB 
(Transaccion de Impresión call transaction: ZNOPN en programa de envio que llama al smartform)

* FORMULARIO:  ZSF_DEB_CRED2 (smart form) 
Formulario de notas de débito y credito propias registradas en SAP: Clase de clases de documento son KB, KD y KG
Configuración en SO10: el TEXTO “ZDETALLENOTA”, contiene el detalle que se imprime al pie del smartform de la ND o NC cuando se marca el pop up "observaciones" en el programa.

Datos de selección del programa:
•	Nro. débito SAP:
•	Fecha de entrada:
•	Fecha de contabilización
•	Nro. legal factura
•	Nro. factura SAP 
•	Proveedor

El programa realiza envío de mail con las notas de débito y debito adjuntas, más la hoja resumen de detalle de debitos emitida desde presmed.

-Ejecución automática: diaria,  schedulleada para las 23 hs todos los días.

-Variantes:

Hospitales KD-KB-KG (Hospitales Viernes):
Solo se envia el dia viernes toda la semana de debitos/creditos generados al grupo de cuentas 0004.

KD DEBITO ADM (Cuentas a pagar -10): Se envia 10 dias posteriores al registro de los documentos KD al grupo de cuentas 0004 (Exepto prestador 5880).
KD DEBITO ADM2 (Cuentas a pagar Sin Hoja -10)
Doc. KD sin hoja de servicio: al grupo de cuentas 0004 (Solo prestador 5880).
KB DEBITO MED (Cuentas a pagar -3)
KB: Doc. KB se envian 3 dias posteriores al registro del grupo de cuentas 0004.
KG Credito (Cuentas a pagar Diario)
KG: Todos los dias.

-Opción de Ejecución manual 
La opción automática controlara la duplicidad del envío, no siendo así para la ejecución manual.

EL programa realiza un control del usuario que envio el mail, si es LTAMARGO1 impide que se envie 2 veces. Si es otro usuario, es sin limite.


Configuración de Mail: 

    Remitentes: 
    1. noreply-hospitales@uocra.org y 
    2. noreply-cuentasapagar@uocra.org

    Título: Tipo Documento+Numero sapDoc. (Ej. Débito Médico Nº 0002A00037014)

    Cuerpo del mail: TEXTO configurado en SO10,  “ZFI_MAIL_ND”

    Observaciones: se imprime al pie del smartform de la ND o NC el texto de la SO10 “ZDETALLENOTA”

VaLidaciones en Transaccion ZNOPN 

    Códigos:
    * 02: ND A
    * 07: ND B
    * 03: NC A
    * 08: NC B

Hoja Resumen Presmed:
Si es NC NO tiene adjunto de hoja resumen

Si es ND, tiene que tener adjunto de hoja resumen de Presmed. El adjunto lo busca por expediente en el texto cabecera (BKPF BKTXT) del BKPF BELNR, ejercicio y sociedad, en la carpeta \\uocrafs\DEVPresmed\Expediente nombre archivo pdf EXP_0000332445
Si lo encuentra, envía el mail y sino cancela el envio y avisa en el log.


Tabla de control de envios realizados: 
ZCONTROL_MAIL

Transaccion de reporte envios: ZFI_ENVIO_ND_L

