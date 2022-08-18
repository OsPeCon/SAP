---
title: Cheques.
date: Last Modified
permalink: /Cheques/
eleventyNavigation:
    key: cheques
    order: 10
    title: Cheques.
---
# Cheques: Generación, Visualización, liberación

## Descripción breve del proceso:

Los cheques siempre se emiten como emitidos no entregrados y luego pasan a ser liberados a la espera de la conciliacion bancaria.

---

---

## Proceso paso a paso:

1. Emisión de cheques:

* La emisión de cheque puede ser manual:

A partir de un documento de pago previamente contabilizado, se emite por la transaccion F-58.

FCH5 A través de esta transacción se puede asignar el cheque.

* La emisión de cheque puede ser automática:

Transaccion F110 que genera el documento de pago y el cheque en forma automatica.

Asiento contable: (Pago)  Proveedor "CT" 25 a Banco cheque emitido no entregado "CT" 50.

2. Liberación:

Transacción ZCHQ_N :

La cual permite la Liberación de una selección múltiple de cheques ingresmndo la fecha de liberación.

Transacción ZLIB:

Libera en forma manual cheques, los cuales no pueden liberarse en forma automática a causa de un error.

Asiento contable: (Liberacion) cheque liberado "CT" 50 a Banco cheque emitido no entregado "CT" 40.

3. Visualización:

* TRX.FCH1: visualiza cheques.
* TRX.FB03: visualiza documentos.
* TRX.ZQCH_2: Permite emitir un listado de cheque.

### Casos / Preguntas frecuentes

Caso 1:

El cheque posee fecha de cobro pero no tiene el documento de liberacion asignado (KY). Usar transacción ZLIB para liberar cheque manualmente.

Caso 2:

En caso de que el cheque no tenga ni fecha ni (KY) se libera a travez de la transaccion ZCHQ_N ya que aun no se ha liberado.

---

---
