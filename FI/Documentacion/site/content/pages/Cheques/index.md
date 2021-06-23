# Cheques: Generacion, Visualizacion, liberacion

## Descripcion breve del proceso:
Los cheques siempre se emiten como emitidos no entregrados y luego pasan a ser liberados a la espera de la conciliacion bancaria.

***
***

## Proceso paso a paso:

1.Emision de cheques: 

A) La emision de cheque puede ser manual:

 a partir de un documento de pago previamente contabilizado se emite por la transaccion FCH5 o F-58. 

B) La emision de cheque puede ser automatica:

transaccion F110 que genera el docuemnto de pago y el cheque en forma automatica.

Asiento contable: (Pago)  Proveedor "CT" 25 a Banco cheque emitido no entregado "CT" 50.


2. Liberacion:

explicar transacciones paso a paso.
Transacion ZCHQ_N Para liberar.
ZLIB Liberar Cheques Manualmente.
Poner asiento contable

3. Visualizacion:

Poner todas las transacciones para visualisar 1 2 y 3 y 4

### Casos / Preguntas frecuentes
Caso 1: 

El cheque posee fecha de cobro pero no tiene el documento de liberacion asignado (KY). usar transaccion ZLIB para liberar cheque manualmente.

Caso 2: 

En caso de que el cheque no tenga ni fecha ni (KY) se libera a travez de la transaccion ZCHQ_N ya que aun no se a liberado.

***
***
## Documentacion Técnica

**Liberacion:**

Cargar documentos DOC tecnicos 1 y 2