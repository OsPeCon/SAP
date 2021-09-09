---
title: Validacion de Expediente FI.
date: Last Modified
permalink: /Expediente_Validacion/
eleventyNavigation:
    key: expediente
    order: 20
    title: Validacion de Expediente FI.
---

## Tecnología de la Información
### Documento ConceptualTecnico

**Título:** Validacion Expediente Ape via WS

**Área de aplicación:**	FI

**Fecha:** 31/05/2021

**Dirigida a:**	

**CC.**	

**Confeccionada por:** Leonardo Ruseff

***

# Objetivo
Insertar un WS en una transaccion standard de SAP 
Validar el ingreso de un Numero de expediente contra el Centro Autorizador

# Especificacion
Enhancement Implementation:  ZENH_REFERENCIA (SE20)

Programa: SAPMF05A

INCLUDE: MF05AI10_PAI_ANFANG 

Funcion: ZWS_CONSULTA_EXPEDIENTE 

Destination: ZCONSULTA_EXPEDIENTE

# Programa
![Mi Imagen](../content/images/Expediente_Validacion/standard_01.png)
![Prueba](../content/images/Expediente_Validacion/Standard_02.png)