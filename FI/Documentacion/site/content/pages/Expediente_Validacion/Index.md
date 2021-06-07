---
title: Validacion de Expediente.
date: Last Modified
permalink: /Expediente_Validacion/
eleventyNavigation:
    key: validacion
    order: 2
    title: Validacion de Expediente.
---

<!-- @format -->


# Tecnología de la Información
## Documento ConceptualTecnico

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
![Prueba](/Expediente_Validacion/images/Standard_01.png)
![Prueba](/Expediente_Validacion/images/Standard_02.png)