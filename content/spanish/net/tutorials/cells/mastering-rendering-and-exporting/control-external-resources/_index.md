---
title: Controle recursos externos con Aspose.Cells para .NET
linktitle: Controle recursos externos con Aspose.Cells para .NET
second_title: API de procesamiento de Excel Aspose.Cells .NET
description: Desbloquee todo el potencial de sus conversiones de Excel a PDF con Aspose.Cells para .NET. En esta guía completa, aprenda a administrar recursos externos, como imágenes, para garantizar que sus archivos PDF reflejen sus requisitos de formato exactos.
type: docs
weight: 12
url: /es/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Introducción

En el panorama digital actual, convertir hojas de cálculo de Excel a documentos PDF es una tarea común y esencial. Ya sea que esté preparando informes, datos financieros o materiales de presentación, es fundamental asegurarse de que sus archivos PDF reflejen el formato deseado. Aspose.Cells para .NET ofrece una potente biblioteca que le permite controlar este proceso de conversión en detalle, especialmente cuando se trata de recursos externos como imágenes. En esta guía, exploraremos cómo administrar de manera eficaz los recursos externos durante el proceso de conversión de Excel a PDF con Aspose.Cells. ¡Vamos a profundizar!

## Prerrequisitos

Antes de comenzar, asegúrese de tener listo lo siguiente:

1. Visual Studio o cualquier IDE compatible con .NET: este será su entorno de desarrollo.
2.  Aspose.Cells para .NET: Si aún no lo ha instalado, visite el sitio[Descargas de Aspose](https://releases.aspose.com/cells/net/) página para obtener la última versión.
3. Conocimientos básicos de C#: será de gran utilidad estar familiarizado con C#. Si necesita aclaraciones sobre algún concepto, no dude en consultarlo.
4. Archivo de Excel de muestra: prepare un archivo de Excel, como "samplePdfSaveOptions_StreamProvider.xlsx", que contenga los recursos externos que desea convertir.
5. Archivo de imagen para prueba: utilice un archivo de imagen como "newPdfSaveOptions_StreamProvider.png" como recurso externo durante la conversión.

## Importar paquetes necesarios

Para comenzar, deberá importar los espacios de nombres necesarios de la biblioteca Aspose.Cells. Agregue las siguientes directivas using en la parte superior de su archivo C#:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Estos espacios de nombres proporcionan las clases y métodos esenciales para sus tareas.

## Paso 1: Crear una clase de proveedor de transmisión

 Primero, cree una clase de proveedor de transmisión que implemente el`IStreamProvider` Interfaz. Esta clase le permitirá controlar cómo se cargan los recursos externos.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Cargar la imagen en un flujo de memoria
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: este método se llama cuando se cierra la transmisión y actualmente se registra un mensaje de depuración.
- InitStream: este método lee el archivo de imagen externo como una matriz de bytes, lo convierte en un flujo de memoria y lo asigna a la`options.Stream` propiedad.

## Paso 2: Configurar los directorios de origen y salida

A continuación, defina los directorios para su archivo Excel y el PDF de salida.

```csharp
// Directorio de fuentes
string sourceDir = "Your Document Directory";
// Directorio de salida
string outputDir = "Your Document Directory";
```

 Reemplazar`"Your Document Directory"` con la ruta real en su sistema donde se encuentran sus archivos.

## Paso 3: Cargue su archivo Excel

Ahora, cargue el archivo Excel desde el cual desea crear el PDF.

```csharp
// Cargue el archivo Excel de origen que contiene imágenes externas
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 El`Workbook` La clase de Aspose.Cells representa su archivo Excel, que puede incluir varios recursos externos como imágenes.

## Paso 4: Establecer las opciones para guardar el PDF

Antes de guardar el libro de trabajo como PDF, especifique las opciones de guardado deseadas.

```csharp
// Especificar opciones de guardado de PDF - Proveedor de transmisión
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Guarda cada hoja en una nueva página
};
```

 Esto crea una instancia de`PdfSaveOptions` , lo que le permite personalizar el formato PDF.`OnePagePerSheet` Esta opción garantiza que cada hoja de Excel aparezca en una página separada en el PDF final.

## Paso 5: Asigna tu proveedor de transmisión

 Conecta tu`Workbook` instancia con el`MyStreamProvider` clase que creaste anteriormente.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Esta línea garantiza que siempre que se encuentren recursos externos durante la conversión, su proveedor personalizado los gestionará en consecuencia.

## Paso 6: Guarde el libro de trabajo como PDF

Ahora, guarde su libro de Excel como PDF.

```csharp
// Guardar el libro de trabajo en formato PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Al llamar al`Save` Al utilizar el método en el objeto del libro de trabajo y pasar el directorio de salida junto con las opciones de PDF, convierte el archivo de Excel en un PDF bien formateado.

## Paso 7: Confirmar ejecución exitosa

Por último, es una buena práctica confirmar que el proceso se completó exitosamente.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Este mensaje le informará sobre el estado de su operación, proporcionándole retroalimentación útil.

## Conclusión

¡Ya domina el proceso de control de recursos externos durante las conversiones de Excel a PDF con Aspose.Cells! Si sigue estos pasos, podrá asegurarse de que sus documentos incluyan imágenes y otros elementos externos de forma precisa, lo que dará como resultado un producto final impecable en todo momento.

## Preguntas frecuentes

### ¿Qué es Aspose.Cells?
Aspose.Cells es una potente biblioteca para desarrolladores .NET que permite la creación, manipulación, conversión y representación de archivos Excel en varios formatos.

### ¿Cómo descargo Aspose.Cells?
 Puede descargar la última versión desde[Enlace de descarga](https://releases.aspose.com/cells/net/).

### ¿Puedo probar Aspose.Cells gratis?
 ¡Sí! Puedes acceder a una prueba gratuita visitando el sitio[Página de prueba gratuita](https://releases.aspose.com/).

### ¿Dónde puedo encontrar soporte para Aspose.Cells?
 Para consultas relacionadas con soporte, visite el[Foro de soporte de Aspose](https://forum.aspose.com/c/cells/9).

### ¿Cómo puedo obtener una licencia temporal para Aspose.Cells?
 Puede solicitar una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).
