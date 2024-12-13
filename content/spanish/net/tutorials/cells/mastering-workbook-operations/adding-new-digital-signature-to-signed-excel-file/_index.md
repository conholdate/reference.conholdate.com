---
title: Cómo agregar una nueva firma digital a un archivo Excel firmado
linktitle: Cómo agregar una nueva firma digital a un archivo Excel firmado
second_title: API de procesamiento de Excel Aspose.Cells .NET
description: Aprenda a agregar una nueva firma digital a un archivo de Excel firmado existente mediante Aspose.Cells para .NET. Esta guía completa cubre todos los requisitos previos, instrucciones paso a paso y ejemplos de código.
type: docs
weight: 12
url: /es/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Introducción

En el panorama digital actual, garantizar la autenticidad e integridad de los documentos es más crucial que nunca. Las firmas digitales proporcionan una forma confiable de verificar que un documento no ha sido alterado y que proviene de una fuente legítima. Si está trabajando con archivos de Excel en .NET y necesita agregar una nueva firma digital a un archivo que ya está firmado, ¡esta guía es para usted! Le guiaremos a través del proceso de agregar una firma digital a un archivo de Excel firmado existente utilizando Aspose.Cells para .NET.

## Prerrequisitos

Antes de sumergirnos en la implementación, asegúrese de tener lo siguiente:

1.  Aspose.Cells para .NET: Descargue e instale Aspose.Cells desde[página de lanzamiento](https://releases.aspose.com/cells/net/).
2. .NET Framework: asegúrese de que su máquina tenga configurado .NET Framework y que esté familiarizado con los conceptos básicos de programación .NET.
3. Certificado digital: obtenga un certificado digital válido en formato .pfx. Para realizar pruebas, puede crear un certificado autofirmado.
4. Entorno de desarrollo: utilice un IDE como Visual Studio para escribir y ejecutar su código C#.
5. Archivo de Excel de muestra: tenga un archivo de Excel existente que ya esté firmado digitalmente, que será el destino para agregar una nueva firma.

Con estos requisitos previos establecidos, ¡pasemos al código!

## Importar paquetes necesarios

En la parte superior de su archivo C#, incluya los siguientes espacios de nombres para acceder a las clases y métodos necesarios:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Paso 1: Defina sus directorios

Especifique los directorios para sus archivos de origen y dónde guardar el archivo de salida:

```csharp
// Directorio de fuentes
string sourceDir = "Your Document Directory"; // Reemplazar con su directorio actual
// Directorio de salida
string outputDir = "Your Document Directory"; // Reemplazar con su directorio actual
```

## Paso 2: Cargue el libro de trabajo firmado existente

Cargue el libro de Excel que ya está firmado:

```csharp
// Cargue el libro de trabajo que ya está firmado digitalmente
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Paso 3: Crear una colección de firmas digitales

Crea una colección para administrar tus firmas digitales:

```csharp
//Crear la colección de firmas digitales
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Paso 4: Cargue su certificado

Cargue su certificado digital, que se utilizará para crear la nueva firma:

```csharp
// Archivo de certificado y su contraseña
string certFileName = sourceDir + "AsposeDemo.pfx"; // Su archivo de certificado
string password = "aspose"; // Su contraseña de certificado

// Crear nuevo certificado
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Paso 5: Crear una nueva firma digital

Ahora, crea una nueva firma digital y agrégala a tu colección:

```csharp
// Crea una nueva firma digital y agrégala a la colección
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Paso 6: Agregue la colección de firmas al libro de trabajo

Agregue la colección de firmas digitales al libro de trabajo:

```csharp
// Agregar una colección de firmas digitales al libro de trabajo
workbook.AddDigitalSignature(dsCollection);
```

## Paso 7: Guardar el libro de trabajo

Guarde el libro de trabajo con la nueva firma digital incluida:

```csharp
// Guardar el libro de trabajo
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Paso 8: Confirmar el éxito

Proporcionar retroalimentación tras la ejecución exitosa:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Conclusión

¡Felicitaciones! Ha agregado con éxito una nueva firma digital a un archivo Excel ya firmado mediante Aspose.Cells para .NET. Este proceso mejora la seguridad de sus documentos y garantiza su autenticidad e integridad.

## Preguntas frecuentes

### ¿Qué es una firma digital?

Una firma digital es un esquema matemático que verifica la autenticidad e integridad de los mensajes o documentos digitales, asegurando que no han sido alterados y confirmando la identidad del firmante.

### ¿Necesito un certificado especial para crear una firma digital?

Sí, se requiere un certificado digital emitido por una autoridad de certificación (CA) confiable para crear una firma digital válida.

### ¿Puedo utilizar un certificado autofirmado para realizar pruebas?

¡Por supuesto! Puedes usar un certificado autofirmado para fines de desarrollo y prueba, pero para producción, es recomendable usar un certificado de una CA confiable.

### ¿Qué sucede si intento agregar una firma a un documento no firmado?

Si intenta agregar una firma digital a un documento que aún no está firmado, funcionará sin problemas, pero la firma original no estará presente.

### ¿Dónde puedo encontrar más información sobre Aspose.Cells?

 Para obtener guías detalladas y referencias de API, consulte[Documentación de Aspose.Cells](https://reference.aspose.com/cells/net/).