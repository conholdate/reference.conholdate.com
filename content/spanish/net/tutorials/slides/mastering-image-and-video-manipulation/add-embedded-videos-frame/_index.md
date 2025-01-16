---
title: Agregar marcos de videos incrustados en presentaciones .NET
linktitle: Agregar marcos de videos incrustados en presentaciones .NET
second_title: API de procesamiento de PowerPoint Aspose.Slides .NET
description: Descubra el potencial de sus presentaciones aprendiendo a incrustar videos con Aspose.Slides para .NET. Este completo tutorial le guiará paso a paso por el proceso de integración de elementos multimedia.
type: docs
weight: 19
url: /es/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## Introducción

En el vertiginoso panorama de las presentaciones actuales, la integración de elementos multimedia puede aumentar significativamente la participación y la retención de la audiencia. Aspose.Slides para .NET ofrece una solución sólida para incorporar fotogramas de vídeo en las diapositivas. Este tutorial le guiará por el proceso paso a paso, lo que le garantizará una experiencia fluida de principio a fin.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Biblioteca Aspose.Slides para .NET: Descargue e instale la biblioteca desde[página de lanzamiento](https://releases.aspose.com/slides/net/).
- Contenido multimedia: un archivo de vídeo (por ejemplo, "Wildlife.mp4") que desea incrustar en su presentación.

## Importar espacios de nombres necesarios

Comience importando los espacios de nombres necesarios en su proyecto .NET:

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## Paso 1: Configura tus directorios

Asegúrese de que su proyecto incluya los directorios necesarios para los archivos de documentos y multimedia:

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// Crear directorio si no existe
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## Paso 2: Crear una instancia de la clase de presentación

 Crear una instancia de la`Presentation` clase para representar su archivo PPTX:

```csharp
using (Presentation pres = new Presentation())
{
    // Obtenga la primera diapositiva
    ISlide sld = pres.Slides[0];
```

## Paso 3: Incrustar el vídeo

Incruste el vídeo en su presentación usando el siguiente código:

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## Paso 4: Agregar un fotograma de vídeo

A continuación, agregue un fotograma de vídeo a la diapositiva:

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## Paso 5: Configurar las propiedades del vídeo

Establezca las propiedades del video, incluido el modo de reproducción y el volumen:

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // Reproducir automáticamente el vídeo
vf.Volume = AudioVolumeMode.Loud; // Establecer el nivel de volumen
```

## Paso 6: Guarda tu presentación

Por último, guarde el archivo PPTX modificado en el disco:

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

Puedes repetir estos pasos para cada vídeo que desees incrustar en tu presentación.

## Conclusión

¡Felicitaciones! Ha incorporado con éxito un fotograma de video en su presentación con Aspose.Slides para .NET. Esta función dinámica puede llevar sus presentaciones al siguiente nivel y cautivar a su audiencia con contenido multimedia perfectamente integrado.

## Preguntas frecuentes

### ¿Puedo incrustar vídeos en cualquier diapositiva de la presentación?

 Sí, puedes seleccionar cualquier diapositiva ajustando el índice en`pres.Slides[index]`.

### ¿Qué formatos de vídeo son compatibles?

Aspose.Slides admite varios formatos de vídeo, incluidos MP4, AVI y WMV.

### ¿Puedo personalizar el tamaño y la posición del fotograma del vídeo?

 ¡Por supuesto! Puedes modificar los parámetros en`AddVideoFrame(x, y, width, height, video)` para adaptarse a sus necesidades.

### ¿Existe un límite en la cantidad de vídeos que puedo insertar?

El límite de videos incrustados generalmente depende de la capacidad de su software de presentación.

### ¿Dónde puedo buscar más ayuda o compartir mi experiencia?

 Siéntete libre de visitar el[Foro de Aspose.Slides](https://forum.aspose.com/c/slides/11) para apoyo y debates de la comunidad.