---
title: Crear modelos 3D primitivos
linktitle: Crear modelos 3D primitivos
second_title: API .NET de Aspose.3D
description: Aprenda a crear y personalizar modelos 3D primitivos, incluidas cajas y cilindros, y guárdelos en formato FBX sin esfuerzo.
type: docs
weight: 10
url: /es/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Introducción

¡Bienvenido al mundo envolvente del modelado 3D con Aspose.3D para .NET! En este completo tutorial, lo guiaremos a través del proceso de creación de modelos 3D primitivos paso a paso. Ya sea que sea un desarrollador experimentado o un principiante ansioso por aprender, esta guía le permitirá crear elementos 3D visualmente impactantes para sus proyectos.

## Prerrequisitos

Antes de sumergirse en el modelado 3D, asegúrese de tener los siguientes requisitos previos:

-  Aspose.3D para .NET: Descargue e instale la biblioteca Aspose.3D para .NET desde[página de descarga](https://releases.aspose.com/3d/net/).
  
- Entorno de desarrollo .NET: configure un entorno compatible con Aspose.3D, como Visual Studio.

¡Con todo preparado, emprendemos nuestra aventura de modelado 3D!

## Importación de los espacios de nombres necesarios

Comience importando los espacios de nombres necesarios para acceder a las funcionalidades de Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Estos espacios de nombres le proporcionarán las herramientas necesarias para manipular modelos 3D y guardar sus creaciones.

## Paso 1: Inicializar un objeto de escena

Cree un nuevo objeto de escena que actúe como lienzo para sus modelos 3D:

```csharp
// Inicializar un objeto de escena
Scene scene = new Scene();
```

Esta escena contendrá las formas primitivas que estás a punto de crear.

## Paso 2: Crear un modelo de caja

A continuación, agreguemos un modelo de caja a su escena:

```csharp
// Crear un modelo de caja
scene.RootNode.CreateChildNode("box", new Box());
```

Puede personalizar las dimensiones y propiedades de la caja para adaptarla a su visión creativa.

## Paso 3: Crear un modelo de cilindro

Ahora, mejora tu escena agregando un cilindro:

```csharp
// Crear un modelo de cilindro
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Al igual que con la caja, siéntete libre de ajustar los parámetros del cilindro para lograr el aspecto deseado.

## Paso 4: Guarda la escena en formato FBX

Para conservar su modelo 3D, guárdelo en formato FBX:

```csharp
// Guardar dibujo en formato FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Asegúrese de elegir un directorio de salida y un nombre de archivo adecuados para su modelo.

## Paso 5: Mostrar un mensaje de éxito

Por último, celebra tu éxito mostrando un mensaje:

```csharp
// Mostrar mensaje de éxito
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

¡Tu escena 3D compuesta de modelos primitivos ahora está completa y guardada!

## Conclusión

 ¡Felicitaciones por crear modelos 3D asombrosos con Aspose.3D para .NET! Este tutorial cubrió los conceptos básicos del modelado primitivo, pero las posibilidades son infinitas. Explore más sobre las características y técnicas avanzadas en[documentación](https://reference.aspose.com/3d/net/).

## Preguntas frecuentes

### ¿Puedo utilizar Aspose.3D para .NET con lenguajes de programación distintos de .NET?

Aspose.3D soporta principalmente .NET, pero hay versiones disponibles para Java y otras plataformas.

### ¿Hay una prueba gratuita disponible?

 Sí, puedes probar las capacidades de Aspose.3D con un[prueba gratis](https://releases.aspose.com/).

### ¿Dónde puedo encontrar soporte para Aspose.3D para .NET?

Para obtener apoyo comunitario, visite el sitio[Foro de Aspose.3D](https://forum.aspose.com/c/3d/18).

### ¿Cómo puedo obtener una licencia temporal?

 Puede solicitar una licencia temporal[aquí](https://purchase.conholdate.com/temporary-license/).

### ¿Hay tutoriales adicionales disponibles?

 ¡Sí! Explora más tutoriales y ejemplos en el[documentación](https://reference.aspose.com/3d/net/).