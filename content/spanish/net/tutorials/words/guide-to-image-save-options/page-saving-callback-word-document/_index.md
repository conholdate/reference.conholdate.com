---
title: Retrollamada para guardar páginas en documentos de Word
linktitle: Retrollamada para guardar páginas en documentos de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a convertir fácilmente cada página de un documento de Word en imágenes PNG individuales mediante Aspose.Words para .NET. Esta guía proporciona instrucciones paso a paso, incluidos ejemplos de código.
type: docs
weight: 10
url: /es/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Introducción

¿Alguna vez ha tenido que convertir cada página de un documento de Word en imágenes individuales? Ya sea que desee crear miniaturas para una vista previa o dividir un informe extenso en elementos visuales fáciles de entender, Aspose.Words para .NET hace que esta tarea sea sencilla y eficiente. En esta guía, lo guiaremos a través del proceso de configuración de una devolución de llamada para guardar páginas y guardar cada página de su documento como una imagen PNG. ¡Comencemos!

## Prerrequisitos

Antes de sumergirte, asegúrate de tener lo siguiente:

1.  Aspose.Words para .NET: Descárguelo e instálelo desde[aquí](https://releases.aspose.com/words/net/).
2. Visual Studio: cualquier versión funcionará, pero usaremos Visual Studio 2019 para esta guía.
3. Conocimientos básicos de C#: estar familiarizado con C# le ayudará a seguir el proceso sin problemas.

## Paso 1: Importar los espacios de nombres necesarios

Primero, debemos importar los espacios de nombres necesarios. Esto nos permite acceder a las clases y métodos necesarios sin tener que escribir el espacio de nombres completo cada vez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 2: Defina su directorio de documentos

A continuación, establezca la ruta al directorio de documentos. Aquí se encuentra el documento de Word de entrada y donde se guardarán las imágenes de salida.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 3: Cargue su documento

Ahora, carguemos el documento que desea procesar. Asegúrese de que el documento, llamado "Rendering.docx", se encuentre en el directorio especificado.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 4: Configurar las opciones para guardar imágenes

Configuraremos las opciones para guardar imágenes, especificando que queremos guardar las páginas como archivos PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Aquí,`PageSet` define el rango de páginas a guardar, y`PageSavingCallback` apunta a nuestra clase de devolución de llamada personalizada.

## Paso 5: Implementar la devolución de llamada para guardar la página

Ahora, necesitamos implementar la clase de devolución de llamada que maneja cómo se guarda cada página.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Esta clase implementa el`IPageSavingCallback` interfaz. En el`PageSaving` método, especificamos el patrón de nombres para cada página guardada.

## Paso 6: Guardar el documento como imágenes

Por último, guardamos el documento utilizando las opciones configuradas.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusión

¡Felicitaciones! Ha configurado correctamente una devolución de llamada para guardar páginas y guardar cada página de un documento de Word como una imagen PNG independiente mediante Aspose.Words para .NET. Esta técnica es increíblemente útil para diversas aplicaciones, desde la creación de vistas previas de páginas hasta la generación de imágenes de páginas individuales para informes.

## Preguntas frecuentes

### ¿Puedo guardar páginas en formatos distintos a PNG?
 ¡Sí! Puede guardar páginas en formatos como JPEG, BMP y TIFF cambiando el`SaveFormat` en`ImageSaveOptions`.

### ¿Cómo puedo guardar sólo páginas específicas?
 Para guardar páginas específicas, ajuste la`PageSet` parámetro en`ImageSaveOptions` para incluir sólo las páginas deseadas.

### ¿Es posible personalizar la calidad de la imagen?
 ¡Por supuesto! Puedes controlar la calidad de la imagen de salida configurando propiedades como`ImageSaveOptions.JpegQuality`.

### ¿Cómo puedo gestionar eficazmente documentos de gran tamaño?
Para documentos grandes, considere procesar páginas en lotes para administrar el uso de memoria de manera efectiva.

### ¿Dónde puedo encontrar más información sobre Aspose.Words para .NET?
 Para obtener guías y ejemplos completos, consulte[Documentación de Aspose.Words](https://reference.aspose.com/words/net/).