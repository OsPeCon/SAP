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
* Fecha de proceso: no se graba en el documento

Esta transaccion contabiliza las compensaciones de los bancos y los movimientos de gastos.

Para que estas contabilizaciones sean posibles, deben estar debidamente configuradas las siguientes tablas y transacciones:

Tabla ZCONCILIA: actualizable por el usuario mediante transaccion "ZCONCILIA". Indica los asientos contables a realizar y la Regla de contabilización, según cuenta
bancaria y operación externa.

Tabla ZCODEX: contiene los códigos externos Datanet con sus características (debe/ haber, tipo operación, etc.) . Actualizable por Tecnologia de la Informacion mediante la transaccion ZCODEX.

Tabla ZCTABANK:  Contiene los datos de Cuentas bancarias en bancos propios. Si hay una “X” en el campo Ignora, esto hace que la 		cuenta no sea procesada. Actualizable por Tecnologia de la Informacion mediante la transaccionSistemas con la Trx. SM30

<!--
 /* Font Definitions */
 @font-face
	{font-family:"Cambria Math";
	panose-1:2 4 5 3 5 4 6 3 2 4;
	mso-font-charset:0;
	mso-generic-font-family:roman;
	mso-font-pitch:variable;
	mso-font-signature:-536869121 1107305727 33554432 0 415 0;}
@font-face
	{font-family:"Albertus Medium";
	mso-font-alt:"Century Gothic";
	mso-font-charset:0;
	mso-generic-font-family:swiss;
	mso-font-pitch:variable;
	mso-font-signature:7 0 0 0 147 0;}
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
p.MsoHeader, li.MsoHeader, div.MsoHeader
	{mso-style-unhide:no;
	mso-style-link:"Encabezado Car";
	margin:0cm;
	margin-bottom:.0001pt;
	mso-pagination:widow-orphan;
	mso-hyphenate:none;
	tab-stops:center 212.6pt right 425.2pt;
	font-size:10.0pt;
	font-family:"Times New Roman",serif;
	mso-fareast-font-family:"Times New Roman";
	mso-ansi-language:ES;
	mso-fareast-language:ES;}
p.MsoFooter, li.MsoFooter, div.MsoFooter
	{mso-style-unhide:no;
	mso-style-link:"Pie de página Car";
	margin:0cm;
	margin-bottom:.0001pt;
	mso-pagination:widow-orphan;
	mso-hyphenate:none;
	tab-stops:center 212.6pt right 425.2pt;
	font-size:10.0pt;
	font-family:"Times New Roman",serif;
	mso-fareast-font-family:"Times New Roman";
	mso-ansi-language:ES;
	mso-fareast-language:ES;}
span.EncabezadoCar
	{mso-style-name:"Encabezado Car";
	mso-style-unhide:no;
	mso-style-locked:yes;
	mso-style-link:Encabezado;
	mso-ansi-language:ES;
	mso-fareast-language:ES;}
span.PiedepginaCar
	{mso-style-name:"Pie de página Car";
	mso-style-unhide:no;
	mso-style-locked:yes;
	mso-style-link:"Pie de página";
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
	margin:70.9pt 36.85pt 2.0cm 2.0cm;
	mso-header-margin:36.0pt;
	mso-footer-margin:36.0pt;
	mso-paper-source:0;}
div.WordSection1
	{page:WordSection1;
	mso-footnote-position:beneath-text

Si se realiza cualquier cambio en ZCODEX o ZCUENTABANK, el usuario deberá actualizar ZCONCILIA.

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

Antes de procesar hacer llamada a la tabla ZDATANET001 y chequear fecha de proceso.

Si existe fecha de proceso del dia anterior, no procesar el archivo, sino dar una advertencia: "ya se ha procesado fecha XX.XX.XXX", sin contemplar sabados, domingos ni feriados.

Crear reporte a tabla ZDATANET001 con visualizacion de fecha de proceso.

---
