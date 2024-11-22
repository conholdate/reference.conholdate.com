---
title: Cómo guardar documentos de OneNote en formato PDF con Aspose.Note para .NET
linktitle: Cómo guardar documentos de OneNote en formato PDF
second_title: API de Aspose.Note .NET
description: Aprenda a guardar de manera eficiente documentos de Microsoft OneNote como archivos PDF con Aspose.Note para .NET. Esta guía le indica los requisitos previos necesarios y ofrece preguntas frecuentes útiles.
type: docs
weight: 26
url: /es/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Introducción

En este tutorial, exploraremos cómo guardar documentos en formato PDF con Aspose.Note para .NET. Aspose.Note es una potente biblioteca que permite a los desarrolladores trabajar con archivos de Microsoft OneNote de forma programada. Cubriremos los requisitos previos, importaremos espacios de nombres y proporcionaremos guías paso a paso para guardar documentos en formato PDF en varios diseños de página.

## Prerrequisitos
1. Visual Studio: asegúrese de que esté instalado.
2. Aspose.Note para .NET: Descargue e instale la biblioteca.
3. Conocimiento de C#: Se requiere comprensión básica del lenguaje.

## Importación de los espacios de nombres necesarios
Antes de continuar, importe los siguientes espacios de nombres en su código:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Paso 1: Guardar en formato PDF con la configuración de la página de la carta
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Actualizar esta ruta
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Carga el documento de OneNote y lo guarda como PDF usando configuraciones de página de tamaño carta.

## Paso 2: Guardar en PDF con configuración de página A4 (sin límite de altura)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Actualizar esta ruta
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Similar al paso 1, pero utiliza configuraciones de página A4 sin limitaciones de altura.

## Conclusión
El tutorial demuestra con éxito cómo convertir archivos de OneNote a formato PDF con Aspose.Note. Al utilizar diferentes configuraciones de página, los desarrolladores ganan flexibilidad en la gestión de documentos.

## Preguntas frecuentes
### ¿Puede Aspose.Note manejar archivos complejos de OneNote?
Sí, maneja eficazmente varias funciones de archivos complejos de OneNote.

### ¿Aspose.Note es adecuado para proyectos comerciales?
Sí, puedes usarlo para aplicaciones comerciales después de comprar una licencia.

### ¿Aspose.Note ofrece una prueba gratuita?
Sí, hay una prueba gratuita disponible para explorar.

### ¿Dónde puedo encontrar documentación para Aspose.Note?
La documentación detallada está disponible en el sitio de referencia de Aspose.

### ¿Necesita más ayuda?
Para preguntas y soporte, consulte el foro Aspose.Note.
