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
* Motivo del canje (hasta 18 caracteres)
* Tipo ejecucion BI: Modo A permite visualizar las pantallas, en modo N invisible y E solo errores. 

### Casos / Preguntas frecuentes

No existen casos a la fecha

---

---

## Documentacion Técnica

**Para Canje Automatico:**

Transacción: ZFI_CANJE
Programa: ZFI_CANJE_AUT

Pantalla de Selección:

* Sociedad:
* Doc. Pago rechazado:  validar que se trate de clase de documento de pago KZ o ZP
* Motivo del canje (18 caracteres)
* Tipo ejecucion BI: Modo A permite visualizar las pantallas, en modo N invisible y E solo errores.

Tomar del documento de pago indicado:

- Proveedor (KOART = K)
- Cuenta contable (para posición BSEG-KOART = S y BSEG-QSSKZ  = vacío)

Call Transaction a Transaction FB01

Clase de documento a generar KS

Posición 1:
Clave contabilización 34 / Proveedor / Clave Ref1:  doc pago rechazado

Posición 2:
Clave contabilización 50 /
Cuenta de mayor a determinar por tabla T012K (CON EXCEPCION *)

Llamada a tabla T012K (para determinar la contrapartida del asiento del canje)

    -Si el asiento tiene cuenta T012K-HKONT con ID 00002, entonces se 							usa T012K-HKONT de ID 00003

    -Si el asiento tiene cuenta T012K-HKONT con ID 00005, entonces se usa T012K-HKONT de ID 00006

    EXCEPCION (*): Si T012K-HKONT=1101021414 o 1101021394 entonces se usa T012K-HKONT de ID 00012

VALIDACIONES

SOLO CANJEAR  en el caso en que ya se encuentre la OP liberada o compensada y SIN EXTRACTO BANCARIO (1)

NO CANJEAR cuando:

- No esta liberado (2)
- Esta liberado pero tiene conciliacion bancaria (3)
- La OP esta anulada, es decir BKPF = STBLG es distinto de vacio. Mensaje de error: “La OP se encuentra anulada con doc BKPF = STBLG

Especicacion de la validacion para hacer el canje:

Ingresar a BSEG con SOC y BELNR = doc de pago y clase de cuenta KOART = “S”.

Si para ese registro el campo BSEG-AUGBL es distinto de vacio, hacer un segundo ingreso a la BSEG con
Soc, BELNR = valor encontrado en BSEG-AUGBL y BSEG-BSCHL = 50. Si para ese registro BSEG-AUGBL es vacio, ENTONCES LIBERAR. (1)

```
    -Si ese campo es distinto de vacio (3) NO LIBERAR y arrojar el siguiente error: “la OP no puede canjearse ya que se encuentra conciliada con Documento XXXXXXXX” siendo xxxxx el valor que se encuentra en BSEG-AUGBL.
```

-Si BSEG-AUGBL es vacio,  (2) entonces arrojar mensaje de error: “la OP no puede canjearse ya que aun no se encuentra liberada.


Validacion de que el canje no este realizado

Validacion de Sociedad

Validacion de O.P. anulada

Validacion de O.P. ya canjeada

**Para canje manual no existe documentacion tecnica**
