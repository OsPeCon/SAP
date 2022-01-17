---
title: Expediente Validación.
date: Last Modified
permalink: /Expediente_Validacion/
eleventyNavigation:
    key: expediente
    order: 50
    title: Expediente Validación
---



# Validacion Expediente Ape via WS


Programa (Web Service)  que valida  los nros. de expedientes cargados en una OC.

Cómo funciona? SAP toma el expediente cargado en el campo “nro. Necesidad” al cargar una OC en la ME21 o modificarla en la ME22; y va a buscarlo al Centro Autorizador para validarlo
 
Estos son los mensajes que emitirá dicho control (por favor leer el mensaje para  asegurarse de que el mismo es correcto y dar “enter”)


* Expediente de materiales existe aprobado

* Expediente de materiales existe rechazado
* Expediente de materiales existe pendiente

* Expediente existe pero no corresponde a materiales
* Expediente inexistente

*  Error en la comunicación.
  
* Debe ingresar expediente (Este mensaje aparece en rojo por mayor control, pero NO ES UN ERROR, sino que es una advertencia para que el usuario verifique realmente si no corresponde ingresar un nro de expediente).

***

# Objetivo
Insertar un WS en una transaccion standard de SAP 
Validar el ingreso de un Numero de expediente contra el Centro Autorizador

# Especificacion
Enhancement Implementation:  ZMM_VALIDA_EXPEDIENTE

Programa: SAPMM06E	

INCLUDE: MM06EF0F_FCODE_LOOP

Funcion: ZWS_CONSULTA_EXPEDIENTE_OC

Destination: 'ZCONSULTA_EXPEDIENTE_OC'

Formato de la devolución del método http://localhost/DigitalizacionExpedientes/odata/Traer(pIdExpediente=5476791), al que le agregamos el Estado del expediente.

Valores Posibles
N= Rechazado
P=Pendiente
S=Aprobado

 "value": [
        {
            "TipoPed": 3,
            "Seccional": "0001",
            "EventoId": 39,
            "ObraSocial": "MON",
            "Cuil": 20119989575,
            "HisCli": 11998957,
            "Nombre": "ARATTA NESTOR ADOLFO",
            "Patologia": 0,
            "DenoPatologia": "SIN PATOLOGIA SUR",
            "Sur": 0,
            "TramiteId": 0,
            "DenoTipoPed": "PRACTICAS MEDICAS             ",
            "DenoSeccional": "NODO CABALLITO                ",
            "DenoEvento": "RECHAZO MEDICO FORMAL                             ",
            "Programado": "",
            "Estado": "N"
        }
    ]


