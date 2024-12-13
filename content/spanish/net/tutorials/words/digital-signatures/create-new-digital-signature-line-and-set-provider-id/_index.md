---
title: Crear nueva línea de firma digital y establecer ID de proveedor
linktitle: Crear nueva línea de firma digital y establecer ID de proveedor
second_title: API de procesamiento de documentos Aspose.Words
description: Descubra cómo agregar líneas de firma de forma programada a sus documentos de Word con Aspose.Words para .NET. Esta guía completa cubre todo, desde la configuración de su entorno de desarrollo hasta la inserción de líneas de firma y la firma segura de documentos.
type: docs
weight: 10
url: /es/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Introducción

¡Hola, entusiastas de la tecnología! ¿Alguna vez quisiste automatizar la inclusión de líneas de firma en tus documentos de Word? Hoy, profundizaremos en cómo lograrlo usando Aspose.Words para .NET. Esta guía paso a paso te guiará en la creación de una línea de firma y la configuración del ID del proveedor, lo que hará que tus tareas de procesamiento de documentos sean más eficientes y optimizadas.

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo configurado:

1.  Aspose.Words para .NET: Si aún no lo has instalado, descárgalo[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: utilice Visual Studio o cualquier configuración de desarrollo de C#.
3. .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.
4. Certificado PFX: necesitará un certificado PFX para firmar documentos, que puede obtenerse de una autoridad de certificación confiable.

## Importación de los espacios de nombres necesarios

Para comenzar, importe los espacios de nombres necesarios en su proyecto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Ahora, profundicemos en los detalles de cómo crear una nueva línea de firma y configurar el ID del proveedor.

## Paso 1: Crear un nuevo documento

Primero, necesitamos crear un nuevo documento de Word, que servirá como lienzo para nuestra línea de firma:

```csharp
// Especifique la ruta a su directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aquí, inicializamos un nuevo`Document` y un`DocumentBuilder`, lo que nos permite agregar elementos fácilmente.

## Paso 2: Definir las opciones de la línea de firma

A continuación, definiremos las opciones para nuestra línea de firma, incluido el nombre del firmante, el título, el correo electrónico y otros detalles relevantes:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Estas opciones ayudan a personalizar la línea de la firma, haciéndola clara y profesional.

## Paso 3: Insertar la línea de firma

Con nuestras opciones listas, ahora podemos insertar la línea de firma en el documento:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 El`InsertSignatureLine` El método agrega la línea de firma y le asignamos un ID de proveedor único.

## Paso 4: Guardar el documento

Después de insertar la línea de firma, guardemos el documento:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Esto guarda su documento con la línea de firma recién agregada.

## Paso 5: Configurar las opciones de firma

Ahora, configuraremos las opciones de firma, incluido el ID de la línea de firma, el ID del proveedor, los comentarios y el tiempo de firma:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Estas configuraciones garantizan que el documento esté firmado con los detalles correctos.

## Paso 6: Crear el titular del certificado

Para firmar el documento, necesitamos crear un titular de certificado utilizando el certificado PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Reemplazar`"morzal.pfx"` con el nombre de archivo de su certificado real y`"aw"` con la contraseña de su certificado.

## Paso 7: Firma el documento

Por último, firmaremos el documento utilizando la utilidad de firma digital:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Este proceso firma el documento y lo guarda como un archivo nuevo.

## Conclusión

¡Felicitaciones! Ha creado con éxito una línea de firma y ha establecido el ID del proveedor en un documento de Word con Aspose.Words para .NET. Esta potente biblioteca simplifica las tareas de procesamiento de documentos y hace que su flujo de trabajo sea más eficiente. ¡Pruébela y vea cómo puede mejorar sus proyectos!

## Preguntas frecuentes

### ¿Puedo personalizar la apariencia de la línea de firma?
 ¡Por supuesto! Puedes ajustar varias opciones en el`SignatureLineOptions` para adaptarse a su estilo y necesidades.

### ¿Qué pasa si no tengo un certificado PFX?
Necesitará obtener uno de una autoridad de certificación confiable, ya que es esencial para firmar documentos digitalmente.

### ¿Puedo agregar varias líneas de firma a un documento?
Sí, puede agregar varias líneas de firma repitiendo el proceso de inserción con diferentes opciones.

### ¿Aspose.Words para .NET es compatible con .NET Core?
Sí, Aspose.Words para .NET es compatible con .NET Core, lo que lo hace versátil para diversos entornos de desarrollo.

### ¿Qué tan seguras son las firmas digitales?
Las firmas digitales creadas con Aspose.Words son altamente seguras, siempre que utilice un certificado válido y confiable.