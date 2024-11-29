---
title: Exportera CAD till Raster Image Conversion med Aspose.CAD för .NET
linktitle: Exportera CAD till Raster Image Conversion
second_title: Aspose.CAD .NET - CAD- och BIM-filformat
description: Lär dig hur du effektivt konverterar CAD-layouter till olika rasterbildsformat med Aspose.CAD för .NET. Denna omfattande guide leder dig genom processen med tydlig kod.
type: docs
weight: 10
url: /sv/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Introduktion

Vill du enkelt konvertera CAD-layouter till rasterbildsformat med Aspose.CAD för .NET? Den här steg-för-steg-guiden är utformad för att hjälpa dig att navigera i processen, komplett med kortfattade kodavsnitt för en smidig upplevelse. Oavsett om du är en erfaren utvecklare eller precis har börjat, ger den här handledningen värdefulla insikter för alla färdighetsnivåer.

## Förutsättningar

Innan du börjar, se till att du har följande:

- Aspose.CAD för .NET Library: Ladda ner och installera biblioteket från[Aspose.CAD webbplats](https://releases.aspose.com/cad/net/).
-  CAD-ritningsfil: Ha din CAD-ritningsfil (t.ex.`conic_pyramid.dxf`) redo för konvertering.

## Importera nödvändiga namnområden

I ditt .NET-projekt måste du importera nödvändiga namnområden för att använda Aspose.CAD-funktioner. Lägg till följande överst i din kod:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Steg 1: Ladda din CAD-ritning

Ange först katalogen och ladda din CAD-fil i en bildinstans:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// Ladda CAD-ritningen
using (var image = Image.Load(sourceFilePath))
{
    // Fortsätt till nästa steg
}
```

## Steg 2: Skapa rasteriseringsalternativ

Ställ sedan in rastreringsalternativen och definiera önskade dimensioner för utdatabilden:

```csharp
// Initiera CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Steg 3: Ange lager för konvertering

Om du vill konvertera specifika lager, lägg till dem i dina rasteriseringsalternativ:

```csharp
// Ange vilket lager som ska konverteras
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Steg 4: Ställ in JPEG-exportalternativ

Skapa nu alternativ för bildformatet du vill exportera till (JPEG i det här fallet):

```csharp
// Skapa JpegOptions för export
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Steg 5: Exportera till JPEG-format

Slutligen, spara den konverterade bilden:

```csharp
// Definiera utdatafilens sökväg och spara bilden
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Ytterligare funktion: Konvertera alla lager

För att konvertera alla lager i din CAD-ritning kan du implementera en metod som denna:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Iterera genom lager och spara varje som en separat JPEG-fil
    // Din implementeringskod här
}
```

## Slutsats

Grattis! Du har lärt dig hur du effektivt konverterar CAD-layouter till rasterbildsformat med Aspose.CAD för .NET. Den här guiden erbjuder ett enkelt tillvägagångssätt som lämpar sig för utvecklare som siktar på effektiva CAD-konverteringar.

## FAQ's

### Kan jag exportera till olika bildformat?

 Absolut! Byt helt enkelt`JpegOptions` med andra formatalternativ, som t.ex`PngOptions` eller`BmpOptions`, beroende på dina behov.

### Finns en testversion tillgänglig?

 Ja, du kan ladda ner en testversion för att utforska funktionaliteten genom att följa detta[länk](https://releases.aspose.com/cad/net/).

### Var kan jag hitta support för Aspose.CAD?

 För gemenskapsstöd, kolla in Aspose.CAD[forum](https://forum.aspose.com/c/cad/19), eller överväg att köpa en licens för mer dedikerad hjälp.

### Är tillfälliga licenser möjliga?

 Ja, tillfälliga licenser är tillgängliga; du kan begära en[här](https://purchase.conholdate.com/temporary-license/).

### Var kan jag få tillgång till detaljerad dokumentation?

 Besök den omfattande dokumentationen[här](https://reference.aspose.com/cad/net/) för mer information.