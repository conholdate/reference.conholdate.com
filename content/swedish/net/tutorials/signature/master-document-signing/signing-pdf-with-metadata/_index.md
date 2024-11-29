---
title: Guide till att signera PDF-filer med metadata med GroupDocs.Signature
linktitle: Guide till att signera PDF-filer med metadata
second_title: GroupDocs.Signature .NET API
description: Lär dig hur du förstärker dina PDF-dokument med förbättrad säkerhet och spårbarhet genom att signera dem med metadata med GroupDocs.Signature för .NET. Denna omfattande handledning ger en tydlig.
type: docs
weight: 11
url: /sv/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Introduktion

I den här handledningen kommer vi att lära oss hur du signerar ett PDF-dokument och lägger till metadata med GroupDocs.Signature för .NET. Att lägga till metadata förbättrar dokumentet genom att tillhandahålla viktig information som författare, skapandedatum, dokument-ID och mer.

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  GroupDocs.Signature för .NET: Ladda ner den från[här](https://releases.groupdocs.com/signature/net/).
2. Ett PDF-dokument: Ha ett exempel på en PDF-fil redo för signering.
3. Grundläggande kunskaper i C#-programmering: Förtrogenhet med C#-syntax är nödvändig för att förstå kodexemplen.

## Importera namnområden

Börja med att importera de nödvändiga namnområdena för att komma åt de nödvändiga klasserna och metoderna:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Steg 1: Ladda PDF-dokumentet

Ange sökvägen till PDF-dokumentet du vill signera:

```csharp
string filePath = "sample.pdf";
```

## Steg 2: Ange sökväg för utdatafil

Definiera var den signerade PDF-filen med metadata ska sparas:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Steg 3: Skapa en signaturinstans

 Initiera a`Signature` instans med sökvägen till PDF-dokumentet:

```csharp
using (Signature signature = new Signature(filePath))
{
    // Signaturrelaterad kod kommer hit
}
```

## Steg 4: Definiera metadataalternativ

 Skapa`MetadataSignOptions` och lägg till metadatafälten tillsammans med deras värden:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Strängvärde
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // DateTime värde
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Heltalsvärde
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Dubbelt värde
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Decimalvärde
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Flytvärde
```

## Steg 5: Signera dokumentet

Signera PDF-dokumentet med de angivna metadataalternativen och spara det signerade dokumentet:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Slutsats

I den här handledningen tog vi upp hur man signerar ett PDF-dokument med metadata med GroupDocs.Signature för .NET. Genom att följa dessa steg kan du enkelt berika dina PDF-filer med värdefull metadata, vilket förbättrar deras spårbarhet och användbarhet.

## FAQ's

### Kan jag lägga till anpassade metadatafält i mina PDF-dokument?

Ja, du kan lägga till anpassade metadatafält genom att ange fältnamnet och dess motsvarande värde med GroupDocs.Signature för .NET.

### Är GroupDocs.Signature för .NET kompatibel med alla versioner av .NET Framework?

GroupDocs.Signature för .NET är kompatibel med olika versioner av .NET Framework, vilket säkerställer flexibilitet och enkel integration.

### Stöder GroupDocs.Signature signering av andra dokumentformat förutom PDF?

Ja, GroupDocs.Signature stöder ett brett utbud av dokumentformat, inklusive Word, Excel, PowerPoint och mer.

### Kan jag signera flera dokument samtidigt med GroupDocs.Signature för .NET?

Absolut! Du kan signera flera dokument samtidigt genom att iterera genom en lista med filer och tillämpa signaturprocessen programmatiskt.

### Finns teknisk support tillgänglig för GroupDocs.Signature-användare?

Ja, GroupDocs tillhandahåller dedikerad teknisk support genom sina forum. Du kan komma åt supportforumet[här](https://forum.groupdocs.com/c/signature/13).