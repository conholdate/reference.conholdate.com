---
title: Convertir DGN a PDF en Aspose.CAD para .NET
linktitle: Convertir DGN a PDF en Aspose.CAD para .NET
second_title: Aspose.CAD .NET formato de archivo CAD y BIM
description: Aprenda a convertir archivos DGN a PDF sin esfuerzo utilizando la potente biblioteca Aspose.CAD para .NET. Esta guía paso a paso está diseñada para desarrolladores de todos los niveles.
type: docs
weight: 12
url: /es/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Introducción

Navegar por el mundo de los archivos CAD puede ser un desafío, pero con Aspose.CAD para .NET, los desarrolladores pueden manipular y convertir fácilmente varios formatos CAD. Una necesidad común es convertir archivos DGN a PDF, que exploraremos paso a paso en este tutorial.

## Prerrequisitos

Para seguir, asegúrese de tener lo siguiente:

- Conocimiento básico de C# y el framework .NET.
-  Biblioteca Aspose.CAD para .NET instalada. Puedes descargarla[aquí](https://releases.aspose.com/cad/net/).
- Un archivo DGN de muestra (por ejemplo, Nikon_D90_Camera.dgn). 

## Paso 1: Importar los espacios de nombres necesarios

Comience importando los espacios de nombres relevantes en su proyecto C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Paso 2: Cargue el archivo DGN

Especifique el directorio para su archivo DGN y cárguelo usando el siguiente código:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Aquí se realizará un procesamiento adicional...
}
```

## Paso 3: Configurar las opciones de rasterización

A continuación, configure las opciones de rasterización para definir cómo se representará su DGN en el PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Ajuste el ancho según sea necesario
    PageHeight = 300, // Ajuste la altura según sea necesario
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Paso 4: Crear opciones de PDF

Defina las opciones de PDF, integrando las configuraciones de rasterización configuradas anteriormente:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Paso 5: Guarda el DGN como PDF

Por último, guarda el archivo DGN como PDF utilizando las opciones que hayas configurado:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Conclusión

¡Felicitaciones! Ha convertido exitosamente un archivo DGN en un PDF usando Aspose.CAD para .NET. Este sencillo tutorial lo guió a través del proceso de cargar el archivo DGN, configurar las opciones de rasterización y guardar el resultado como PDF.

## Preguntas frecuentes

### ¿Necesito conocimientos previos de CAD para utilizar Aspose.CAD?  
¡Por supuesto! Aspose.CAD está diseñado para simplificar tareas CAD complejas, haciéndolo accesible para todos los desarrolladores, independientemente de sus conocimientos de CAD.

### ¿Dónde puedo encontrar más recursos y documentación para Aspose.CAD?  
 Puede explorar guías y ejemplos completos en el[Documentación de Aspose.CAD](https://reference.aspose.com/cad/net/).

### ¿Hay una prueba gratuita disponible para Aspose.CAD?  
 Sí, se puede obtener una prueba gratuita.[aquí](https://releases.aspose.com/).

### ¿Cómo puedo obtener una licencia temporal para Aspose.CAD?  
 Puedes solicitar licencias temporales[aquí](https://purchase.conholdate.com/temporary-license/).

### ¿Necesita ayuda o tiene preguntas?  
Únase a la conversación en el[Foro de Aspose.CAD](https://forum.aspose.com/c/cad/19) Para apoyo y consultas de la comunidad.