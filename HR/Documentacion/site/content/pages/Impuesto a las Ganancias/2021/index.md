---
title: F1357.
date: Last Modified
permalink: /2021/
eleventyNavigation:
    key: f1357
    order: 2
    title: F1357.
---
# Tecnología de la Información

## Ley 27617 - Impuesto a las Ganancias

**Agenda 2021** 

- Abril 2021 -  Decreto 336,excluye al aguinaldo del cálculo de la base imponible; elimina el tope de deducción por hijos con discapacidad; introduce la figura de concubino dentro de las cargas de familia; y exime del pago a las horas horas extras o guardias del personal de salud hasta septiembre.
- Junio 2021 - RG 5008/2021 - Devolucion

## Descripcion breve del proceso de devolucion:

Para transitar a las nuevas normas del cálculo de Impuesto a las Ganancias de la Ley 27617/21, la Resolución General 5008/21 establece que cualquier diferencia originada por la aplicación de las deducciones y exenciones de enero a mayo debe ser devuelta en cinco cuotas iguales de julio a noviembre. Adicionalmente, si ya se calcularon, los períodos de junio y julio también pueden generar diferencias que se deben reincorporar al empleado, no incluidas en las cuotas.

La identificación de esta diferencia en el impuesto consiste en: comparar el impuesto calculado originalmente en los períodos afectados con el nuevo impuesto calculado, donde ya se aplican los nuevos requisitos de la Ley y RG. 

Debido a la complejidad y la falta de tiempo de pruebas del proceso,  SAP provee una solucion automatica y nominas manuales para ajustes en los casos que no funcione la solucion automatica

---

---

## Proceso paso a paso:

En el mes de setiembre 2021 se implementa esta modificación publicada en Junio 2021 con lo cual debemos hacer un cálculo retro desde enero a la fecha y un recalculo de junio en adelante.

El impuesto a devolver de enero a mayo inclusive se devuelve en 5 cuotas en los meses de  Julio, Agosto, Setiembre, Octubre,Noviembre

Como esto se implementa en el mes de Setiembre el sistema debe calcular 2 cuotas Retro (Julio y Agosto) y una cuota Setiembre y quedaran 2 cuotas para los próximos meses

Como SAP no termino de considerar todos los escenarios posibles se crearon nóminas de ingreso manual para resolver esos casos

Hasta acá lo que detectamos nosotros son varios grupos de tipos de liquidación

- Legajos de menos de 150000 , no deberían tener ningún problema ( excepto con embargos )
- Legajos de más 173000 desde enero
- Legajos con embargos
- Legajos de entre 150000 y 173000 o más de junio en adelante

**Consideraciones Generales**

**Registro de Gestión para liquidar** 

Registro al 09/2021

Retro obligatoria 01/2021

**Constantes para Retro**

Tabla :  V_T511K

REDED - Law 27617- Deducc. Originales	31.12.2020	30.06.2021 Valor 1
								01.07.2021	31.08.2021 Valor 1
								01.09.2021	07.10.2021 Valor 1
								08.10.2021	31.12.9999 Valor 0

RETAX - Law 27617 - Recalc tax origin	31.12.2020	30.06.2021 Valor 1
								01.07.2021	31.08.2021 Valor 1
								01.09.2021	07.10.2021 Valor 1
								08.10.2021	31.12.9999 Valor 0

Terminada la liquidacion de Setiembre se volvieron todos los valores a "0" segun indicacion de SAP


**Liquidación**

```
Siempre indicar retro al
```

01.01.2021

**Nominas manuales a utilizar brindadas por SAP**

Se ingresan en el infotipo 14 y/o 15 y son:

- M4NR : Deshabilitar el retro cálculo
- M4JT :  Forzar el impuesto a devolver
- M4TD : Devolver una cuota diferente
- M147 : Modificar la base  calculo
- M41D : Ajustar las deducciones especiales en sueldos de hasta 150000
- M42D : Ajustar las deducciones especiales en sueldos de entre 150000 y 173000

**Legajos de menos de 150000 en todo el periodo**

