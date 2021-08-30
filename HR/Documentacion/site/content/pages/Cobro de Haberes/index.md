# Cobro de Haberes - Transferencias 


## Descripcion breve del proceso:
Proceso de pago de sueldos y  generacion de archivos para enviar a bancos con el objetivo de realizar las transferencias bancarias correposndientes . Cada banco tiene su propio tipo de archivo para transferencias propias y hacia otros bancos por lo cual se generan archivos con distintos formatos para subir a los home banking .

***
***

## Proceso paso a paso:
El proceso de transferencias para pago de sueldos tiene  2 pasos , el primero genera el pago en el legajo del empleado segun su liquidacion de sueldo , esto puede ser total o parcial , el segundo paso es la generacion de los distintos archivos tipo txt para enviar a los bancos.

Todas las sociedades tienen cuenta en Banco La Pampa , siendo este banco el principal para toda la red , no obstante tambien existen cuentas en otros bancos como Credicoop , Hipotecario y Frances

Los empleados de cada Sociedad reciben los depositos desde las cuentas de la sociedad para la que trabajan. Si el empleado tiene cuenta en alguno de los bancos de la sociedad se realiza una transferencia directa desde el mismo banco , caso contrario se transfiere desde Banco La Pampa.
        


**Metodologia para transferencias**


**Generar las transferencias**
* Transacción  PC00_M29_CDTA / PC00_M29_CDTB

    La Primera de ellas genera la transferencia por el total del sueldo , la segunda genera un pago parcial que previamente sera ingresado en el legajo con su importe correspondiente
Se generan todas las sociedades juntas  , no es necesario seleccionar legajos , la selección se hará en el próximo paso

**Armado del Txt**

* Transacción PC00_M29_FFOT

    Se generaron las siguientes variantes que abarcarían el total de las transferencias a realizar . 
    No tuvimos en cuenta los Confidenciales en esta separación, deberían agregarse en cada variante según corresponda filtrar

    Cada variante trae definidos los codigos de Banco y Formatos 

    Variantes:

        Sociedad 0100 - Os.Pe.Con.
            -	0100–0100  : Transferencias Banco La Pampa a Banco La Pampa
            -	0100–HIPOTECARIO : Transferencia Banco Hipotecario a Banco Hipotecario
            -	0100 – CBU  : Transferencia Banco La Pampa a otros Bancos

        Sociedad 0200 - UOCRA
            -   0200 – 0200 : Transferencias Banco La Pampa a Banco La Pampa
            -	0200 – HIPOTECARIO : Transferencia Banco Hipotecario a Banco Hipotecario
            -	0200 – CBU : Transferencia Banco La Pampa a otros Bancos

        Sociedad 0300 - F.E.F.C.T.

            - 0300 - 0300  : Transferencias Banco La Pampa a Banco La Pampa
            - 0300 – CBU   : Transferencia Banco La Pampa a otros Bancos

        Sociedad 0400 - I.V.T.

            - 0400 - 0400  : Transferencias Banco La Pampa a Banco La Pampa
            -  0400 – CBU : Transferencia Banco La Pampa a otros Bancos

        Sociedad 0500 - Construir Futuro

            -	0500 - 0500 : Transferencias Banco La Pampa a Banco La Pampa
            -	0500 – CBU  : Transferencia Banco La Pampa a otros Bancos


        

Codigos de Banco para ingresar en legajo de empleados
* Banco La Pampa   - 093
* Banco Credicoop  - 191
* Banco Hipotcario - 093
* Banco Frances    - 017

Codigos de Bancos Propios :

*    Soc.0100 
        * Banco La Pampa - 19000/00005
        * Banco Hipotecario - 93100/00001
        * Banco La Pampa a otros Bancos : 19000/HR001


*    Soc.0200 
        * Banco La Pampa - 10000/00005
        * Banco Hipotecario - 91000/00001
        * Banco Credicoop - 94000/0001
        * Banco Frances - EN DESARROLLO
        * Banco La Pampa a otros Bancos : 10000/HR001

*   Soc.0300 
       * Banco La Pampa - 10000/00005
       * Banco La Pampa a otros Bancos : 10000/HR001

*   Soc.0400 
       * Banco La Pampa - 10000/00005
       * Banco La Pampa a otros Bancos : 10000/HR001

*   Soc.0500
       * Banco La Pampa - 10000/00005
       * Banco La Pampa a otros Bancos : 10000/HR001


Formatos a utilizar para el armado de los archivos TXT , indistintamete de la sociedad
* Banco La Pampa a Banco La Pampa  - HR_LAPAMPA
* Banco La Pampa a otros bancos    - HR_LAPAMPA_OTROS
* Banco Credicoop a Banco Credicoop - HR_CREDICOOP
* Banco Hipotcario a Banco Hipotecario - HR_HIPOTECARIO
* Banco Frances - En Desarrollo

Las sociedades 0100 y 0200 , tienen cuentas en todos los bancos propios ( La Pampa , Frances , Hipotecario y Credicoop ) , los empleados de esas sociedades  que tengan esos bancos ( códigos 93 , 44, 17 , 191 Respectivamente )  definidos en sus legajos recibirán la  transferencia desde las cuentas  propias de esos bancos , aquellos que tengan cuentas definidas en bancos diferentes a estos se les transferirá desde la cuenta del banco La Pampa con salida a otros bancos
Las sociedades 0300 , 0400 y 0500 , solo tienen cuenta en banco La Pampa ,con lo cual , los empleados de esas sociedades recibirán transferencias siempre desde esa cuentas , si el banco elegido es La pampa se genera en un formato la transferencia y si es diferente a la pampa se genera en otro formato


### Casos / Preguntas frecuentes
No existen casos a la fecha 

***
***
## Documentacion Técnica

**En SAP:** 

* TRANSACCION: PC00_M29_CDTA - Transferencia Total de la remuneracion
* TRANSACCION: PC00_M29_CDTB - Transferencia anticipio de la remuneracion
* TRANSACCION: PC00_M29_FFOT - Armado del txt


Los programas de transferencias generan un registro en la tabla REGUH , en este registro se incluyen datos como fecha de transferencia , código de característica ( número de generación ) y código de banco propio desde donde va a salir el dinero , datos del banco del empleado e importe a pagar.
EL programa del armado del txt para el banco , selecciona según fecha , característica , código de banco propio y formato ( esto según el banco propio lo podemos deducir )  , con eso genera el archivo correspondiente

* TRANSACCION: PC00_M29_CDTA

    Datos a ingresar:

        Area de nomina 
        Periodo de pago
        Seleccion de numeros de legajos
        Fecha de ejecucion requerida de transferencia


* TRANSACCION: PC00_M29_FFOT

    Datos a ingresar:

        Fecha
        Codigo de caracteristica ( generado en proceso anterior)
        Elegir variante segun transferencia a realizar
        Descargar el txt generado



