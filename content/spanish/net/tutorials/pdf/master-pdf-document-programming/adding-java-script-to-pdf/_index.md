---
title: Cómo agregar Java Script a un archivo PDF
linktitle: Agregar archivo PDF con Java Script
second_title: Referencia de API de Aspose.PDF para .NET
description: Este documento proporciona una guía completa para agregar elementos interactivos como alertas emergentes o funciones de impresión automática a documentos PDF utilizando Aspose.PDF para .NET.
type: docs
weight: 10
url: /es/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Introducción
Este documento ofrece una guía completa para agregar elementos interactivos, como alertas emergentes o funciones de impresión automática, a documentos PDF mediante Aspose.PDF para .NET. Al aprovechar las capacidades de esta biblioteca, puede crear archivos PDF dinámicos y atractivos que satisfagan las distintas necesidades de los usuarios.

## Prerrequisitos
 Antes de continuar, asegúrese de haber descargado la última versión de Aspose.PDF para .NET desde[Comunicados de Aspose](https://comunicados.aspose.com/pdf/net/) o obtuvo una prueba gratuita a través de su sitio web:[releases.aspose.com](http://releases.aspose.com).

También debe tener conocimientos básicos de C# y estar familiarizado con el entorno de desarrollo que está utilizando. Además, si necesita evitar limitaciones durante su proceso de desarrollo, considere adquirir una licencia temporal de Aspose.

## Importación de paquetes necesarios
Para comenzar a escribir código, importe los espacios de nombres necesarios de la biblioteca Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Paso 1: Cargar un PDF existente
Cargue un documento PDF existente al que desee agregar elementos interactivos:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su archivo PDF.

## Paso 2: Agregar JavaScript a nivel de documento

 Para aplicar un script que se active cuando se abra el documento, cree una instancia de`JavascriptAction` objeto:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Paso 3: Agregar JavaScript a nivel de página

 Para activar acciones específicas en función de la apertura o el cierre de páginas, cree una instancia`JavascriptAction` objeto para cada página:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Paso 4: Guardar el documento PDF

Para guardar el documento PDF modificado, especifique la ruta del archivo de salida:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Conclusión
Si sigue esta guía y utiliza Aspose.PDF para .NET, podrá mejorar eficazmente sus archivos PDF con elementos interactivos. Esta biblioteca ofrece una solución integral para crear documentos dinámicos y atractivos que satisfagan las distintas necesidades de los usuarios.

## Preguntas frecuentes

### ¿Puedo agregar múltiples acciones de JavaScript a diferentes páginas de un PDF?
Sí, puedes asignar diferentes acciones de JavaScript a páginas individuales o a todo el documento.

### ¿Es posible eliminar JavaScript de un PDF después de agregarlo?
 Sí, puedes eliminar o modificar acciones de JavaScript existentes borrando la casilla`Actions` Propiedades del documento o página.

### ¿Qué tipo de funciones de JavaScript puedo utilizar en un PDF?
Puede utilizar cualquier JavaScript compatible con el motor JavaScript de Adobe Acrobat, como impresión, alertas y manipulaciones de formularios.

### ¿Funciona JavaScript en todos los visores de PDF?
La mayoría de las acciones de JavaScript funcionarán en visores de PDF que admitan archivos PDF interactivos, como Adobe Acrobat. Sin embargo, es posible que algunos lectores de PDF básicos no admitan JavaScript.