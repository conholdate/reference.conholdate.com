---
title: Listas numeradas con estilo usando Aspose.PDF para .NET
linktitle: Listas numeradas con estilo usando Aspose.PDF para .NET
second_title: Referencia de API de Aspose.PDF para .NET
description: Descubra cómo crear listas numeradas de forma atractiva en sus documentos PDF con Aspose.PDF para .NET. Esta guía le muestra el proceso de aplicación de varios estilos de numeración, como los números romanos.
type: docs
weight: 10
url: /es/net/programming-with-headings/stylish-numbered-lists/
---
## Introducción

¿Alguna vez ha necesitado crear listas numeradas y bien estructuradas en sus documentos PDF? Ya sea para documentos legales, informes o presentaciones, los estilos de numeración efectivos son cruciales para organizar su contenido. Con Aspose.PDF para .NET, puede aplicar fácilmente varios estilos de numeración a los encabezados de sus PDF, lo que da como resultado documentos pulidos y profesionales.

## Prerrequisitos

Antes de comenzar con la codificación, asegúrese de tener listo lo siguiente:

1.  Aspose.PDF para .NET: Descargue la última versión desde[aquí](https://releases.aspose.com/pdf/net/).
2. Entorno de desarrollo: necesitará Visual Studio o cualquier IDE compatible con .NET.
3. .NET Framework: asegúrese de tener instalado .NET Framework 4.0 o superior.
4.  Licencia: Puede utilizar una licencia temporal de[aquí](https://purchase.aspose.com/temporary-license/) o explorar el[prueba gratis](https://releases.aspose.com/) Opciones.

## Importación de paquetes necesarios

Comience importando los espacios de nombres necesarios en su proyecto:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Paso 1: Configuración del documento

Comencemos creando un nuevo documento PDF y configurando su diseño, incluido el tamaño de página y los márgenes.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Establecer las dimensiones y los márgenes de la página
pdfDoc.PageInfo.Width = 612.0; // 8,5 pulgadas
pdfDoc.PageInfo.Height = 792.0; // 11 pulgadas
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // Márgenes de 1 pulgada
```

Esta configuración le da a su documento un tamaño de carta estándar con márgenes de una pulgada en todos los lados.

## Paso 2: Agregar una página al PDF

A continuación, agregaremos una página en blanco al documento PDF, donde luego aplicaremos los estilos de numeración.

```csharp
// Agregar una nueva página al documento PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Utilice la misma configuración que el documento
```

## Paso 3: Crear un cuadro flotante

Un FloatingBox le permite posicionar el contenido independientemente del flujo de la página, lo que le brinda un mayor control sobre su diseño.

```csharp
//Crear un FloatingBox para contenido estructurado
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Paso 4: Agregar títulos con números romanos

Ahora, agreguemos nuestro primer encabezado con numeración en números romanos en minúscula.

```csharp
// Crea el primer encabezado con números romanos
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Paso 5: Agregar un segundo encabezado con un número inicial personalizado

A continuación, agregaremos un segundo encabezado, comenzando desde el número romano 13.

```csharp
// Crea un segundo encabezado que comience con el número romano 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Paso 6: Agregar un encabezado con numeración alfabética

Para variar, agreguemos un tercer encabezado utilizando numeración alfabética en minúsculas.

```csharp
// Crear un encabezado con numeración alfabética
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Paso 7: Guardar el PDF

Por último, guardemos el archivo PDF en el directorio que deseemos.

```csharp
// Guardar el documento PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Conclusión

¡Felicitaciones! Ha aplicado con éxito varios estilos de numeración (números romanos y alfabéticos) a los encabezados de un archivo PDF con Aspose.PDF para .NET. La flexibilidad de Aspose.PDF le permite controlar el diseño de la página, los estilos de numeración y la posición del contenido, lo que le permite crear documentos PDF bien organizados y profesionales.

## Preguntas frecuentes

### ¿Puedo aplicar diferentes estilos de números al mismo documento PDF?  
Sí, puede mezclar diferentes estilos de numeración, como números romanos, números arábigos y numeración alfabética dentro del mismo documento.

### ¿Cómo puedo personalizar el número inicial de los encabezados?  
 Puede establecer el número de inicio para cualquier encabezado utilizando el`StartNumber` propiedad.

### ¿Hay alguna forma de restablecer la secuencia de numeración?  
 Sí, puede restablecer la numeración ajustando la`StartNumber` propiedad para cada encabezado.

### ¿Puedo aplicar estilo negrita o cursiva a los encabezados además de la numeración?  
 ¡Por supuesto! Puedes personalizar los estilos de encabezado modificando propiedades como fuente, tamaño, negrita y cursiva mediante el botón`TextState` objeto.

### ¿Cómo puedo obtener una licencia temporal para Aspose.PDF?  
 Puede obtener una licencia temporal en[aquí](https://purchase.aspose.com/temporary-license/)para probar Aspose.PDF sin restricciones.