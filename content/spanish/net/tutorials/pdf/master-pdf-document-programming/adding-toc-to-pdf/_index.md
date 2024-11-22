---
title: Cómo agregar una tabla de contenido a un documento PDF
linktitle: Cómo agregar una tabla de contenido a un documento PDF
second_title: Referencia de API de Aspose.PDF para .NET
description: Este tutorial demuestra cómo agregar una tabla de contenido (TOC) a un documento PDF usando Aspose.Pdf para .NET.
type: docs
weight: 40
url: /es/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Introducción

La creación de una tabla de contenidos (TOC) en un documento PDF puede mejorar enormemente su navegación y accesibilidad. En esta guía, demostraremos cómo agregar una TOC a un archivo PDF utilizando Aspose.Pdf para .NET.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.   Aspose.PDF para .NET: Descargue e instale la última versión desde[aquí](https://releases.aspose.com/pdf/net/).
2.  Entorno de desarrollo: configure un entorno de desarrollo .NET como Visual Studio.
3.   Licencia: Solicite una licencia temporal si es necesaria; visite[Página de licencias de Aspose.Pdf](https://asposepdf.com/developers) Para más información.

Importación de las bibliotecas necesarias

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Paso 1: Cargue el documento PDF

Cargue el archivo PDF existente en el que desea agregar la tabla de contenidos. Especifique la ruta al directorio de documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Paso 2: Insertar una nueva página para la tabla de contenidos

Insertar una nueva página al comienzo del documento PDF. Esta página servirá como índice (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Paso 3: Crear un objeto de información de TOC

Crea un objeto que represente la información de la tabla de contenidos. Añade un título y un enlace para una mejor navegación.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Paso 4: Definir los elementos de la tabla de contenidos

Defina los elementos (o encabezados) que se mostrarán en la tabla de contenidos. Estos elementos pueden ayudar a los lectores a navegar a secciones específicas del documento.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Paso 5: Crear títulos de tabla de contenidos

Crea encabezados para los dos primeros elementos de la tabla de contenidos. Estos encabezados se vincularán a sus respectivas páginas.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Paso 6: Guarda el PDF con la tabla de contenidos

Por último, guarde el archivo PDF actualizado.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Mensaje de confirmación

Muestra un mensaje de confirmación para que el usuario sepa que el proceso se ha completado.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Conclusión

Con Aspose.PDF para .NET, agregar una tabla de contenido a un PDF no solo es fácil, sino que también es personalizable. Ya sea que necesite crear enlaces de navegación simples o estructuras complejas, esta herramienta lo ayudará. Por lo tanto, la próxima vez que trabaje en un PDF extenso, no olvide agregar una tabla de contenido para darle un toque profesional.

## Preguntas frecuentes

### ¿Puedo personalizar la apariencia de la tabla de contenidos en Aspose.PDF?

Sí, puedes personalizar completamente la apariencia de la tabla de contenidos, incluido el estilo de fuente, el tamaño y la alineación.

### ¿Cómo agrego subtítulos a la tabla de contenidos?

 Puede agregar subtítulos ajustando el`Heading` nivel (por ejemplo,`Heading(2)`).

### ¿Es posible actualizar la tabla de contenidos automáticamente si el documento cambia?

No, la tabla de contenidos no se actualizará automáticamente. Deberá volver a crearla si cambia la estructura del documento.

### ¿Puedo vincular entradas de TOC a documentos externos?

Sí, puede utilizar hipervínculos para vincular entradas de TOC a archivos PDF o URL externos.

### ¿Aspose.PDF admite tablas de contenidos de varios niveles?

Sí, Aspose.PDF admite tablas de contenidos de varios niveles para documentos complejos con subsecciones.
