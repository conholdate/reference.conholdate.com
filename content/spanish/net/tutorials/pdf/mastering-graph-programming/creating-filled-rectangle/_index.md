---
title: Creando un rectángulo relleno
linktitle: Creando un rectángulo relleno
second_title: Referencia de API de Aspose.PDF para .NET
description: Descubra el poder de la manipulación de archivos PDF con Aspose.PDF para .NET en este tutorial paso a paso. Aprenda a crear mediante programación documentos PDF visualmente atractivos dibujando rectángulos rellenos.
type: docs
weight: 50
url: /es/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introducción

¿Alguna vez has deseado crear archivos PDF visualmente impactantes mediante programación? Si es así, ¡estás en el lugar correcto! En este tutorial, exploraremos Aspose.PDF para .NET, una potente biblioteca que simplifica la manipulación de documentos PDF. Hoy, nos centraremos en la creación de un rectángulo relleno dentro de un archivo PDF. Ya seas un desarrollador experimentado o recién estés comenzando, esta guía te guiará por cada paso de una manera amigable y atractiva. ¡Así que, ponte a programar y comencemos!

## Prerrequisitos

Antes de sumergirnos en el código, asegúrese de tener lo siguiente:

1. Visual Studio: instale Visual Studio en su máquina, ya que es un excelente IDE para el desarrollo .NET.
2. Aspose.PDF para .NET: Descargue e instale la biblioteca Aspose.PDF desde[aquí](https://releases.aspose.com/pdf/net/).
3. Conocimientos básicos de C#: la familiaridad con la programación en C# le ayudará a comprender mejor los fragmentos de código.

## Paso 1: Crear un nuevo proyecto

1. Abra Visual Studio y cree un nuevo proyecto de aplicación de consola.
2. Ponle un nombre apropiado a tu proyecto.

## Paso 2: Agregar referencia de Aspose.PDF

1. Haga clic derecho en su proyecto en el Explorador de soluciones.
2. Seleccione Administrar paquetes NuGet.
3. Busque Aspose.PDF e instale la última versión.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Ahora que tenemos todo configurado, ¡profundicemos en el código!

## Paso 3: Configura tu directorio de documentos

Especifique la ruta donde se guardará su PDF:

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real en su máquina donde desea guardar el PDF.

## Paso 4: Crear una instancia de documento

Inicializar un nuevo documento PDF:

```csharp
//Crear instancia de documento
Document doc = new Document();
```

## Paso 5: Agregar una página al documento

Todo PDF necesita al menos una página. Agreguemos una:

```csharp
// Agregar página a la colección de páginas del archivo PDF
Page page = doc.Pages.Add();
```

## Paso 6: Crear una instancia de gráfico

 A`Graph` La instancia actúa como un lienzo para dibujar formas:

```csharp
// Crear una instancia de Graph
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Paso 7: Agrega el gráfico a la página

Adjunte el gráfico a la página:

```csharp
// Agregar objeto gráfico a la colección de párrafos de una instancia de página
page.Paragraphs.Add(graph);
```

## Paso 8: Crear una instancia de rectángulo

Define la posición y el tamaño del rectángulo:

```csharp
// Crear una instancia de Rectángulo
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Paso 9: Especifique el color de relleno

Elige un color para el rectángulo. En este ejemplo, utilizaremos el rojo:

```csharp
// Especificar el color de relleno para el objeto gráfico
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Paso 10: Agrega el rectángulo al gráfico

Añade el rectángulo al gráfico:

```csharp
// Agregar objeto rectángulo a la colección de formas del objeto Gráfico
graph.Shapes.Add(rect);
```

## Paso 11: Guarde el documento PDF

Por último, guarde el documento en el directorio especificado:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Guardar archivo PDF
doc.Save(dataDir);
```

## Paso 12: Mensaje de confirmación

Imprima un mensaje de confirmación para indicar el éxito:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusión

¡Felicitaciones! Ha creado exitosamente un rectángulo relleno en un documento PDF usando Aspose.PDF para .NET. Esta poderosa biblioteca abre un mundo de posibilidades para la manipulación de PDF, permitiéndole generar documentos asombrosos mediante programación. Ya sea que esté creando informes, facturas o cualquier otro tipo de PDF, Aspose.PDF lo tiene cubierto.

## Preguntas frecuentes

### ¿Qué es Aspose.PDF para .NET?
Aspose.PDF para .NET es una biblioteca que permite a los desarrolladores crear, manipular y convertir documentos PDF mediante programación.

### ¿Puedo utilizar Aspose.PDF gratis?
 Sí, Aspose ofrece una versión de prueba gratuita que puedes usar para explorar las funciones de la biblioteca. Puedes descargarla[aquí](https://releases.aspose.com/).

### ¿Hay alguna forma de obtener soporte para Aspose.PDF?
 ¡Por supuesto! Puedes obtener ayuda a través del foro de Aspose[aquí](https://forum.aspose.com/c/pdf/10).

### ¿Cómo puedo comprar Aspose.PDF?
 Puedes comprar Aspose.PDF visitando la página de compra[aquí](https://purchase.aspose.com/buy).

### ¿Qué tipos de formas puedo crear con Aspose.PDF?
Puede crear varias formas, incluidos rectángulos, círculos, líneas y más, utilizando la biblioteca Aspose.PDF.