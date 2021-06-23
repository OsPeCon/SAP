# Preliminares Integración y No Integración

## Descripción breve del proceso:
Generación automatica de los documentos preliminares correspondientes a las facturas Integración y no Integración (ex sur)

***
***

## Proceso paso a paso:
Los documentos se cargan en una app externa, el cual a través de JSON ingresan a SAP (Programa zws_preliminares para cargar y  programa zws_borraprel para borrar).
De mismo modo  en forma de documento Preliminar. 
### Casos / Preguntas frecuentes


Column A | Column B | Column C
---------|----------|---------
 dddddddddddd | B1 | C1
 A2 |ddd | C2
 A3 | B3 | C3
***
***
## Documentacion Técnica

**Llamada JSON:**

CARGA PRELIMINARES NO INTEGRACION:
URL: http://saphanaprod:8000/sap/opu/odata/sap/ZAPI_PRELIMINARES_SRV/PrelimDosPoSet/

AUTORIZATION: 
Basic Auth: Usuario y contraseña SAP. (Solo Para Metodo GET)

HEADERS:
x-csrf-token = Generar token (Con Metodo GET) 

BODY:
RAW
formato (JSON): 
```json
{"Bukrs": "0100",
 "Zzidexterna": "1600",
 "Blart": "KR",
 "Bldat": "2021-03-28T00:00:00",
 "Monat": "02",  
 "Gjahr": "2021",
 "Xblnr": "00001A12345679",
 "Bktxt": "PEREZ RICARDO E - 2021.02",
 "Brnch": "",
 "Ltext": "\\Uocrafs\\DigitalizacionMesadeEntrada",
 "Zltext": "d2a06550-187e-4fe3-9129-b2fea70b06e4",
 "Zzextension": "jpeg",  
 "Newko": "1060",
 "Wrbtr": "10.23",
 "Zuonr": "00001A22345678",
 "Sgtxt": "RAMALLO - PEREZ RICARDO ENRIQUE - 2021.02",
 "Xref1": "",
 "Xref2": "",
 "Xref3": "",
 "Zzcod": "001",
 "Tipaf": "MON",
 "Zcemnue": "0006"}
```

**En SAP:** 

* TRANSACCION: ZFI_ENVIO_ND

* PROGRAMA: ZFI_ENVIO_MAIL_DEB 
(Transaccion de Impresión call transaction: ZNOPN en programa de envio que llama al smartform)

* FORMULARIO:  ZSF_DEB_CRED2 (Smartforms) 
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

-Opción de Ejecución manual 
La opción automática controlara la duplicidad del envío, no siendo así para la ejecución manual.

EL programa realiza un control del usuario que envio el mail, si es LTAMARGO impide que se envie 2 veces. Si es otro usuario, es sin limite.


Configuración de Mail: 

    Remitentes: 
    1. noreply-hospitales@uocra.org y 
    2. noreply-cuentasapagar@uocra.org

    Título: xxxxxxxxx

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

Si es ND, tiene que tener adjunto de hoja resumen de Presmed. El adjunto lo busca por expediente en el texto cabecera (BKPF BKTXT) del BKPF BELNR, ejercicio y sociedad, en la carpeta \\uocrafs\ProdPresmed\EXP_NROEXPEDIENTE.pdf (EXP_0000332445.pdf)
Si lo encuentra, envía el mail y sino cancela el envio y avisa en el log.


Tabla de control de envios realizados: 
ZCONTROL_MAIL

Transaccion de reporte envios: ZFI_ENVIO_ND_L

