---
title: Bradley binariseringsalgoritm
linktitle: Bradley binariseringsalgoritm
second_title: Aspose.PDF för .NET API Referens
description: Lär dig hur du konverterar PDF-sidor till binära TIFF-bilder av hög kvalitet med bradley-binariseringsalgoritmen i Aspose.PDF för .NET. Denna steg-för-steg-guide innehåller kodexempel.
type: docs
weight: 30
url: /sv/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Introduktion

den här handledningen guidar vi dig genom processen att konvertera en PDF-sida till en TIFF-bild med Bradleys binariseringsalgoritm. Aspose.PDF för .NET förenklar denna uppgift, så att du enkelt kan automatisera och effektivisera dina dokumentarbetsflöden.

## Förutsättningar

Innan vi börjar, se till att du har följande:

-  Aspose.PDF för .NET: Ladda ner biblioteket från[här](https://releases.aspose.com/pdf/net/).
- Visual Studio (eller vilken C# IDE som helst).
- Grundläggande kunskaper i C#.
-  En giltig licens eller en[tillfällig licens](https://purchase.aspose.com/temporary-license/) från Aspose.

## Steg 1: Konfigurera ditt projekt

Skapa först ett nytt C#-projekt i din IDE och importera de nödvändiga namnrymden:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Steg 2: Definiera dokumentkatalogen

Ange sökvägen till katalogen där ditt PDF-dokument finns, samt utdatasökvägarna för TIFF-bilderna:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Sökväg till din PDF-fil
```

Den här katalogen lagrar både käll-PDF och de konverterade TIFF-filerna.

## Steg 3: Ladda PDF-dokumentet

Öppna PDF-dokumentet du vill konvertera:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Ersätta`PageToTIFF.pdf` med namnet på din PDF-fil.

## Steg 4: Ange utmatningsvägar

Definiera utdatasökvägarna för de genererade TIFF-filerna:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Steg 5: Ställ in bildupplösning

Ställ in upplösningen för TIFF-bilderna. En högre DPI ger bättre bildkvalitet:

```csharp
Resolution resolution = new Resolution(300);
```

## Steg 6: Konfigurera TIFF-inställningar

Konfigurera inställningarna för TIFF-bilden, inklusive komprimering och färgdjup:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Genom att använda 1bpp (1-bit per pixel) förbereds bilden för binär utdata.

## Steg 7: Skapa TIFF-enheten

Skapa en TIFF-enhet som hanterar konverteringen:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Steg 8: Konvertera PDF-sidan till TIFF

Konvertera den första sidan i PDF:en till en TIFF-bild:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Steg 9: Använd Bradley Binarization Algorithm

Använd nu Bradley-algoritmen för att konvertera TIFF-bilden i gråskala till en binär bild:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 De`BinarizeBradley` Metoden tar två filströmmar (ingång och utdata) och ett tröskelvärde. Justera tröskeln efter behov för optimala resultat.

## Steg 10: Bekräfta framgångsrik konvertering

Slutligen, bekräfta att konverteringen lyckades:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Slutsats

Grattis! Du har framgångsrikt konverterat en PDF-sida till en TIFF-bild och tillämpat Bradley Binarization Algorithm med Aspose.PDF för .NET. Denna process är viktig för dokumentarkivering, OCR och andra professionella tillämpningar. Med högkvalitativ upplösning och effektiv komprimering blir dina dokumentbilder tydliga och hanterbara i storlek.

## FAQ's

### Vad är Bradley-algoritmen?
Bradley Algorithm är en binariseringsteknik som omvandlar gråskalebilder till binära bilder genom att bestämma en adaptiv tröskel för varje pixel baserat på dess omgivning.

### Kan jag konvertera flera PDF-sidor till TIFF med den här metoden?
 Ja, du kan ändra`Process` metod för att gå igenom alla sidor i dokumentet för konvertering.

### Vilken är den optimala upplösningen för att konvertera PDF-filer till TIFF?
En upplösning på 300 DPI rekommenderas generellt för bilder av hög kvalitet, men du kan justera detta utifrån dina specifika behov.

### Vad betyder 1bpp i färgdjup?
1bpp (1 bit per pixel) indikerar att bilden kommer att vara i svartvitt, där varje pixel är antingen helt svart eller helt vit.

### Är Bradley-algoritmen lämplig för OCR?
Ja, Bradley-algoritmen används ofta i OCR-förbearbetning eftersom den förbättrar kontrasten hos text i skannade dokument, vilket förbättrar igenkänningsnoggrannheten.