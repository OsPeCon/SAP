# Preliminares Integración y No Integración

## Descripción breve del proceso:
Generación automática de los documentos preliminares correspondientes a las facturas Integración y no Integración (ex sur)

***
***

## Proceso paso a paso:
Los documentos se cargan en una app externa, el cual a través de JSON ingresan a SAP (Programa zws_preliminares para cargar y  programa zws_borraprel para borrar) en forma de documento Preliminar. 
### Casos / Preguntas frecuentes

Los errores en la app externa solo muestran un cartel de 'null' (en proceso de identificacion de error).
***
***
## Documentación Técnica

***INTEGRACION:***

**Llamada JSON:**

URL: http://saphanaprod:8000/sap/opu/odata/sap/ZAPI_PRELIMINARES_SRV/PreliminaresSet/

AUTORIZATION: 
Basic Auth: Usuario y contraseña SAP. (Solo Para Método GET)

HEADERS:
x-csrf-token = Generar token (Con Metodo GET) 

BODY:
RAW
formato (JSON): 
```json
{"Bukrs": "0100",
 "Zzidexterna": "600",
 "Blart": "KR",
 "Bldat": "2021-03-28T00:00:00",
 "Monat": "02",  
 "Gjahr": "2021",
 "Xblnr": "00001A12345678",
 "Bktxt": "",
 "Brnch": "0030",
 "Ltext": "979",
 "Zltext": "caf1d9af-7388-4fc2-9bc3-bef3c75f9673",
 "Zzextension": "jpeg", 
 "Newko": "1060",
 "Wrbtr": "10.23",
 "Zuonr": "00001A12345678",
 "Sgtxt": "",
 "Xref1": "",
 "Xref2": "",
 "Xref3": ""}
```

***NO INTEGRACION:***

**Llamada JSON:**

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
 "Ltext": "1023",
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

***BORRADO:***

**Llamada JSON:**

URL: http://saphanaprod:8000/sap/opu/odata/sap/ZAPI_PRELIMINARES_SRV/BorrarPrelSet/

AUTORIZATION: 
Basic Auth: Usuario y contraseña SAP. (Solo Para Metodo GET)

HEADERS:
x-csrf-token = Generar token (Con Metodo GET) 

BODY:
RAW
formato (JSON): 
```json
{"Bukrs": "0100",
 "Belnr": "120006580"}
```

**En SAP:** 

* TRANSACCION: -

* PROGRAMA: ZWS_PRELIMINARES 
(Recibe los JSON tanto para integracion/no integracion utilizando la tabla zws_preliminar)

* PROGRAMA: ZWS_BORRARPREL 
(Recibe los JSON utilizando la tabla zws_borrarprel)

-Ejecución Online.

-Opción de Ejecución Manual 
Ingresansando los datos del JSON, permite cargar un preliminar.

 * MODULO DE FUNCIONES:
    * Z_BAPI_PREL (Integración)
    * Z_BAPI_PREL_2POS (No Integración)
    * Z_BAPI_BORR_PREL (Borrado)

Tabla de control de Preliminares: 
ZWS_PREL_LOG

Tabla de control de Borrado de Preliminares: 
ZWS_BORR_LOG