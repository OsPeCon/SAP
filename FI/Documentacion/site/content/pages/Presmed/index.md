---
title: Pagos por Transferencia.
date: Last Modified
permalink: /Pagos_por_Transferencia/
eleventyNavigation:
    key: pagos por transferencia
    order: 50
    title: Pagos por Transferencia.
---
## **Pagos por Transferencia**

**Descripción breve del proceso:**

Pagos via transferencia Banco La Pampa, Banco Nacion y Banco Hipotecario. 

## Proceso paso a paso:

1. 

ENVIO DE MAIL:
Tanto para UOCRA como para OSPECON y para todos los bancos con los que realizamos transferencias (BNA, BLP y BHI), el envio de  MAIL es POSDATADO.


Funciona asi:

EN la transacción de liberación, el mail se envía al proveedor en la fecha indicada como “fecha de transferencia” en el momento en que generaron el lote archivo para ser enviado al banco.
•	Si esa fecha es la del día, el mail se dispara inmediatamente.
•	Si la fecha es posterior a la del día, el mail se disparara en dicha fecha y a las 10 a.m. (es decir hoy hago un lote de transferencia con fecha 19.09.2021… cuando voy a liberar el lote,  el mail no se envía ya que el mismo será enviado el 19.09 a las 10 hs)

En el reporte ZCBU_2, las marcas de mail son las mismas ya que el mail sabremos que fue enviado el dia de transferencia.




## **Casos / Preguntas frecuentes**

Caso 1:

Caso 2:

---

## Documentación Técnica

* ENVIO DE MAIL: Para el envio de mail en el Banco BLP/BNA, se agrego una validacion la cual deja en cola de espera en la sost en caso que la fecha de pago/liberacion sea superior a la fecha del dia que se ejecuta:

      IF sy-datum < p_output-fecha_transfer.

        lv_diff = p_output-fecha_transfer - sy-datum.
        lv_sec = lv_diff * 86400.

DATA: fechaenv(14) TYPE c.
CONCATENATE p_output-fecha_transfer '130000' INTO fechaenv.
lv_timestamp = fechaenv.

"        GET TIME STAMP FIELD lv_timestamp.               
"        lv_timestamp = cl_abap_tstmp=>add( tstmp = lv_timestamp  secs = lv_sec ).   
        send_request->send_request->set_send_at( lv_timestamp ).

      ENDIF.
Nota: Las 2 lineas comentadas tenian como funcion tomar la hora que se genero la liberacion, con lo cual se cambio por las 10:00AM por un tema de liberacion de fondos.