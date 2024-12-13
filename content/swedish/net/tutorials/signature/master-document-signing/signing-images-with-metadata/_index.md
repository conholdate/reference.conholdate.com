---
title: Guide till att signera bilder med metadata med hjälp av GroupDocs.Signature
linktitle: Guide till att signera bilder med metadata
second_title: GroupDocs.Signature .NET API
description: Lär dig hur du effektivt signerar bilder med metadata i dina .NET-applikationer med GroupDocs.Signature. Denna steg-för-steg handledning täcker allt från installation till implementering, så att du enkelt kan förbättra dina dokument med metadatasignaturer.
type: docs
weight: 10
url: /sv/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## Introduktion

GroupDocs.Signature för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att effektivt signera bilder med metadata. Denna handledning guidar dig genom processen steg för steg.

## Förutsättningar

Innan du börjar, se till att du har följande:

1.  GroupDocs.Signature för .NET: Installera GroupDocs.Signature-paketet i ditt .NET-projekt. Du kan ladda ner den från[här](https://releases.groupdocs.com/signature/net/).
2. Bildfil: Förbered bildfilen du vill signera med metadata.

## Importera nödvändiga namnområden

Importera följande namnrymder i din C#-kod:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Steg 1: Ladda din bildfil

Börja med att ange sökvägen till din bildfil och utdatakatalogen för den signerade bilden:

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## Steg 2: Skapa metadatasignaturer

Skapa sedan metadatasignaturer och lägg till dem i signeringsalternativen:

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; // Start-ID för metadata
    MetadataSignOptions options = new MetadataSignOptions();

    //Lägg till olika typer av metadatasignaturer
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) // Strängvärde
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          // DateTime värde
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                // Heltalsvärde
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              // Dubbelt värde
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              // Decimalvärde
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             // Flytande värde

    // Signera dokumentet och spara resultatet
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## Slutsats

I den här handledningen lärde du dig hur du signerar en bild med metadata med GroupDocs.Signature för .NET. Genom att följa dessa steg kan du enkelt lägga till metadatasignaturer till dina .NET-applikationer, vilket förbättrar dina bilders funktionalitet och integritet.

## FAQ's

### Kan jag signera flera bilder med metadata med GroupDocs.Signature för .NET?
Ja, du kan signera flera bilder genom att iterera genom varje bildfil och använda metadatasignaturerna.

### Finns det en testversion tillgänglig för GroupDocs.Signature för .NET?
 Ja, du kan ladda ner testversionen från[här](https://releases.groupdocs.com/).

### Stöder GroupDocs.Signature for .NET andra filformat än bilder?
Absolut! GroupDocs.Signature stöder olika format, inklusive PDF, Word, Excel och mer.

### Kan jag anpassa utseendet på metadatasignaturen?
Ja, du kan anpassa aspekter som teckenstorlek, färg och position för metadatasignaturen.

### Var kan jag få support för GroupDocs.Signature för .NET?
 Besök forumet GroupDocs.Signature för support[här](https://forum.groupdocs.com/c/signature/13).