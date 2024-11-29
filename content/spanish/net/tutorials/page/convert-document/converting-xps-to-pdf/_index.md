---
title: Conversión de XPS a PDF con Aspose.Page para .NET
linktitle: Conversión de XPS a PDF
second_title: API de Aspose.Page .NET
description: Descubra cómo convertir sin problemas documentos XPS (XML Paper Specification) a PDF (Portable Document Format) utilizando la potente biblioteca Aspose.Page para .NET.
type: docs
weight: 11
url: /es/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introducción

En este tutorial, exploraremos cómo convertir documentos XPS (XML Paper Specification) a PDF (Portable Document Format) utilizando la versátil biblioteca Aspose.Page para .NET. Esta potente biblioteca simplifica la conversión de documentos y ofrece varias opciones de personalización, lo que la convierte en una excelente opción para los desarrolladores.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente en su lugar:

-  Biblioteca Aspose.Page para .NET: Descargue e instale la biblioteca Aspose.Page para .NET desde[Documentación de Aspose.Page](https://reference.aspose.com/page/net/).
  
- Entorno de desarrollo: configure un entorno de desarrollo .NET utilizando Visual Studio u otro IDE compatible.

- Documento XPS: Tenga listo el archivo XPS que desea convertir, almacenado en un directorio designado.

## Paso 1: Importar los espacios de nombres necesarios

Comience importando el espacio de nombres necesario para acceder a las funcionalidades de Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Paso 2: Inicializar el directorio de documentos

Define la ruta del directorio donde se almacenan tus documentos:

```csharp
string dataDir = "Your Document Directory";
```

 Asegúrese de reemplazar`"Your Document Directory"` con la ruta real al directorio que contiene su documento XPS.

### Paso 3: Abra secuencias de PDF y XPS

A continuación, inicialice las transmisiones tanto para el archivo XPS de entrada como para el archivo PDF de salida:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Asegúrese de tener la ruta correcta configurada para sus archivos.

### Paso 4: Cargue el documento XPS

Ahora, cargue su documento XPS usando la biblioteca Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Paso 5: Configurar las opciones para guardar PDF

Configure las opciones de guardado para su PDF, incluidos los parámetros de compresión y calidad de imagen:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Establecer el nivel de calidad JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Utilice compresión JPEG para imágenes
    TextCompression = PdfTextCompression.Flate, // Aplicar compresión Flate para texto
    PageNumbers = new int[] { 1, 2, 6 } // Especifique los números de página que desea incluir
};
```

Siéntase libre de ajustar estos parámetros según sus necesidades.

### Paso 6: Crear el dispositivo de renderizado de PDF

Crear un dispositivo de renderizado para el formato PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Paso 7: Guarde el documento como PDF

Por último, guarde el documento XPS en PDF utilizando el dispositivo y las opciones especificadas:

```csharp
document.Save(device, options);
```

## Conclusión

¡Felicitaciones! Ha convertido exitosamente un documento XPS a PDF usando Aspose.Page para .NET. Esta biblioteca no solo simplifica la conversión de documentos, sino que también ofrece amplias capacidades para manejar varios formatos.

## Preguntas frecuentes

### ¿Puedo convertir varios archivos XPS en un solo PDF?

¡Por supuesto! Puedes iterar a través de varios archivos XPS y fusionarlos en un solo documento PDF siguiendo los mismos pasos de conversión.

### ¿Qué otros formatos de salida admite Aspose.Page para .NET?

Además de PDF, Aspose.Page para .NET admite una variedad de formatos, incluidos TIFF, JPEG y PNG.

### ¿Cómo puedo personalizar la apariencia del PDF convertido?

 Puede ajustar los parámetros en el`PdfSaveOptions` objeto, como la calidad JPEG y la configuración de compresión, para lograr la apariencia deseada.

### ¿Hay una versión de prueba disponible para Aspose.Page para .NET?

 Sí, puedes probar Aspose.Page para .NET con una versión de prueba gratuita disponible[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar soporte de la comunidad para Aspose.Page para .NET?

Para discusiones y soporte de la comunidad, visite el[Foro de Aspose.Page](https://forum.aspose.com/c/page/39).