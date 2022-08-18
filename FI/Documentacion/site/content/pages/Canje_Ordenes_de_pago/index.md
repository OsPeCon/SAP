---
title: Canje de Ordenes de Pago.
date: Last Modified
permalink: /Canje_Ordenes_de_pago/
eleventyNavigation:
    key: canje
    order: 30
    title: Canje de Ordenes de Pago.
---
# Canje de Ordenes de Pago

## Descripcion breve del proceso:

Las ordenes de pago que se encuentren liberadas, ya no podran ser anuladas; con lo cual se debera hacer un "Canje".
Esto corre tanto para las OP de cheques como para las de transferencias de todos los bancos.
El canje implica generar una nueva deuda con el proveedor para generar un pago y a la vez bajar el saldo de la cuenta de cheque liberado o transferencia liberada.

---

## Proceso paso a paso:

El canje de OP puede realizarse de dos formas: Manual o Automatica

CANJE MANUAL:

**TRANSACCION: FB01**
Se debera generar una clase de documento "KS".
Documento contable con clave de contabilizaion 34 para el acreedor y 40 para la cuenta de cheque liberado o bien transferencia liberada segun corresponda.
El importe debera ser el contabilziado en la OP original en la cuenta contable "cheque liberado o transferencia liberada.

Datos importantes en la posicion del acreedor:

* Borrar retenciones las retenciones ya que las mismas fueron contabilizadas en la OP original
* Otros datos - Clave de Referencia 1: Ingresar el nro. de OP que se esta canjeando, ya que sino el sistemas arrojara mensaje de error. Este dato sirve a efectos de reportes posteriores.
* Si OP original tiene datos de receptor de pago, se deberan completar.

Una vez que el documento KS esta contabilizado, el mismo seguira el curso de pago normal.

CANJE AUTOMATICO:
Por default, el modo de ejecucion de la transaccion sera "N" automatico, este modo no da la posibilidad de modificar datos de receptor de pago. En caso de que haya que modificar estos datos en pantalla, se debera seleccionar MODO VISIBLE "A".

**TRANSACCION: ZFI_CANJE**

Pantalla de Selección:

* Sociedad:
* Doc. Pago rechazado:  validar que se trate de clase de documento de pago KZ o ZP
* Ejercicio:
* Motivo del canje (hasta 18 caracteres)
* Tipo ejecucion BI: Modo A permite visualizar las pantallas, en modo N invisible y E solo errores.

**VALIDACIONES que realiza el programa:**

* Solo se canjea en el caso en que ya se encuentre la OP
liberada o compensada.

* No se canjea cuando la OP no está liberada.

* No se canjea cuando la OP esta liberada pero tiene
conciliacion bancaria. Esta validación solo se realiza para Banco Hipotecario,
siendo para ospecon 93000 y para uocra 95000.

* No se canjea cuando la OP esta anulada.

* No se canjea cuando el canje ya fue realizado (es decir
exite un KS para esa OP)

* Adicionalmente, el programa valida la sociedad y el
ejercicio de la OP que se va a canjear.

### Casos / Preguntas frecuentes

No existen casos a la fecha

---

