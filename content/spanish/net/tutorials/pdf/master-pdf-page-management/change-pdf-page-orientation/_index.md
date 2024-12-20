---
title: Cambiar la orientación de la página PDF
linktitle: Cambiar la orientación de la página PDF
second_title: Referencia de API de Aspose.PDF para .NET
description: Descubra cómo ajustar fácilmente la orientación de la página de los archivos PDF con Aspose.PDF para .NET. Esta guía paso a paso ofrece instrucciones claras sobre cómo cargar, rotar y guardar sus documentos.
type: docs
weight: 10
url: /es/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Introducción

¿Alguna vez se ha encontrado con un archivo PDF en el que la orientación de las páginas no es correcta? Ya sea que se trate de un documento que se escaneó incorrectamente o de uno que simplemente necesita un diseño diferente, ajustar la orientación puede marcar una gran diferencia. Afortunadamente, Aspose.PDF para .NET ofrece una forma potente y fácil de usar de manipular archivos PDF, incluido el cambio de la orientación de las páginas. En esta guía, lo guiaremos paso a paso por el proceso, ya sea que desee cambiar de vertical a horizontal o viceversa.

## Prerrequisitos

Antes de profundizar en los detalles, asegúrese de tener lo siguiente en su lugar:

-  Aspose.PDF para .NET: Asegúrese de tener instalada la biblioteca Aspose.PDF. Si aún no lo ha hecho, puede[Descárgalo aquí](https://releases.aspose.com/pdf/net/).
- Un entorno de desarrollo .NET: puede utilizar Visual Studio, JetBrains Rider o cualquier otro IDE que prefiera para el desarrollo .NET.
- Conocimientos básicos de C#: Estar familiarizado con C# le ayudará a seguir el proceso más fácilmente.
- Un archivo PDF: tenga listo un archivo PDF de muestra para probar. Puede crear uno o descargar una muestra en línea.

 Si recién está comenzando, considere probar Aspose.PDF con un[licencia temporal gratuita](https://purchase.aspose.com/temporary-license/) Antes de decidir[comprar la versión completa](https://purchase.aspose.com/buy).

## Importar espacios de nombres

Para manipular páginas PDF, primero deberá importar los espacios de nombres necesarios en su proyecto de C#. Agregue las siguientes líneas en la parte superior de su archivo de código:

```csharp
using System.IO;
using Aspose.Pdf;
```

Ahora que tenemos todo configurado, ¡comencemos!

## Paso 1: Cargue el documento PDF

 El primer paso es cargar el archivo PDF que desea modificar. Utilice el botón`Document` clase del espacio de nombres Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Asegúrese de reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su archivo PDF.

## Paso 2: Recorre cada página

A continuación, recorreremos cada página del documento PDF. Esto nos permitirá aplicar el cambio de orientación a todas las páginas:

```csharp
foreach (Page page in doc.Pages)
{
    // Manipular cada página
}
```

## Paso 3: Acceda al MediaBox de la página

 Cada página PDF tiene una`MediaBox` que define sus límites. Necesitamos acceder a él para comprobar la orientación actual y realizar ajustes:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 El`MediaBox` Proporciona las dimensiones de la página, incluido el ancho y la altura.

## Paso 4: Intercambiar ancho y alto

Para cambiar la orientación de la página, intercambiaremos los valores de ancho y alto. Este ajuste cambiará las dimensiones de la página:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Aquí, calculamos las nuevas dimensiones y reposicionamos la esquina inferior izquierda (`LLY`) respectivamente.

## Paso 5: Actualizar MediaBox y CropBox

 Ahora que tenemos las nuevas dimensiones, aplicaremos estos cambios a la`MediaBox` y`CropBox` Para garantizar que la página se muestre correctamente:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Paso 6: Girar la página

Para finalizar el cambio de orientación, rotaremos la página. Esto es muy sencillo con Aspose.PDF:

```csharp
page.Rotate = Rotation.on90; // Girar 90 grados
```

Esta línea voltea efectivamente la página a la orientación deseada.

## Paso 7: Guardar el PDF de salida

Después de modificar la orientación de todas las páginas, guarde el documento actualizado en un nuevo archivo:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Asegúrese de proporcionar un nuevo nombre de archivo para evitar sobrescribir el documento original.

## Conclusión

¡Y ya está! Cambiar la orientación de la página de un archivo PDF con Aspose.PDF para .NET es un proceso sencillo. Al cargar el documento, recorrer las páginas, actualizar el MediaBox y guardar el archivo, puede ajustar fácilmente el diseño para satisfacer sus necesidades. Ya sea que esté corrigiendo un documento mal escaneado o formateando páginas para una presentación, esta guía debería ayudarlo a realizar el trabajo de manera eficiente.

## Preguntas frecuentes

### ¿Puedo rotar páginas específicas en lugar de todas las páginas del PDF?  
Sí, puedes modificar el bucle para apuntar a páginas específicas por su índice en lugar de iterar a través de todas las páginas.

### ¿Qué es el?`MediaBox`?  
 El`MediaBox` define el tamaño y la forma de la página en un archivo PDF, determinando dónde se coloca el contenido.

### ¿Aspose.PDF para .NET funciona con otros formatos de archivo?  
Sí, Aspose.PDF puede manejar varios formatos de archivos, incluidos HTML, XML, XPS y más.

### ¿Existe una versión gratuita de Aspose.PDF para .NET?  
 Sí, puedes empezar con un[prueba gratis](https://releases.aspose.com/) o solicitar una[licencia temporal](https://purchase.aspose.com/temporary-license/).

### ¿Puedo deshacer los cambios una vez guardados?  
Una vez que guardes el documento, los cambios serán permanentes. Es recomendable trabajar sobre una copia o mantener un respaldo del archivo original.