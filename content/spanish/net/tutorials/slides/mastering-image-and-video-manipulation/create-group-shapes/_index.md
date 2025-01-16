---
title: Cree formas de grupo en PowerPoint con Aspose.Slides para .NET
linktitle: Cree formas de grupo en PowerPoint con Aspose.Slides para .NET
second_title: API de procesamiento de PowerPoint Aspose.Slides .NET
description: Aprenda a crear y administrar formas de grupo con Aspose.Slides para .NET. Esta guía completa ofrece instrucciones claras paso a paso.
type: docs
weight: 11
url: /es/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Introducción

Mejorar el atractivo visual y la organización de sus presentaciones de PowerPoint puede tener un impacto significativo en la participación de su audiencia. Un método eficaz para lograrlo es mediante formas de grupo. En este tutorial, exploraremos cómo aprovechar Aspose.Slides para .NET para crear y manipular formas de grupo en sus presentaciones.

## Prerrequisitos

Antes de sumergirte en el tutorial, asegúrate de tener lo siguiente:

-  Aspose.Slides para .NET: Descargue e instale la última versión de la biblioteca Aspose.Slides desde[Sitio web de Aspose](https://releases.aspose.com/slides/net/).
- Entorno de desarrollo: configure un IDE compatible con .NET, como Visual Studio, para trabajar en su proyecto.
- Conocimientos básicos de C#: familiarícese con los conceptos fundamentales de C#.


## Importar espacios de nombres necesarios

En su proyecto de C#, comience por incluir los siguientes espacios de nombres:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Paso 1: Crear una instancia de la clase de presentación

 Crear una instancia de la`Presentation`Clase en la que trabajarás en tus diapositivas. Especifica el directorio donde se almacenan tus documentos:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // Los pasos para crear y manipular formas irán aquí.
}
```

## Paso 2: Acceda a la primera diapositiva

Recupere la primera diapositiva de su presentación recién creada:

```csharp
ISlide slide = pres.Slides[0];
```

## Paso 3: Acceda a la colección de formas

Obtenga la colección de formas en la diapositiva:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Paso 4: Agregar una forma de grupo

Ahora es el momento de agregar una forma de grupo a la diapositiva:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Paso 5: Agregar formas dentro del grupo

Puede rellenar la forma del grupo con formas individuales, como rectángulos:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Forma 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Forma 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Forma 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Forma 4
```

## Paso 6: Defina el marco para la forma del grupo

Establecer un marco para la forma del grupo le otorga un límite definido:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Paso 7: Guardar la presentación

Por último, guarde la presentación modificada en el directorio especificado:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Conclusión

¡Felicitaciones! Ha creado formas de grupo con éxito en sus presentaciones de PowerPoint con Aspose.Slides para .NET. Al organizar las formas de esta manera, puede mejorar en gran medida el diseño visual y la claridad de su contenido, lo que hará que sus presentaciones sean más impactantes.

## Preguntas frecuentes

### ¿Aspose.Slides es compatible con la última versión de .NET?

 Sí, Aspose.Slides se actualiza periódicamente para que sea compatible con las últimas versiones de .NET.[documentación](https://reference.aspose.com/slides/net/) para obtener los últimos detalles de compatibilidad.

### ¿Puedo probar Aspose.Slides antes de comprarlo?

 ¡Por supuesto! Puedes descargar una versión de prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar ayuda para consultas relacionadas con Aspose.Slides?

 Visita Aspose.Slides[foro](https://forum.aspose.com/c/slides/11) para apoyo y debates de la comunidad.

### ¿Cómo obtengo una licencia temporal para Aspose.Slides?

 Puede solicitar una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo comprar una licencia completa para Aspose.Slides?

 Puede comprar una licencia en[Página de compra](https://purchase.aspose.com/buy).