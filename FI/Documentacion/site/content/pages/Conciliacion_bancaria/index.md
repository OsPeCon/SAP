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


### Casos / Preguntas frecuentes

No existen casos a la fecha

---

---

## Documentacion Técnica

**Para Canje Automatico:**

Transacción: ZDAT

Programa: ZCONCILIA

Se bajan los movimientos del banco mediante un programa externo (usuario APAGANO) y se  genera un archivo txt llamado DNCTAS en el
disco rígido del usuario. El usuario debe borrar este txt pues de lo contrario se van generando distintos txt con nros. Correlativos.

Se ejecuta en SAP el Programa ZCONCILIA que realiza los siguientes
pasos:

Importa el archivo TXT  generado en el paso anterior.

Formato de Archivo txt:

| **Campo**         | **Longitud** |
| ----------------------- | ------------------ |
| Tipo de registro        | 1                  |
| Código de Banco        | 3                  |
| Nº Cta. Corto          | 2                  |
| Fecha Movimiento        | 8                  |
| Fecha Valor             | 8                  |
| Deb. Cred.              | 1                  |
| Importe Movimiento      | 17                 |
| (2)                     |                    |
| Número de cheque o Nro |                    |
| Lote Ebanking           | 12                 |
| Código de Operación   | 3                  |
| Fecha de Proceso        | 8                  |
| blanco                  |                    |
| Sin Contenido           | 3                  |
| Desc.Movimiento         | 25                 |
| Suc. Origen             | 5                  |
| Código Depositante     | 8                  |
| NºCta.Bancaria UOCRA   |                    |
| 52568/ Ospecon 58726    | 17                 |

Guarda en \uocrafs\ datanet\ backup, una copia del archivo TXT, tal cual lo envió el banco. Este archivo no se pisa sino que se guardan todos y se zipea anualmente para guardar la información compactada.

Guarda en la tabla  “ZDATANET001” todos los movimiento tipo “M” y tipo “V”. Estos movimientos se depuran
anualmente en forma manual, por parte de Tecnología de la Información.

La  tabla ZDATANET001, que es un reflejo del txt de datanet, contiene 3 Fechas:

    - [ ] Fecha movimiento (FECHA_MOV)

    - [ ] Fecha Valor           (FECHA_VALOR)

    - [ ] Fecha Proceso       (FECHA_PROCESO)

Cuando SAP realiza el asiento, el tratamiento de dichas fechas, es el siguiente:

    - [ ] Fecha de documento (BLDAT): toma la FECHA_VALOR.

    - [ ] Fecha de contabilización (BUDAT): toma la FECHA_VALOR.

    - [ ] Periodo de Liquidación (ABPER): toma la FECHA_MOV, y la transforma en año/ mes.

    - [ ] Fecha valor (VALUT): toma la FECHA_VALOR

    - [ ] La FECHA_PROCESO no se graba en ningún campo.

Recorre la tabla del punto anterior y mediante la consulta a la tabla “ZCONCILIA,” realiza los asientos correctos.

Las transacciones que ejecuta el programa son F-51 o F-02 según la tabla “ZREGLACONTAB”

Guarda en \uocrafs\ datanet\ log una copia del log de errores generado.

Mediante la Transacción ZLOG se visualiza el LOG generado.

**Detalle técnico de las TABLAS creadas:**

ZCONCILIA:
Actualizable por usuario.
Indica los Asientos contables a realizar y la Regla de contabilización, según cuenta bancaria y operación externa.

ZREGLACONTAB:
Actualizable por usuario.
Indica la transacción funcional a ejecutar según la Regla de contabilización.

ZCODEX:
Actualizable por usuario con la Trx. ZCODEX
Códigos externos Datanet con sus características (debe/ haber, tipo operación, etc).

ZCTABANK:
Actualizable por Sistemas con la Trx. SM30
Contiene los datos de Cuentas bancarias en bancos propios. Si hay una “X” en el campo Ignora, esto hace que la cuenta no sea procesada.

ZTIPOPEXT:
Tipo de operación externa.

ZDATANET001:
Log de procesamiento Datanet.

ZDATANET002:
Tabla numeradora de procesos de datanet que proporciona el ID para el control de procesamiento de Zdatanet001, pues le asigna el nombre al archivo (AAAMMDD).

NOTA: Si se realiza cualquier cambio en ZCODEX o ZCUENTABANK, el usuario deberá actualizar ZCONCILIA.

**Modificacion 15/11/2021**

Antes de procesar hacer llamada a la tabla ZDATANET001 y chequear fecha de proceso.

Si existe fecha de proceso del dia anterior, no procesar el archivo, sino dar una advertencia: "ya se ha procesado fecha XX.XX.XXX", sin contemplar sabados, domingos ni feriados.

Crear reporte a tabla ZDATANET001 con visualizacion de fecha de proceso.

La fecha de Proceso de
Datanet es siempre un día antes de la actual.
