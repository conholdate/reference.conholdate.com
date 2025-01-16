---
title: Extraer audio de hipervínculos en PowerPoint con Aspose.Slides
linktitle: Extraer audio de hipervínculos
second_title: API de procesamiento de PowerPoint Aspose.Slides .NET
description: Aprenda a extraer audio de hipervínculos en presentaciones de PowerPoint con Aspose.Slides para .NET. Esta guía paso a paso ofrece instrucciones claras.
type: docs
weight: 12
url: /es/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Introducción

En las presentaciones multimedia, el audio mejora significativamente el impacto de las diapositivas. Si alguna vez ha visto una presentación de PowerPoint con hipervínculos de audio y se ha preguntado cómo extraer ese audio para otros usos, está en el lugar correcto. Esta guía le guiará a través del proceso de extracción de audio de hipervínculos en una presentación de PowerPoint utilizando la biblioteca Aspose.Slides para .NET.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

### Biblioteca Aspose.Slides para .NET

 Asegúrese de tener instalada la biblioteca Aspose.Slides para .NET. Si aún no lo ha hecho, puede descargarla desde[Documentación de Aspose.Slides para .NET](https://reference.aspose.com/slides/net/).

### Presentación de PowerPoint con hipervínculos de audio

Necesitará una presentación de PowerPoint (PPTX) que contenga hipervínculos con audio asociado. Esta presentación será su fuente para la extracción de audio.

## Importación de los espacios de nombres necesarios

Para utilizar Aspose.Slides para .NET de manera eficaz, deberá importar los siguientes espacios de nombres en su proyecto de C#:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Ahora que tenemos todo en su lugar, dividamos el proceso de extracción en pasos sencillos.

## Paso 1: Definir el directorio del documento

 Comience por especificar el directorio donde se encuentra su presentación de PowerPoint. Reemplace`"Your Document Directory"` con la ruta actual.

```csharp
string dataDir = "Your Document Directory";
```

## Paso 2: Cargue la presentación de PowerPoint

 A continuación, cargue la presentación de PowerPoint (PPTX) que contiene el hipervínculo de audio. Reemplace`"HyperlinkSound.pptx"` con el nombre de archivo de su presentación real.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Continúe con el siguiente paso.
}
```

## Paso 3: Acceda al sonido del hipervínculo

Recuperar el hipervínculo de la primera forma de la primera diapositiva. Si este hipervínculo tiene un sonido asociado, podemos proceder a extraerlo.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Continúe con el siguiente paso.
}
```

## Paso 4: Extraer audio del hipervínculo

Si el hipervínculo contiene sonido, podemos extraerlo como una matriz de bytes y guardarlo como un archivo multimedia.

```csharp
// Extraer el sonido del hipervínculo como una matriz de bytes
byte[] audioData = link.Sound.BinaryData;

// Especifique la ruta donde desea guardar el audio extraído
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Guardar el audio extraído en un archivo multimedia
File.WriteAllBytes(outMediaPath, audioData);
```

¡Felicitaciones! Ha extraído correctamente el audio de un hipervínculo en una presentación de PowerPoint con Aspose.Slides para .NET. Ahora puede usar este audio en sus proyectos multimedia.

## Conclusión

Aspose.Slides para .NET ofrece una forma eficaz y sencilla de extraer audio de hipervínculos en presentaciones de PowerPoint. Con los pasos que se describen en esta guía, puede reutilizar fácilmente el contenido de audio de sus presentaciones para mejorar sus proyectos.

## Preguntas frecuentes

### ¿Es Aspose.Slides para .NET una biblioteca gratuita?
 No, Aspose.Slides para .NET es una biblioteca comercial, pero puedes descargar una versión de prueba gratuita para explorar sus funciones desde[aquí](https://releases.aspose.com/).

### ¿Puedo extraer audio de formatos de PowerPoint más antiguos como PPT?
Sí, Aspose.Slides para .NET admite los formatos PPTX y PPT para la extracción de audio.

### ¿Existe un foro comunitario para el soporte de Aspose.Slides?
 ¡Por supuesto! Puedes obtener ayuda y compartir experiencias en el[Foro de la comunidad Aspose.Slides](https://forum.aspose.com/).

### ¿Puedo comprar una licencia temporal de Aspose.Slides para un proyecto a corto plazo?
Sí, puede obtener una licencia temporal para las necesidades de su proyecto a corto plazo visitando[Este enlace](https://purchase.aspose.com/temporary-license/).

### ¿Existen otros formatos de audio compatibles con la extracción además de MPG?
Sí, Aspose.Slides para .NET permite la extracción en varios formatos de audio. Puede convertir el audio al formato que prefiera después de la extracción.