Se le debe devolver todo el impuesto retenido en todo el periodo , estos casos funcionas bien en forma automatica . Se generan las 5 cuotas a devolver de enero a mayo y se devuelve retro junio , julio , agosto y setiembre ya no calcula impuesto

**Legajos de más de 173000 en todo el periodo**

Estos legajos no deberían tener ningún tipo de devolución  y el impuesto no debería cambiar, pero como

no está funcionando correctamente debemos ingresar la nómina manual

M4NR  - del 01.01.2021 al 31.08.2021

Con esto logramos que no haga ningún retro y que el impuesto siga de la misma manera

**Legajos con Embargos e Impuesto a las Ganancias**

Al generar estas liquidaciones con cálculo retro, hace un retro de embargos que no corresponde, para resolverlo hacemos lo siguiente:

1-      Simular la liquidación sin hacer nada , de ahí obtenemos:

```
a.       Importe correcto de cuotas a generar por la devolución de 		enero a Mayo
```


```
b.      Importe correcto de devolución de Junio a Setiembre
```


```
c.       Importe correcto de impuesto Setiembre
```


2-      Agregar en el infotipo 14

```
a.       M4NR – 01.01.2021 al 31.08.2021 – Con esto le decimos que no haga retro
```


```
b.      M4JT – importe (b) de devolución de Junio a Setiembre, ingresar en negativo
```


```
c.       M4TD – Devolución en cuotas. Acá siempre se debe poner el importe de la devolución total y el sistema hace 5 cuotas de ese importe. 		En estos casos que le decimos que no haga retro no me va a calcular las cuotas de Julio y agosto , lo cual lo resolvemos de la siguiente manera
```


```
i.	M4TD – 01.09.2021 al 30.11.2021 – Importe total a 	devolver ( en negativo) : Genera cuotas Setiembre , Octubre y Noviembre
```


```
ii.	M4TD -
```

01.09.2021 al 30.09.2021  - Importe total a devolver , Genera 1 cuota para este mes

```
iii.	M4TD - 01.09.2021 al 30.09.2021  - Importe
	total a devolver , Genera 1 cuota para este mes
```


Así tendríamos 3 cuotas en setiembre, 1 para octubre, 1 para noviembre

**Legajos con Embargos sin Impuesto a las Ganancias**

A estos legajos debemos borrarle del status de nomina ( infotipo 3 ) ,las fechas de retroactividad y cálculos , con esto resolvemos el tema de la retroactividad.

**Legajos con Pluriempleo**

Al generar estas liquidaciones, devuelve todo siempre sin tener en cuenta ni el pluriempleo ni el sueldo, ni nada, con lo cual NO funciona y debemos manejarlo en forma manual.

Acordamos con Devora darle a estos legajos el tratamiento de los de más de 173000, no devolver nada y generar el impuesto del mes como el del mes pasado, después se ajustara en la liquidación final en el caso de corresponder

Para hacer esto debemos hacer lo siguiente

- M4NR – 01.01.2021 al 31.08.2021
- M4JT   - 01.09.2021 al 30.09.2021 con impuesto determinado en agosto

**Legajos con impuesto determinado en el año de menos de  150000 y superiores a partir de junio**

Este grupo de legajos que están en este rango y se les debe devolver todo en el periodo hasta junio y parcial después, no está funcionando correctamente y devuelve todo hasta setiembre inclusive

Para resolverlo le debemos ingresar manualmente las nóminas de deducción especial con los importes según el sueldo de cada mes (Junio – Julio – Agosto – Setiembre)

- M41D – 01.06.2021 al 30.06.2021 con importe de tabla
- M41D – 01.07.2021 al 31.07.2021 con importe de tabla
- M41D – 01.08.2021 al 31.08.2021 con importe de tabla
- M41D – 01.09.2021 al 30.09.2021 con importe de tabla

Aclaracion : en estos casos se deberia usar la nomina M41D si el sueldo es menos de 150000 y M42D si esta entre 150000 y 173000 , pero la nomina de M42D no estaba funcionando correctamente asi que decidimos usar para todos la M41D
