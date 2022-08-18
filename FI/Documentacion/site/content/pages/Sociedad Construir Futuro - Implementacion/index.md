---
title: CONSTRUIR FUTURO.
date: Last Modified
permalink: /Construir Futuro./
eleventyNavigation:
    key: Construir Futuro.
    order: 120
    title: CONSTRUIR FUTURO.
---
## **IMPLEMENTACION SOCIEDAD**

FUNDACION CONSTRUIR FUTURO.

| Documentado por | Mariela Etcheverry - SAP – Tecnología de la Información |
|-----------------|---------------------------------------------------------|
| Fecha           | 14.01.2021                                              |
| Estado          | En proceso                                              |

    
**Descripción del proceso:**


Contabilidad General

Definición de Datos de la Sociedad
Fecha de constitución de Fundación Construir Futuro: 02/12/1999
CUIT: 33-70710321-9
IIBB Exento
Clase de impuesto frente al IVA: Responsable Exento
La actividad no está gravada
No es Agente de Retención de Impuesto a las Ganancias ni IIBB

Plan de Cuentas: se tomará como base el plan de cuentas de la sociedad OSPECON y se habilitaran las cuentas contables que utiliza FUNDACION. 
Dichas cuentas serán dadas de alta en forma manual. 

Ajuste por Inflación: se definen los parámetros de ajuste por inflación ídem sociedades existentes.

Tipos de comprobantes a utilizar: 
Factura 
Nota de crédito     
Nota de débito
Otros doc. Según RG3419 39
Otros doc. No según RG3419 99

Las parametrizaciones generales serán tomadas de la actual parametrización existente en SAP

Manejo de apertura y cierre de períodos contables:
La apertura y cierre de períodos contables para contabilizar se manejara para esta sociedad. El balance cierra el 30.11

IVA
Fundación es Responsable Exento en el IVA, con lo cual solo se configurara el código C0 “Exento del pago de impuestos”


Cuentas a Pagar

Proveedores:
Se define utilización de grupo de cuentas de proveedores Z001 – Proveedores.
Los proveedores se darán de alta en forma manual.

Anticipo a Proveedores: 
Se habilitara el tipo de anticipos “3 – Anticipo a proveedores bienes y servicios”.

Circuito de Pagos a Proveedores
Todas las facturas y comprobantes a pagar serán registrados en SAP con indicador de bloqueo “2”.
Luego seguirán el circuito de desbloqueo a través del traslado de documento de proveedores y su desbloqueo posterior (transacciones ZTD1 y ZDL1.


Circuito de pagos

Los bancos Ciudad y Nación se darán de alta como cuenta contable para realizar las distintas operaciones.
Ciudad cta. Cte. 277/8
Nacion cta. Cte 49292/22

El banco de la Pampa se dará de alta en forma completa en cuanto al circuito de pagos tanto de cheque como transferencias.
Nro. Cuenta bancaria BLP: cta. Cte. 5648/5
Banco Propio: 10000

| Denominación                                 | Cuenta contable |
|----------------------------------------------|-----------------|
| Banco Cheque Emitido no entregado            | 1101022131      |
| Banco Cheque Liberado                        | 1101022132      |
| Banco Cuenta Corriente                       | 1101022130      |
| Banco Movimientos pendientes de acreditación | 1101022133      |
| Banco Transferencia no liberada              | 1101022134      |
| Banco Transferencia Liberada                 | 1101022135      |

Para el banco mencionado, se habilitarán todas las transacciones necesarias de pago mediante trasferencia por archivo. 

La conciliación bancaria se configurara en forma automática para Banco de la Pampa, esto se hará con el primer extracto bajado de datanet.


Cuentas a Cobrar y Clientes:

Definir la Sucursal emisora de facturación: pendiente

Clientes:
Se define utilización de grupo de cuentas de deudores Z001 – Clientes.
Los mismos serán dados de alta en forma manual.

Facturación:
La emisión de las mismas se realizara por la aplicación AFIP de comprobantes en línea  y luego serán registradas contablemente.
Se trata de Recibos tipo C.


Manejo de Costos

Las cuentas de resultado negativo deben ser dadas de alta como clases de costo.

Jerarquía definida para Centros de Costos: FUNDACION

La numeración de los CeCo será a partir de 500000


Activos Fijos

Se habilitara el modulo activos fijos para tipo de Activos “instalaciones”.


ANEXO I – Seguridad: Usuarios y Permisos

Usuarios de Fundación
PROMERO
NMARTI
DTAMARGO
OBURGOS
LBUSSI

Definir si desempeñaran las mismas funciones que en OSPECON para replicar los perfiles de autorización.


ANEXO II – ABAP

A la fecha se detectaron los siguientes programas Z a modificar para integrar la nueva sociedad

| Referencia        | Trx             | Programa                     | Formulario       |
|-------------------|-----------------|------------------------------|------------------|
| Trasnferencia BLP | ZFI_LOTES_BLP   | ZFI_LOTES_BLP_2              |                  |
| Trasnferencia BLP | ZFI_LIB_BLP     | ZFI_LIB_BLP                  |                  |
| Trasnferencia BLP | ZFI_ARCHIVO_BLP | ZFI_ARCHIVO_BLP              |                  |
| Trasnferencia BLP | ZCBU_2          | Z_FI_PAGO_2                  |                  |
| Desbloqueo doc    | ZDL1            | Z_DESBLOQ_ZTRASLADO_CONTABLE |                  |
| Desbloqueo doc    | ZTD1            | ZTRASLADO_CONTABLE           |                  |
| Emision OP        | ZODP            | Z_SELECCION_ORDEN_DE_PAGO    | Z_1A_F012_PM_NO2 |
| Emision Recibo    | ZRE             | Z_1AF011                     | Z_1A_F011_PM_NOT |
			

ANEXO III – Plan de Implementación 

Se definen las siguientes tareas por parte de Equipo SAP – TI:
•	Culminar  el diseño en forma total con la obtención de definiciones pendientes
•	Configuración del Sistema. OK  
•	Modificaciones en programación ABAP para programas y formularios. OK
•	Alta de Perfiles de autorización. Ok 
•	Pruebas unitarias ambiente DESARROLLO. OK
•	Prueba de sistemas ambiente QAs. OK
•	Pase a productivo de las OT. OK
•	Tareas pos implementación:
	Creación de Grupos de Numeración legal en mandantes QAs y PROD para emisión de factura. Pendiente por definir sucursal emisora.
	Creación de Rangos de números  en mandantes QAs y PROD para clases de documento FI. OK
	Creación de Rangos de números en mandantes QAs y PROD para documentos CO. OK
	Creación de Clave de Banco (FI01) OK

Se definen las siguientes tareas funcionales a cargo de usuarios:
•	Alta de cuenta plan de cuentas y sociedad (incluida cuenta de remanente 3301010002)
•	Alta de proveedores
•	Alta de Deudores
•	Alta de Centros de Costos (numeracion 5xxxxx)
•	Alta de Clases de Costos
•	Carga inicial de saldos contables mediante asiento manual XA
•	Carga inicial de saldo de acreedores
•	Carga inicial de saldo de deudores

