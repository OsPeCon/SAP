---
title: Vista expediente / orden de compra.
date: Last Modified
permalink: /Vista_Expediente_OC/
eleventyNavigation:
    key: vistaexoc
    order: 50
    title: Vista expediente / orden de compra.
---

# Tecnología de la Información
## Documento Tecnico

**Título:** Vista para consumir Expediente + OC + Factura + Pago

**Área de aplicación:**	FI

**Fecha:** 01/06/2021

**Dirigida a:**	

**CC.**	

**Confeccionada por:** Leonardo Ruseff

***

# Objetivo
Armar una vista que contenga las OC y Expediente de materiales quierurjico prueba nico lucas 3

# Especificacion
Prorama SAP: ZDATA_EXPEDIENTE_OC

Vista generada: ZDEXPEDIENTE

Vista en SQL UNET20.Dpx.dbo.SAP_Expediente_OC con los campos solicitados

Definicion de la vista
SELECT        *
FROM            OPENQUERY(HANASAP, 'Select * From SAPABAP1.ZDEXPEDIENTE a ') AS derivedtbl_1


# Notas
La ejecución del programa que la alimenta está programada en forma diaria a las 23:59 hs.