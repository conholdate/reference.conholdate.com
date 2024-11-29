---
title: Guía para firmar archivos PDF con metadatos mediante GroupDocs.Signature
linktitle: Guía para firmar archivos PDF con metadatos
second_title: API .NET de GroupDocs.Signature
description: Aprenda a reforzar sus documentos PDF con seguridad y trazabilidad mejoradas firmándolos con metadatos mediante GroupDocs.Signature para .NET. Este tutorial completo ofrece una explicación clara.
type: docs
weight: 11
url: /es/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Introducción

En este tutorial, aprenderemos a firmar un documento PDF y a agregar metadatos mediante GroupDocs.Signature para .NET. Agregar metadatos mejora el documento al brindar información esencial, como la autoría, la fecha de creación, el ID del documento y más.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  GroupDocs.Signature para .NET: Descárguelo desde[aquí](https://releases.groupdocs.com/signature/net/).
2. Un documento PDF: Tenga un archivo PDF de muestra listo para firmar.
3. Conocimientos básicos de programación en C#: es necesario estar familiarizado con la sintaxis de C# para comprender los ejemplos de código.

## Importar espacios de nombres

Comience importando los espacios de nombres necesarios para acceder a las clases y métodos necesarios:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Paso 1: Cargue el documento PDF

Especifique la ruta del documento PDF que desea firmar:

```csharp
string filePath = "sample.pdf";
```

## Paso 2: Especifique la ruta del archivo de salida

Define dónde se guardará el PDF firmado con metadatos:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Paso 3: Crear una instancia de firma

 Inicializar un`Signature` instancia con la ruta al documento PDF:

```csharp
using (Signature signature = new Signature(filePath))
{
    // El código relacionado con la firma irá aquí
}
```

## Paso 4: Definir las opciones de metadatos

 Crear`MetadataSignOptions` y agregue los campos de metadatos junto con sus valores:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Valor de cadena
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // Valor de fecha y hora
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Valor entero
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Doble valor
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Valor decimal
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Valor flotante
```

## Paso 5: Firma el documento

Firme el documento PDF con las opciones de metadatos especificadas y guarde el documento firmado:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Conclusión

En este tutorial, explicamos cómo firmar un documento PDF con metadatos mediante GroupDocs.Signature para .NET. Si sigue estos pasos, podrá enriquecer fácilmente sus archivos PDF con metadatos valiosos, lo que mejorará su trazabilidad y utilidad.

## Preguntas frecuentes

### ¿Puedo agregar campos de metadatos personalizados a mis documentos PDF?

Sí, puede agregar campos de metadatos personalizados especificando el nombre del campo y su valor correspondiente mediante GroupDocs.Signature para .NET.

### ¿GroupDocs.Signature para .NET es compatible con todas las versiones de .NET Framework?

GroupDocs.Signature para .NET es compatible con varias versiones de .NET Framework, lo que garantiza flexibilidad y facilidad de integración.

### ¿GroupDocs.Signature admite la firma de otros formatos de documentos además de PDF?

Sí, GroupDocs.Signature admite una amplia gama de formatos de documentos, incluidos Word, Excel, PowerPoint y más.

### ¿Puedo firmar varios documentos de forma masiva utilizando GroupDocs.Signature para .NET?

¡Por supuesto! Puedes firmar varios documentos en bloque iterando a través de una lista de archivos y aplicando el proceso de firma de forma programada.

### ¿Hay soporte técnico disponible para los usuarios de GroupDocs.Signature?

Sí, GroupDocs ofrece soporte técnico especializado a través de sus foros. Puede acceder al foro de soporte[aquí](https://forum.groupdocs.com/c/signature/13).