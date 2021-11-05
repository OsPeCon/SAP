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

```
Fecha de movimiento:  se graba en la fecha de documento
```


```
Fecha VAlor: se graba en la fecha valor
```


```
Fecha de proceso: no se graba en el documento
```


<!--
 /* Font Definitions */
 @font-face
	{font-family:Wingdings;
	panose-1:5 0 0 0 0 0 0 0 0 0;
	mso-font-charset:2;
	mso-generic-font-family:auto;
	mso-font-pitch:variable;
	mso-font-signature:0 268435456 0 0 -2147483648 0;}
@font-face
	{font-family:"Cambria Math";
	panose-1:2 4 5 3 5 4 6 3 2 4;
	mso-font-charset:0;
	mso-generic-font-family:roman;
	mso-font-pitch:variable;
	mso-font-signature:-536869121 1107305727 33554432 0 415 0;}
 /* Style Definitions */
 p.MsoNormal, li.MsoNormal, div.MsoNormal
	{mso-style-unhide:no;
	mso-style-qformat:yes;
	mso-style-parent:"";
	margin:0cm;
	margin-bottom:.0001pt;
	mso-pagination:widow-orphan;
	mso-hyphenate:none;
	font-size:10.0pt;
	font-family:"Times New Roman",serif;
	mso-fareast-font-family:"Times New Roman";
	mso-ansi-language:ES;
	mso-fareast-language:ES;}
.MsoChpDefault
	{mso-style-type:export-only;
	mso-default-props:yes;
	font-size:10.0pt;
	mso-ansi-font-size:10.0pt;
	mso-bidi-font-size:10.0pt;}
@page WordSection1
	{size:612.0pt 792.0pt;
	margin:70.85pt 3.0cm 70.85pt 3.0cm;
	mso-header-margin:36.0pt;
	mso-footer-margin:36.0pt;
	mso-paper-source:0;}
div.WordSection1
	{page:WordSection1;}
 /* List Definitions */
 @list l0
	{mso-list-id:1093628789;
	mso-list-type:hybrid;
	mso-list-template-ids:1721636328 201981957 201981955 201981957 201981953 201981955 201981957 201981953 201981955 201981957;}
@list l0:level1
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:36.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l0:level2
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:72.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l0:level3
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:108.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l0:level4
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:144.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Symbol;}
@list l0:level5
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:180.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l0:level6
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:216.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l0:level7
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:252.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Symbol;}
@list l0:level8
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:288.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l0:level9
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:324.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l1
	{mso-list-id:1387988908;
	mso-list-type:hybrid;
	mso-list-template-ids:522219780 201981957 201981955 201981957 201981953 201981955 201981957 201981953 201981955 201981957;}
@list l1:level1
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:36.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l1:level2
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:72.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l1:level3
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:108.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l1:level4
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:144.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Symbol;}
@list l1:level5
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:180.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l1:level6
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:216.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
@list l1:level7
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:252.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Symbol;}
@list l1:level8
	{mso-level-number-format:bullet;
	mso-level-text:o;
	mso-level-tab-stop:288.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:"Courier New";
	mso-bidi-font-family:"Times New Roman";}
@list l1:level9
	{mso-level-number-format:bullet;
	mso-level-text:;
	mso-level-tab-stop:324.0pt;
	mso-level-number-position:left;
	text-indent:-18.0pt;
	font-family:Wingdings;}
ol
	{margin-bottom:0cm;}
ul
	{margin-bottom:0cm;}
-->

2. El Programa **ZCONCILIA Guarda en \uocrafs\ datanet\ backup, una copia del archivo TXT, tal cual lo envió el banco. Este archivo no se pisa sino que se guardan todos y se zipea anualmente para guardar la información compactada. Ademas, se guarda un log de las contabilizaciones y errores del proceso.



### Casos / Preguntas frecuentes

No existen casos a la fecha

---

---

## Documentacion Técnica

**Para Canje Automatico:**

Transacción: ZDAT
Programa: ZCONCILIA

Pantalla de Selección:

* Sociedad:
* Doc. Pago rechazado:  validar que se trate de clase de documento de pago KZ o ZP
* Ejercicio:
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

```
-Si el asiento tiene cuenta T012K-HKONT con ID 00002, entonces se 							usa T012K-HKONT de ID 00003

-Si el asiento tiene cuenta T012K-HKONT con ID 00005, entonces se usa T012K-HKONT de ID 00006

EXCEPCION (*): Si T012K-HKONT=1101021414 o 1101021394 entonces se usa T012K-HKONT de ID 00012
```

VALIDACIONES

SOLO CANJEAR  en el caso en que ya se encuentre la OP liberada o compensada y SIN EXTRACTO BANCARIO (1)

NO CANJEAR cuando:

- No esta liberado (2)
- Esta liberado pero tiene conciliacion bancaria (3). Esta validacion solo realizarla para Banco   HBKID = 93000 para BUKRS = 0100, HBKID = 95000 para BUKRS = 0200
- La OP esta anulada, es decir BKPF = STBLG es distinto de vacio. Mensaje de error: “La OP se encuentra anulada con doc BKPF = STBLG

Especicacion de la validacion para hacer el canje:

Ingresar a BSEG con SOC y BELNR = doc de pago y clase de cuenta KOART = “S”.

Si para ese registro el campo BSEG-AUGBL es distinto de vacio, hacer un segundo ingreso a la BSEG con
Soc, BELNR = valor encontrado en BSEG-AUGBL y BSEG-BSCHL = 50. Si para ese registro BSEG-AUGBL es vacio, ENTONCES LIBERAR. (1)

```
    -Si ese campo es distinto de vacio (3) NO LIBERAR y arrojar el siguiente error: “la OP no puede canjearse ya que se encuentra conciliada con Documento XXXXXXXX” siendo xxxxx el valor que se encuentra en BSEG-AUGBL.
```

-Si BSEG-AUGBL es vacio,  (2) entonces arrojar mensaje de error: “la OP no puede canjearse ya que aun no se encuentra liberada.

Validacion de que el canje no este realizado.

Validacion de Sociedad.

Validacion de Ejercicio.

Validacion de O.P. anulada.

Validacion de O.P. ya canjeada.

**Para canje manual no existe documentacion tecnica**
