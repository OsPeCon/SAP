---
title: Pagos por Transferencia.
date: Last Modified
permalink: /Pagos_por_Transferencia/
eleventyNavigation:
    key: pagos por transferencia
    order: 40
    title: Pagos por Transferencia.
---
## **Pagos por Transferencia**

**Descripción breve del proceso:**

Pagos via transferencia Banco La Pampa, Banco Nacion y Banco Hipotecario.

## Proceso paso a paso:

1. 




## **Casos / Preguntas frecuentes**

Caso 1:

Caso 2:

---

## Documentación Técnica
* Para el envio de mail en el Banco BLP/BNA, se agrego una validacion la cual deja en cola de espera en la sost en caso que la fecha de envio sea superior a la fecha del dia:

      IF sy-datum < p_output-fecha_transfer.

        lv_diff = p_output-fecha_transfer - sy-datum.
        lv_sec = lv_diff * 86400.

DATA: fechaenv(14) TYPE c.
CONCATENATE p_output-fecha_transfer '130000' INTO fechaenv.
lv_timestamp = fechaenv.

*        GET TIME STAMP FIELD lv_timestamp.               
*        lv_timestamp = cl_abap_tstmp=>add( tstmp = lv_timestamp  secs = lv_sec ).   
        send_request->send_request->set_send_at( lv_timestamp ).

      ENDIF.
