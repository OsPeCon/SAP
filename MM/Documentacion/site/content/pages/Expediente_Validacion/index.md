# Tecnología de la Información
## Documento ConceptualTecnico

**Título:** Validacion Expediente Ape via WS

**Área de aplicación:**	MM

**Fecha:** 05/06/2021

**Dirigida a:**	

**CC.**	

**Confeccionada por:** Leonardo Ruseff

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



