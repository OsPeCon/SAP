---
title: Conciliacion Bancaria.
date: Last Modified
permalink: /Conciliacion_Bancaria/
eleventyNavigation:
    key: conciliacion
    order: 30
    title: Conciliacion Bancaria.
---
# Conciliacion Bancaria

## Descripcion breve del proceso:

La conciliacion bancaria se realiza todos los dias mediante la bajada del archivo de estado bancario de datanet y luego el procesamiento en SAP del mismo.

Este proceso genera la compensacion de movimientos bancarios enviandolos a "cuenta corriente", por ejemplo transferencias o cheques liberados, y ademas contabiliza los gastos.

---

## Proceso paso a paso:

**DATANET**
Se bajan los movimientos del banco mediante un programa externo (usuario APAGANO) y se  genera un archivo txt llamado DNCTAS en el disco rígido del usuario. El usuario debe borrar este txt pues de lo contrariose van generando distintos txt con nros. Correlativos.

**EN SAP:**

1) Se ejecuta en SAP el Programa **ZCONCILIA** (Trx. ZDAT),  el cual importa el archivo TXT  generado en el paso anterior.

* Fecha de movimiento:  se graba en la fecha de documento
* Fecha Valor: se graba en la fecha valor
* Fecha de proceso: no se graba en el documento. La fecha de proceso es siempre un dia antes de la actual.

Esta transaccion contabiliza las compensaciones de los bancos y los movimientos de gastos.

Para que estas contabilizaciones sean posibles, deben estar debidamente configuradas las siguientes tablas y transacciones:

Tabla ZCONCILIA: actualizable por el usuario mediante transaccion "ZCONCILIA". Indica los asientos contables a realizar y la Regla de contabilización, según cuenta
bancaria y operación externa.

Tabla ZCODEX: contiene los códigos externos Datanet con sus características (debe/ haber, tipo operación, etc.) . Actualizable por Tecnologia de la Informacion mediante la transaccion ZCODEX.

Tabla ZCTABANK:  Contiene los datos de Cuentas bancarias en bancos propios. Si hay una “X” en el campo Ignora, esto hace que la 		cuenta no sea procesada. Actualizable por Tecnologia de la Informacion mediante la transaccionSistemas con la Trx. SM30

Si se realiza cualquier cambio en ZCODEX o ZCUENTABANK, el usuario deberá actualizar ZCONCILIA.

El Programa ZCONCILIA Guarda en \uocrafs\ datanet\ backup, una copia del archivo TXT, tal cual lo envió el banco. Este archivo no se pisa sino que se guardan todos y se zipea anualmente para guardar la información compactada.

Ademas, se guarda un log de las contabilizaciones y errores del proceso.

Trx. ZFI_DATANET: Reporte que permite visualizar la tabla ZDATANET001.

### Casos / Preguntas frecuentes

No existen casos a la fecha

---

---
