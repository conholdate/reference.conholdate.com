---
title: Creación de un hipervínculo local en un archivo PDF
linktitle: Creación de un hipervínculo local en un archivo PDF
second_title: Referencia de API de Aspose.PDF para .NET
description: Descubra cómo mejorar la navegación en sus documentos PDF mediante la creación de hipervínculos locales con Aspose.PDF para .NET. Este tutorial paso a paso le guiará a través de todo el proceso.
type: docs
weight: 40
url: /es/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Introducción

En esta guía, le explicaremos el proceso de creación de hipervínculos locales en un archivo PDF con Aspose.PDF para .NET. Desglosaremos cada paso con claridad, para garantizar que, incluso si no tiene experiencia en la manipulación de archivos PDF, pueda seguir el proceso sin esfuerzo.

## Prerrequisitos

Antes de sumergirse en el código, asegúrese de tener lo siguiente:

1.  Visual Studio: Descárguelo desde[Sitio web de Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF para .NET: Descargue la biblioteca a través de[Sitio web de Aspose](https://releases.aspose.com/pdf/net/)Esta biblioteca proporciona un amplio conjunto de funciones para la manipulación de PDF.
3. Conocimientos básicos de C#: Estar familiarizado con la programación en C# será de ayuda, pero no te preocupes; te explicaremos el código línea por línea.
4. .NET Framework: asegúrese de tener instalado .NET Framework en su equipo. Consulte los requisitos en Aspose.PDF[documentación](https://reference.aspose.com/pdf/net/).

¡Con estos requisitos previos establecidos, ya está listo para aprender a crear hipervínculos locales en sus documentos PDF!

## Importación de paquetes necesarios

Ahora que ya está todo configurado, es momento de importar los paquetes necesarios a su proyecto C#.

### Abra su proyecto

Abra su proyecto .NET existente o cree uno nuevo en Visual Studio. Si está comenzando desde cero, seleccione “Crear un nuevo proyecto” en la pantalla de inicio.

### Agregar referencia a Aspose.PDF

 Haga clic con el botón derecho en "Dependencias" en la carpeta de su proyecto en el Explorador de soluciones. Seleccione "Administrar paquetes NuGet", busque`Aspose.PDF`, e instala la última versión disponible. Esto te proporcionará todas las herramientas que necesitas para crear y manipular archivos PDF.

### Importar espacios de nombres

En la parte superior de su archivo .cs, agregue las siguientes directivas using:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Estas directivas le permiten acceder a las funciones de la biblioteca sin problemas.

Dividamos el proceso de creación de hipervínculos locales en pasos simples.

## Paso 1: Configurar la instancia del documento

 Crear una nueva instancia de la`Document` clase, que representa el archivo PDF con el que trabajará.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Establezca su directorio de documentos
Document doc = new Document(); //Crear instancia de documento
```

 Reemplazar`"YOUR_DOCUMENT_DIRECTORY"` con la ruta real en su sistema donde se guardará el PDF.

## Paso 2: Agregar una página al documento

A continuación, agregue una página a su documento PDF.

```csharp
Page page = doc.Pages.Add(); // Agregar una nueva página
```

Esta línea agrega una nueva página al documento, donde se colocará todo su contenido.

## Paso 3: Crear un fragmento de texto

Ahora, vamos a crear un fragmento de texto que actuará como un enlace en el que se puede hacer clic.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Crear un fragmento de texto
```

 Este`TextFragment` Mostrará el texto en el que los usuarios pueden hacer clic.

## Paso 4: Crear un hipervínculo local

Ahora, crea un hipervínculo local que apunte a la página 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Crear un hipervínculo local
link.TargetPageNumber = 7; // Establecer la página de destino para el enlace
text.Hyperlink = link; // Establecer el hipervínculo para el fragmento de texto
```

 El`LocalHyperlink` La clase le permite especificar el número de página de destino para el hipervínculo.

## Paso 5: Agrega el fragmento de texto a la página

Añade el texto en el que se puede hacer clic a la página que has creado.

```csharp
page.Paragraphs.Add(text); // Añade el fragmento de texto a la página
```

Esta línea agrega su texto a la colección de párrafos de la página.

## Paso 6: Crea otro fragmento de texto (opcional)

Agreguemos otro hipervínculo para regresar a la página 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Crear un nuevo fragmento de texto
textBack.IsInNewPage = true; // Indica que debe estar en una nueva página.
```

## Paso 7: Configurar el segundo hipervínculo local

Crear otro hipervínculo local para la página 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Crear otro hipervínculo local
linkBack.TargetPageNumber = 1; // Establecer la página de destino para el segundo hipervínculo
textBack.Hyperlink = linkBack; // Establecer el hipervínculo para el segundo fragmento de texto
```

## Paso 8: Agrega el segundo fragmento de texto a la nueva página

Añade el segundo fragmento de texto a su página.

```csharp
Page newPage = doc.Pages.Add(); // Agregar una nueva página para el segundo enlace
newPage.Paragraphs.Add(textBack); // Añade el fragmento de texto a la nueva página
```

## Paso 9: Guardar el documento

Por último, guarde su documento.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Especificar el nombre del archivo de salida
doc.Save(dataDir); // Guardar el documento actualizado
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Esta línea combina la ruta de su directorio con el nombre del archivo y el`Save()` El método guarda su documento.

## Conclusión

La creación de hipervínculos locales en archivos PDF mediante Aspose.PDF para .NET es una función práctica que mejora la navegación y la experiencia del usuario. Ahora tiene el conocimiento para guiar a sus lectores directamente a la información que necesitan, lo que hace que sus archivos PDF sean más interactivos y fáciles de usar.

## Preguntas frecuentes

### ¿Qué es Aspose.PDF para .NET?
Aspose.PDF para .NET es una biblioteca que permite a los desarrolladores crear, manipular y convertir documentos PDF mediante programación utilizando el marco .NET.

### ¿Puedo crear hipervínculos a páginas web externas?
Sí, Aspose.PDF también admite la creación de hipervínculos a URL externas además de hipervínculos locales dentro del PDF.

### ¿Existe una prueba gratuita de Aspose.PDF?
 ¡Por supuesto! Puedes acceder a la prueba gratuita desde el[Sitio web de Aspose](https://releases.aspose.com/).

### ¿Qué lenguajes de programación admite Aspose?
Aspose ofrece bibliotecas para varios lenguajes de programación, incluidos Java, C++, y Python, entre otros.

### ¿Cómo puedo obtener soporte para los productos Aspose?
 Puede buscar ayuda a través de[Foro de Aspose](https://forum.aspose.com/c/pdf/10).