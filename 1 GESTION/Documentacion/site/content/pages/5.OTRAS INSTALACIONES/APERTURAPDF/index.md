---
title: APERTURAPDF.
date: Last Modified
permalink: /APERTURAPDF/
eleventyNavigation:
    key: aperturapdf
    order: 50
    title: APERTURAPDF.
---
## **Apertura PDF**

Cambiar aplicacion "PDF" predeterminada. Por defecto esta asignada el navegador "EDGE" por lo cual hay que predeterminar "AdobeAcrobatReaderDC".

**Descripción breve del proceso:**

Problema de la vista de documentos mediante la transacción FB02 en SAP.

## Documentación Técnica

Para que el archivo ".PDF" sea abierto en forma automática por el Acrobat Reader de la siguiente forma:

1. En el perfil de la persona a configurar seleccionar un archivo PDF luego presionar el botón Propiedades y luego seleccionar botón Cambiar .

![img](../content/images/AperturaPDF/aperturapdf1.jpg)

2. Luego seleccionamos la opción Adobe Acrobat Reader y después seleccionar botón Aceptar para grabar los cambios.

![img](../content/images/AperturaPDF/aperturapdf2.jpg)

3. Una vez finalizado cerrar el explorador de Windows.

Luego en el Front End de SAP ejecutamos las transacción FB02 y realizamos la prueba de visualización :

![img](../content/images/AperturaPDF/aperturapdf3.jpg)

4. En la siguiente pantalla le damos botón Permitir para visualizar el documento seleccionado.

![img](../content/images/AperturaPDF/aperturapdf4.jpg)

5. En la siguiente pantalla se ve en evidencia el contenido del documento PDF mediante el programa de Adobe Acrobat Reader DC sin utilizar el navegador Edge.

Importante : Hay que tener en cuenta que la primera apertura de visualizacion de los documentos PDF cuando se enciende el ordenador diariamente puede tardar unos segundos y la segunda visualizacion deberia ser rapida debido a que el programa quedo en cache de memoria.

Y por ultimo la opcion mas recomendable a futuro sobre el producto, es tener instalado en los ordenadores que disponen SAP en Windows 10 unidades de DISCO SOLIDO (SDD) con eso se garantiza la velocidad y performance al momento de procesar datos

![img](../content/images/AperturaPDF/aperturapdf5.jpg)
