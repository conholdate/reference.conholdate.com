---
title: Skapa 1Bpp Indexed
linktitle: Skapa 1Bpp Indexed
second_title: Aspose.Words Document Processing API
description: Den här guiden ger steg-för-steg-instruktioner och exempelkod som hjälper dig att effektivt skapa 1Bpp-indexerade bilder för arkivering, utskrift eller utrymmesbesparande syften.
type: docs
weight: 10
url: /sv/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Introduktion

Har du någonsin behövt konvertera ett Word-dokument till en svartvit bild? Oavsett om det gäller digital arkivering, utskrift eller helt enkelt spara utrymme kan det vara otroligt användbart att konvertera dina dokument till en indexerad bild på 1Bpp. I den här guiden går vi igenom en enkel metod för att uppnå detta med Aspose.Words för .NET. Låt oss komma igång!

## Förutsättningar

Innan du dyker in i koden, se till att du har följande:

-  Aspose.Words för .NET: Ladda ner och installera biblioteket från[här](https://releases.aspose.com/words/net/).
- .NET-utvecklingsmiljö: Även om Visual Studio är ett populärt val, kommer alla IDE som stöder .NET att fungera.
- Grundläggande C#-kunskaper: Bekantskap med C# kommer att hjälpa, men vi kommer att hålla det enkelt.
- Exempel på Word-dokument: Ha ett dokument redo för konvertering.

## Steg 1: Importera nödvändiga namnområden

För att använda Aspose.Words måste du importera relevanta namnområden. Detta är viktigt för att komma åt de klasser och metoder som krävs för dokumentmanipulation.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 2: Konfigurera din dokumentkatalog

Ange sökvägen till katalogen där ditt Word-dokument är lagrat och där du vill spara den konverterade bilden.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Steg 3: Ladda Word-dokumentet

Ladda ditt Word-dokument i en`Aspose.Words.Document` objekt. Detta objekt låter dig manipulera dokumentet programmatiskt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 4: Konfigurera bildsparalternativ

 Ställ sedan in`ImageSaveOptions` för att definiera hur dokumentet ska sparas som en bild. Vi konfigurerar den för att spara i PNG-format med 1Bpp indexerat färgläge.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Konvertera endast den första sidan
    ImageColorMode = ImageColorMode.BlackAndWhite, // Ställ in på svartvitt
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Använd 1Bpp indexerat format
};
```

- SaveFormat.Png: Anger att utdataformatet ska vara PNG.
- PageSet(1): Indikerar att endast den första sidan i dokumentet kommer att konverteras.
- ImageColorMode.BlackAndWhite: Säkerställer att bilden är i svartvitt.
- ImagePixelFormat.Format1bppIndexed: Ställer in pixelformatet till 1Bpp indexerat, vilket optimerar för utrymme.

## Steg 5: Spara dokumentet som en bild

 Använd slutligen`Save` metod för`Document` objekt för att spara den konverterade bilden.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Slutsats

Grattis! Du har framgångsrikt konverterat ett Word-dokument till en 1Bpp indexerad bild med Aspose.Words för .NET. Denna metod är inte bara effektiv utan hjälper dig också att skapa bilder med hög kontrast som lämpar sig för olika applikationer. Integrera gärna denna funktion i dina projekt. Glad kodning!

## FAQ's

### Vad är en 1Bpp indexerad bild?
En 1Bpp (1 bit per pixel) indexerad bild är ett svartvitt bildformat där varje pixel representeras av en enda bit, antingen 0 eller 1. Detta format är mycket utrymmeseffektivt, vilket gör det idealiskt för arkivering.

### Kan jag konvertera flera sidor i ett Word-dokument samtidigt?
 Ja! Ändra helt enkelt`PageSet` egendom i`ImageSaveOptions` för att inkludera flera sidor eller ställa in den för att konvertera hela dokumentet.

### Behöver jag en licens för att använda Aspose.Words för .NET?
 Ja, en licens krävs för full funktionalitet. Du kan få en[tillfällig licens här](https://purchase.aspose.com/temporary-license/).

### Vilka andra bildformat kan jag konvertera mitt Word-dokument till?
 Aspose.Words stöder olika format, inklusive JPEG, BMP och TIFF. Ändra bara`SaveFormat`i`ImageSaveOptions` till önskat format.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
 För omfattande dokumentation, besök[Aspose.Words för .NET dokumentationssida](https://reference.aspose.com/words/net/).