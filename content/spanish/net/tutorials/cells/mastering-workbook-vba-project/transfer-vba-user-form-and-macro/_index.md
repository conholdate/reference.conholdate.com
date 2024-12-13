---
title: Transferencia de macros y formularios de usuario de VBA entre libros de Excel
linktitle: Transferencia de macros y formularios de usuario de VBA entre libros de Excel
second_title: API de procesamiento de Excel Aspose.Cells .NET
description: Descubra el poder de la automatización de Excel con esta guía completa sobre cómo transferir formularios de usuario y macros de VBA entre libros de trabajo mediante Aspose.Cells para .NET. Perfecta tanto para principiantes como para desarrolladores experimentados.
type: docs
weight: 11
url: /es/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Introducción

¡Bienvenido a la guía definitiva para mejorar su experiencia con Excel mediante el uso de macros y formularios de usuario de VBA! En este tutorial, exploraremos cómo transferir un Diseñador de formularios de usuario de macros de VBA de un libro de trabajo a otro mediante la potente biblioteca Aspose.Cells para .NET. Tanto si es un desarrollador experimentado como si recién está comenzando, esta guía paso a paso le brindará los conocimientos necesarios para manejar archivos de Excel mediante programación. ¿Está listo para sumergirse en el tema? ¡Comencemos!

## Prerrequisitos
Antes de comenzar con la codificación, asegurémonos de que tienes todo lo que necesitas:

1. Entorno de desarrollo de C#: un entorno de trabajo para el desarrollo de C#, con Visual Studio altamente recomendado.
2.  Biblioteca Aspose.Cells para .NET: asegúrese de integrar la biblioteca Aspose.Cells en su proyecto. Puede hacerlo fácilmente[Descárgalo aquí](https://releases.aspose.com/cells/net/).
3. Conocimientos básicos de VBA y macros de Excel: la familiaridad con VBA y cómo funcionan las macros de Excel mejorará su comprensión de este tutorial.
4. Un archivo de Excel con un formulario de usuario: cree u obtenga un libro de Excel que contenga un formulario de usuario (preferiblemente con macros habilitadas, como`.xlsm` archivos).

## Importación de paquetes necesarios
Para utilizar las funcionalidades proporcionadas por Aspose.Cells, incluya los siguientes espacios de nombres en la parte superior de su archivo C#:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Estos espacios de nombres le darán acceso a las poderosas herramientas integradas en la biblioteca Aspose.Cells.

## Paso 1: Defina sus directorios de origen y salida
Primero, establezca las ubicaciones de sus archivos:

```csharp
// Definir los directorios de origen y salida
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Reemplace las rutas de marcador de posición con los directorios reales donde se almacenan sus archivos.

## Paso 2: Crear un libro de trabajo de destino vacío
A continuación, crea un nuevo libro de trabajo donde copiarás el formulario de usuario y las macros:

```csharp
// Crear un libro de trabajo de destino vacío
Workbook target = new Workbook();
```

Esto inicializa un libro de trabajo en blanco, que sirve como lienzo para la próxima transferencia de datos.

## Paso 3: Cargue su libro de trabajo de plantilla
Cargue el libro de trabajo que contiene el formulario de usuario y las macros:

```csharp
// Cargue el archivo Excel que contiene el formulario de usuario del Diseñador de macros de VBA
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Ajustar`"sampleDesignerForm.xlsm"` al nombre de su archivo actual.

## Paso 4: Copiar hojas de trabajo al libro de trabajo de destino
Ahora, copiemos las hojas de trabajo de la plantilla al libro de trabajo de destino:

```csharp
// Copiar todas las hojas de trabajo de plantilla al libro de trabajo de destino
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Agregar un mensaje en la celda A2 de la hoja de cálculo de destino
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Este código recorre cada hoja de trabajo de la plantilla y la copia al libro de destino, lo que garantiza que todos los datos se transfieran sin problemas.

## Paso 5: Copiar macros VBA desde la plantilla
A continuación, copiaremos las macros de VBA, incluidos los módulos UserForm Designer, al nuevo libro de trabajo:

```csharp
// Copiar el UserForm del Diseñador de macros de VBA desde la plantilla al destino
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Copiar el código del módulo ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Copiar el código y los datos de otros módulos
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Obtenga el almacenamiento del diseñador de formularios de usuario
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Agregue el almacenamiento del diseñador al proyecto VBA de destino
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Este código garantiza que no solo se copie el código sino también el diseño del formulario de usuario, preservando la funcionalidad de sus macros.

## Paso 6: Guardar el libro de trabajo de destino
Después de completar el proceso de copia, guarde su nuevo libro de trabajo:

```csharp
// Guardar el libro de trabajo de destino
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Modifique el nombre del archivo de salida según sea necesario. Este paso crea su libro de trabajo personalizado lleno de macros y formularios de usuario.

## Paso 7: Confirmar el éxito
Por último, imprima un mensaje de éxito en la consola:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Esta simple línea le asegura que su proceso se desarrolló sin problemas: ¡una confirmación esencial de su arduo trabajo!

## Conclusión
¡Felicitaciones! Aprendió a copiar un Diseñador de formularios de usuario de macros de VBA de un libro de trabajo a otro usando Aspose.Cells para .NET. Si bien puede parecer abrumador al principio, la práctica lo convertirá en un experto en la manipulación de libros de trabajo. Recuerde que la codificación se trata de experimentación, así que no dude en explorar diferentes funcionalidades dentro de sus archivos de Excel. Si tiene alguna pregunta o necesita ayuda, los foros y la documentación de Aspose son excelentes recursos de soporte.

## Preguntas frecuentes

### ¿Qué versiones de Excel admite Aspose.Cells?
Aspose.Cells admite varios formatos de Excel, incluidos XLSX, XLSM, CSV y más.

### ¿Puedo utilizar Aspose.Cells gratis?
 ¡Sí! Puedes empezar con una prueba gratuita para evaluar la biblioteca:[Prueba gratuita](https://releases.aspose.com/).

### ¿Necesito Visual Studio para ejecutar este código?
Si bien se recomienda Visual Studio por sus características fáciles de usar, cualquier IDE de C# que admita el desarrollo .NET será suficiente.

### ¿Dónde puedo encontrar más ejemplos y documentación?
 Puedes explorar el[Documentación de Aspose.Cells](https://reference.aspose.com/cells/net/) para más ejemplos y explicaciones detalladas.

### ¿Cómo resuelvo problemas al utilizar Aspose.Cells?
 Deberías visitar el[Foro de soporte de Aspose](https://forum.aspose.com/c/cells/9) para solicitar ayuda a la comunidad y al personal de soporte de Aspose.