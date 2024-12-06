---
title: Crear 1Bpp indexado
linktitle: Crear 1Bpp indexado
second_title: API de procesamiento de documentos Aspose.Words
description: Esta guía proporciona instrucciones paso a paso y código de muestra para ayudarlo a crear de manera eficiente imágenes indexadas de 1 Bpp para archivar, imprimir o ahorrar espacio.
type: docs
weight: 10
url: /es/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Introducción

¿Alguna vez ha tenido que convertir un documento de Word en una imagen en blanco y negro? Ya sea para archivarlo digitalmente, imprimirlo o simplemente ahorrar espacio, convertir sus documentos en una imagen indexada de 1 Bpp puede resultar increíblemente útil. En esta guía, le mostraremos un método sencillo para lograrlo utilizando Aspose.Words para .NET. ¡Comencemos!

## Prerrequisitos

Antes de sumergirse en el código, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: Descargue e instale la biblioteca desde[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo .NET: si bien Visual Studio es una opción popular, cualquier IDE que admita .NET funcionará.
- Conocimientos básicos de C#: la familiaridad con C# será útil, pero mantendremos las cosas simples.
- Ejemplo de documento de Word: Tenga un documento listo para la conversión.

## Paso 1: Importar los espacios de nombres necesarios

Para utilizar Aspose.Words, es necesario importar los espacios de nombres correspondientes. Esto es esencial para acceder a las clases y métodos necesarios para la manipulación de documentos.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 2: Configura tu directorio de documentos

Especifique la ruta al directorio donde está almacenado su documento de Word y donde desea guardar la imagen convertida.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Paso 3: Cargue el documento de Word

Cargue su documento de Word en un`Aspose.Words.Document` objeto. Este objeto le permite manipular el documento mediante programación.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 4: Configurar las opciones para guardar imágenes

 A continuación, configure el`ImageSaveOptions` Para definir cómo se guardará el documento como imagen, lo configuraremos para que se guarde en formato PNG con modo de color indexado de 1 Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Convertir solo la primera página
    ImageColorMode = ImageColorMode.BlackAndWhite, // Establecer en blanco y negro
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Utilice el formato indexado de 1 Bpp
};
```

- SaveFormat.Png: especifica que el formato de salida será PNG.
- PageSet(1): indica que solo se convertirá la primera página del documento.
- ImageColorMode.BlackAndWhite: garantiza que la imagen esté en blanco y negro.
- ImagePixelFormat.Format1bppIndexed: establece el formato de píxel en 1 Bpp indexado, optimizando el espacio.

## Paso 5: Guardar el documento como imagen

 Por último, utilice el`Save` método de la`Document` objeto para guardar la imagen convertida.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Conclusión

¡Felicitaciones! Has convertido exitosamente un documento de Word en una imagen indexada de 1 Bpp usando Aspose.Words para .NET. Este método no solo es eficiente, sino que también te ayuda a crear imágenes de alto contraste adecuadas para varias aplicaciones. No dudes en integrar esta funcionalidad en tus proyectos. ¡Disfruta de la codificación!

## Preguntas frecuentes

### ¿Qué es una imagen indexada de 1 Bpp?
Una imagen indexada de 1 Bpp (1 bit por píxel) es un formato de imagen en blanco y negro donde cada píxel está representado por un solo bit, ya sea 0 o 1. Este formato ahorra mucho espacio, lo que lo hace ideal para archivar.

### ¿Puedo convertir varias páginas de un documento de Word a la vez?
 ¡Sí! Simplemente modifique el`PageSet` propiedad en el`ImageSaveOptions` para incluir varias páginas o configurarlo para convertir el documento completo.

### ¿Necesito una licencia para usar Aspose.Words para .NET?
 Sí, se requiere una licencia para la funcionalidad completa. Puede obtener una[Licencia temporal aquí](https://purchase.aspose.com/temporary-license/).

### ¿A qué otros formatos de imagen puedo convertir mi documento de Word?
 Aspose.Words admite varios formatos, incluidos JPEG, BMP y TIFF. Solo cambia el`SaveFormat`en el`ImageSaveOptions` al formato deseado.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?
 Para obtener documentación completa, visite el sitio[Página de documentación de Aspose.Words para .NET](https://reference.aspose.com/words/net/).