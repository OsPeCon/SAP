---
title: PSTI.
date: Last Modified
permalink: /PSTI/
eleventyNavigation:
    key: psti
    order: 40
    title: PSTI.
---
## **PSTI: Facturacion Adherentes**

**Descripción breve del proceso:**

Emision , Impresion y envio de facturacion.

## Proceso paso a paso:

1. Listado de Bajas: Trx. ZFI_BAJAS. Se informan los adherentes con 2 o más facturas vencidas. En el caso que sean 2, solo informa en el listado y en el caso que sean 3 además de informar realiza el bloqueo de dicho adherente.

![img](../content/images/PSTI/psti1.png)

2. ZFI_ADHERENTE_FACT **– FACTURACION AUTOMATICA:                                                        **Una vez confirmado los clientes a facturar con menos de 3 meses de deuda, debemos ejecutar la trx.zfi_adherente_fact.!

![img](../content/images/PSTI/psti2.png)

3. Importe de Plan: Permite ingresar el valor a facturar dependiendo del tipo de plan que posee el adherente.               

![img](../content/images/PSTI/psti3.png)

4. Numero Documento Cliente permite ingresar los adherentes a facturar. Numero de Cuenta Anterior: Es el numero utilizado en el sistema anterio de facturacion ""NO SAP"".  Fecha de Facturacion: ingresar fecha de facturacion. Condicion de Pago: Z018 ""Fija"". Tipo de Ejecucion: Visualizacion, permite visualizar importe y datos del adherente a facturar. Ejecucion, se realiza la facturacion.

5. Factura Manual: Permite Facturar en forma manual a un adherente. En
   caso de encontrarse un error en la facturación Automática, debemos facturar en
   forma manual.

6. **J1AMONITOR (ENVIO DE FACTURAS A AFIP PARA INGRESAR CAE A LA MISMA):** Permite enviar la facturacion generada a AFIP. 

![img](../content/images/PSTI/psti4.png)

**Sociedad:** 0100

**Numero de sucursal:**
0007

7. **ZFI_ADH_MAIL**

**(ENVIO DE MAIL E IMPRESIÓN DE FACTURA)**

La trx. zfi_adh_mail permite el envió
de mail a los adherentes que poseen el mismo cargado o bien imprimir la factura
a los que no lo poseen.



## **PAGO FACIL**


| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).		
					
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Registro de Detalle.(Información detallada de cada transacción)		
					
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Registro de Detalle. (Código de Barras).			
					
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Registro Trailer del Batch.(Información total del Batch, uno por batch).		
					
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).		
					
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
|---------------------------------------------------------------------------------|---------|-----------|------------------------------------------------------------------|-------------|----------------------------------------|
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '1'.                                    | Siempre     | 1                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Origin Name                                                                     | Alf.    | 25        | Valor 'SEPSA'                                                    | Siempre     | PAGO FACIL - Efectivo                  |
| Client Number                                                                   | Num     | 9         | Número de la empresa de servicio.                                | Siempre     | 012150001                              |
| Client Name                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Header del Batch.( Primer Reg. del batch, sólo uno por batch).         |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '5'.                                    | Siempre     | 5                                      |
| Create Date                                                                     | Num     | 8         | Fecha de Creación (YYYYMMDD)                                     | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Description                                                                     | Alf.    | 35        | Nombre de la empresa de servicio.                                | Siempre     | OBRA SOC. PERSONAL DE LA CONSTRUCCI    |
| Filler                                                                          | Alf.    | 39        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle.(Información detallada de cada transacción)                 |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro. Valor '6'.                                   | Siempre     | 6                                      |
| Record Sequence                                                                 | Num     | 5         | Número de secuencia de transacción dentro del Batch.             | Siempre     | 00001                                  |
| Transaction Code                                                                | Num     | 2         | Código de Transacción.                                           | Siempre     | 10                                     |
| Work Date                                                                       | Num     | 8         | Fecha de Proceso. (YYYYMMDD)                                     | Siempre     | 20190318                               |
| Transfer Date                                                                   | Num     | 8         | Fecha de creación. (YYYYMMDD) Es también fecha de transferencia  |
| del archivo/fondos (sólo dentro de las 24hs.)                                   | Siempre | 20190319  |
| Account Number                                                                  | Alf     | 21        | Número de Cuenta del cliente.                                    | Siempre     | 2700038671                             |
| Payment Code                                                                    | Num     | 1         | Código de Transacción.                                           | Siempre     | 0                                      |
| Amount                                                                          | Num     | 10        | Importe cobrado.                                                 | Siempre     | 0000058000                             |
| Terminal Id.                                                                    | Alf     | 6         | Terminal en la cual se efectuó la transacción.                   | Siempre     | A11616                                 |
| Payment Date                                                                    | Num     | 8         | Fecha en que se efectuó la Transacción. (YYYYMMDD).              | Siempre     | 20190318                               |
| Payment Time                                                                    | Num     | 4         | Hora de la Transacción.                                          | Siempre     | 1537                                   |
| Term Seq Number                                                                 | Num     | 4         | Numéro de secuencia de transacción en esa terminal.              | Siempre     | 0023                                   |
| Filler                                                                          | Alf.    | 11        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro de Detalle. (Código de Barras).                                        |         |           |                                                                  |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '7'.                                    | Siempre     | 7                                      |
| Bar Code                                                                        | Num     | 60        | Código de Barras de la Transacción.                              | Siempre     | 1210005800019075270003867116           |
| Filler                                                                          | Alf     | 28        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Batch.(Información total del Batch, uno por batch).        |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '8'.                                    | Siempre     | 8                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Batch Number                                                                    | Num     | 6         | Número del Batch                                                 | Siempre     | 000001                                 |
| Batch Payment Count                                                             | Num     | 7         | Cantidad de transacciones del Batch.                             | Siempre     | 0000006                                |
| Batch Payment Amount                                                            | Num     | 12        | Importe total cobrado del Batch.                                 | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| Batch Count                                                                     | Num     | 5         | Cantidad de transacciones del batch.                             | Siempre     | 00006                                  |
| Filler                                                                          | Alf     | 12        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Registro Trailer del Archivo.(Información total del Archivo, uno por archivo).  |         |           |
|                                                                                 |         |           |                                                                  |             |                                        |
| CAMPO                                                                           | TIPO    | LONG MAX. | DESCRIPCION                                                      | OBLIGATORIO | EN ARCHIVO                             |
| Record Code                                                                     | Num     | 1         | Código de Registro.Valor '9'.                                    | Siempre     | 9                                      |
| Create Date                                                                     | Num     | 8         | Fecha de creación del archivo (YYYYMMDD).                        | Siempre     | 20190319                               |
| Total Batches                                                                   | Num     | 6         |                                                                  | Siempre     | 000001                                 |
| File Payment Count                                                              | Num     | 7         | Cantidad total de transacciones del archivo.                     | Siempre     | 0000006                                |
| File Payment Amount                                                             | Num     | 12        | Importe total cobrado del archivo.                               | Siempre     | 000000434000                           |
| Filler                                                                          | Alf     | 38        |                                                                  | Siempre     | 00000000000000000000000000000000000000 |
| File Count                                                                      | Num     | 7         | Cantidad total de transaciones del archivo.                      | Siempre     | 0000006                                |
| Filler                                                                          | Alf     | 10        |                                                                  | Siempre     | ESPACIOS EN BLANCO                     |
|                                                                                 |         |           |                                                                  |             |                                        |
| Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros. |
					
Nota: cada batch tiene un máximo de 500 transacciones, es decir 1000 registros.		



## Documentación Técnica
