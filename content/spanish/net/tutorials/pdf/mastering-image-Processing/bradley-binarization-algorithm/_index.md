---
title: Algoritmo de binarización de Bradley
linktitle: Algoritmo de binarización de Bradley
second_title: Referencia de API de Aspose.PDF para .NET
description: Aprenda a convertir páginas PDF en imágenes TIFF binarias de alta calidad mediante el algoritmo de binarización Bradley en Aspose.PDF para .NET. Esta guía paso a paso incluye un ejemplo de código.
type: docs
weight: 30
url: /es/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Introducción

En este tutorial, lo guiaremos a través del proceso de conversión de una página PDF en una imagen TIFF mediante el algoritmo de binarización Bradley. Aspose.PDF para .NET simplifica esta tarea, lo que le permite automatizar y optimizar los flujos de trabajo de sus documentos con facilidad.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.PDF para .NET: Descargue la biblioteca desde[aquí](https://releases.aspose.com/pdf/net/).
- Visual Studio (o cualquier IDE de C#).
- Conocimientos básicos de C#.
-  Una licencia válida o una[licencia temporal](https://purchase.aspose.com/temporary-license/) De Aspose.

## Paso 1: Configura tu proyecto

Primero, crea un nuevo proyecto C# en tu IDE e importa los espacios de nombres necesarios:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Paso 2: Definir el directorio del documento

Especifique la ruta al directorio donde se encuentra su documento PDF, así como las rutas de salida para las imágenes TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Ruta a su archivo PDF
```

Este directorio almacenará tanto el PDF de origen como los archivos TIFF convertidos.

## Paso 3: Cargue el documento PDF

Abra el documento PDF que desea convertir:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Reemplazar`PageToTIFF.pdf` con el nombre de su archivo PDF.

## Paso 4: Especificar rutas de salida

Defina las rutas de salida para los archivos TIFF generados:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Paso 5: Establecer la resolución de la imagen

Establezca la resolución de las imágenes TIFF. Cuanto mayor sea el DPI, mejor será la calidad de la imagen:

```csharp
Resolution resolution = new Resolution(300);
```

## Paso 6: Configurar los ajustes TIFF

Configure los ajustes de la imagen TIFF, incluida la compresión y la profundidad de color:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

El uso de 1bpp (1 bit por píxel) prepara la imagen para la salida binaria.

## Paso 7: Crear el dispositivo TIFF

Cree un dispositivo TIFF que manejará la conversión:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Paso 8: Convertir la página PDF a TIFF

Convierte la primera página del PDF en una imagen TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Paso 9: Aplicar el algoritmo de binarización de Bradley

Ahora, aplique el algoritmo Bradley para convertir la imagen TIFF en escala de grises en una imagen binaria:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 El`BinarizeBradley` El método utiliza dos flujos de archivos (entrada y salida) y un valor umbral. Ajuste el umbral según sea necesario para obtener resultados óptimos.

## Paso 10: Confirmar conversión exitosa

Por último, confirme que la conversión se realizó correctamente:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Conclusión

¡Felicitaciones! Ha convertido con éxito una página PDF en una imagen TIFF y ha aplicado el algoritmo de binarización Bradley con Aspose.PDF para .NET. Este proceso es esencial para el archivado de documentos, el reconocimiento óptico de caracteres (OCR) y otras aplicaciones profesionales. Con una resolución de alta calidad y una compresión eficiente, las imágenes de sus documentos serán claras y de tamaño manejable.

## Preguntas frecuentes

### ¿Qué es el algoritmo de Bradley?
El algoritmo Bradley es una técnica de binarización que convierte imágenes en escala de grises en imágenes binarias determinando un umbral adaptativo para cada píxel en función de su entorno.

### ¿Puedo convertir varias páginas PDF a TIFF usando este método?
 Sí, puedes modificar el`Process` método para recorrer todas las páginas del documento para la conversión.

### ¿Cuál es la resolución óptima para convertir archivos PDF a TIFF?
Generalmente se recomienda una resolución de 300 DPI para imágenes de alta calidad, pero puedes ajustarla según tus necesidades específicas.

### ¿Qué significa 1bpp en profundidad de color?
1bpp (1 bit por píxel) indica que la imagen será en blanco y negro, y que cada píxel será completamente negro o completamente blanco.

### ¿Es el algoritmo Bradley adecuado para OCR?
Sí, el algoritmo Bradley se utiliza a menudo en el preprocesamiento de OCR porque mejora el contraste del texto en los documentos escaneados, mejorando la precisión del reconocimiento.