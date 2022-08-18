---
title: Preliminares Integración y No Integración.
date: Last Modified
permalink: /Ws_Preliminares_Integracion_no_integracion/
eleventyNavigation:
    key: preliminares
    order: 60
    title: Preliminares Integración y No Integración.
---

# Preliminares Integración y No Integración

## Descripción breve del proceso:
Generación automática de los documentos preliminares correspondientes a las facturas Integración y no Integración (ex sur)

***
***

## Proceso paso a paso:
Es un proceso transparente para el usuario, al aprobar en la web de prestadores, genera la registracion del documento preliminar.
A través de JSON ingresan a SAP (Programa zws_preliminares para cargar y  programa zws_borraprel para borrar) en forma de documento Preliminar. 
### Casos / Preguntas frecuentes

Los errores en la app externa solo muestran un cartel de 'null' (en proceso de identificacion de error).

Log en SAP:
*   No Procesado - Error Centro Costo no encontrado: Verificar en la tabla zrelceco si exiten los datos.
* No Procesado - El acreedor XXXXX 0100 no existe: El prestador no tiene cargado todos sus datos maestros.

***
***
