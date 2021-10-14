# Clonador de Legajos

## Descripción Breve del Proceso

Este proceso permite enviar información de legajos desde Productivo hasta Test. Una transacción genera la información en productivo y otra la levanta desde Test. La información que se traspasa de un ambiente a otro son Infotipos, Clúster de Tiempos y de Nomina y las tablas que contengan en su clave el número de personal o legajo y que son necesarias para determinados procesos. Al ejecutar la transacción de salida, se generan archivos con la información seleccionada a transportar en un lugar especificado del disco local o un servidor.


## Proceso paso a paso:

Ejecutar en ambiente Productivo la transacción de generación de tablas a clonar:

**TRANSACCION:  ZHR_CLONADOR_OUT**

Datos de selección del programa, uno o varios:

* Número de Personal
* Status de ocupación
* Sociedad
* División
* Subdivisión
* Área de nomina

Otras selecciones

* Opciones de Salida

  * Nombre Archivo de Infotipos : infotipos
  * Nombre Archivo de PCL1 y PCL2 : clúster
  * Nombre Archivo de Costos : asigancioncostos
  * Nombre Archivo de Tiempos : tiempos
  * Nombre Archivo de Tablas : tablas
  * Selección:
    * Guardar en Servidor
    * Guardar localmente: usamos la opción de guardado local.

      En esa dirección se guardaran los archivos generados.

      * Path Servidor
      * Path PC : C : \temp\prueba\  : Usamos
        esta opción como predeterminada
* Selección de Datos: indicar que información se desea clonar. Se puede seleccionar alguna de las siguientes opciones, se sugiere seleccionar todas las opciones

  * Infotipos
  * Clúster PCL1
  * Clúster PCL2
  * Asignación de Costos
  * Tiempos
  * Tablas
* Opciones
* Listar Infotipos Seleccionados
* Listar Clúster
* Display Test : indicar esta opción si solo se desea hacer un test , no genera información
* Selección de Opciones
* Infotipo : Desde – Hasta
* IDRel-PC1 : Desde – Hasta  : AR : para liquidaciones de Argentina
* IDRel-PC2 : Desde – Hasta  : AR : para liquidaciones de Argentina

Este proceso va a generar archivos en el lugar seleccionado como opción de guardado que serán leídos desde la próxima transacción a ejecutar desde Test

Ejecutar en ambiente Productivo la transacción de generación de tablas a clonar y luego ejecutar en Test la bajada de la información

**TRANSACCION:  ZHR_CLONADOR_IN**

Datos de selección del programa, uno o varios:

Se deben indicar los mismos nombres de archivos definidos en la transacción anterior

* Nombre Archivo de Infotipos
* Nombre Archivo PCL1 y PCL2
* Nombre Archivo de Costos
* Nombre Archivo de Tiempos
* Nombre Archivo de Tablas

Opción:

Seleccionar la misma opción que se seleccionó en el proceso de salida

* Leer desde servidor
* Leer desde PC

Opción ejecución en Test : no genera datos

Otras selecciones

* Selección de Datos
  * Infotipos
  * Clúster PCL1
  * Clúster PCL2
  * Asignación de Costos
  * Tiempos
  * Tablas
* Números de Personal : Se puede indicar si queremos cambiarle el número de legajo y borrar los datos que se encuentren hasta el momento y reemplazar por los nuevos
* Alias para Test : Indicar si se quiere importar la información con el nombre y domicilio real del legajo o  cambiarlo
* Alias para Cuenta : Indicar si se quiere importar la información de la cuenta bancaria y clave de banco o  cambiarlo

El clonador no genera algunas tablas clúster, para resolver esto si es que se necesitan los acumuladores ejecutamos el siguiente programa:  H99U_RGDIR_WPBP  con la transacción SE38 . 

Ahí le indicamos el o los números de legajos de los que queremos generar esas tablas

---

## Documentacion Técnica

**En SAP:**

* TRANSACCIONES:
  * ZHR_CLONADOR_OUT
  * ZHR_CLONADOR_IN
  * SE38 : H99U_RGDIR_WPBP

-Variantes:

Para ambas transacciones se generaron variantes “Clonador – Final “ , las cuales generan los archivos con todos los datos en el disco C: , sin nombre del empleado y sin cuenta bancaria
