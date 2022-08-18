---
title: Mail Nota de Debito / Credito.
date: Last Modified
permalink: /Mail_Nota_Debito_Credito/
eleventyNavigation:
    key: mailnotas
    order: 30
    title: Mail Nota de Debito / Credito.
---
# Envío Automático de Mail de NC y ND

## Descripcion breve del proceso:

Envío automático por mail a los prestadores, del detalle de Notas de Crédito y Notas de Débito propias tanto médicas como administrativas que se generan en el proceso de SAP/ PRESMED
Los adjuntos al mail serán los formularios de ND y NC y la hoja de detalle de débitos generada por Presmed.

---

---

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

---

---

