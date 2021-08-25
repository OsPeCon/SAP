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

## Documentación Técnica

**Liberación:**
Nombre del Programa: ZRAFI01
Transacción: ZCHQ_N

1. Especificación
2. Al ingresar en la transacción ZCHQ_N – Actualización de Cheques entregados a proveedores, el sistema no permite que diferentes usuarios puedan ingresar en distintas sociedades al mismo tiempo para ejecutar el programa ZRAFI01 para la liberación de los cheques.

Por eso es necesario que el campo de selección sociedad permita ingresar UN SOLO VALOR. Es decir no permitir “desde – hasta” ni “selección múltiple”.
Además que sea obligatorio.

Campo sociedad:
Tabla: PAYR
Nombre de campo: ZBUKR
Elemento de dato: DZBUKR
Campo dynpro: SOCIEDAD-LOW

Cabe aclarar que se trata de un usuario por cada sociedad y en el caso de que un usuario este utilizando la transacción y otro lo hace al mismo tiempo para la misma sociedad, se deberá emitir el siguiente mensaje de ERROR: “El usuario & ya esta liberando en la sociedad &”.

En consecuencia el actual mensaje “057 - El acreedor &1 está siendo tratado por el usuario &2” actualmente utilizado solamente por el programa ZRAFI01, deberá ser renombrado por el mencionado en el punto anterior.

MENSAJE DE ERROR: 057 - El usuario & ya esta liberando en la sociedad &.

.....

Nombre del Programa: ZRAFI01
Tabla: PAYR
Transacción: ZCHQ_N

1. Objetivo
   Permitir la Liberación de una selección múltiple de cheques ingresando una fecha de liberación.
2. Especificación

Mediante la transacción ZCHQ_N – Actualización de Cheques entregados a proveedores, se debe ingresar manualmente la fecha a cada cheque, por tal motivo se requiere la incorporación de un nuevo campo “Fecha” (opcional) donde se pueda ingresar solo una (dd/mm/aaaa), de acuerdo a los cheques cargados mediante la selección múltiple en el campo Número de Cheque.
