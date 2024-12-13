---
title: Justera kompressionsnivån i arbetsboken
linktitle: Justera kompressionsnivån i arbetsboken
second_title: Aspose.Cells .NET Excel Processing API
description: Upptäck hur du effektivt hanterar stora Excel-filer genom att justera komprimeringsnivåer med Aspose.Cells för .NET. Den här steg-för-steg-guiden täcker allt från att sätta upp kataloger till att mäta komprimeringstider, vilket hjälper dig att optimera filstorleken och förbättra prestandan.
type: docs
weight: 14
url: /sv/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Introduktion

Att hantera stora Excel-filer kan vara en utmaning, särskilt när det gäller lagring och överföringseffektivitet. Lyckligtvis kan filkomprimering avsevärt minska storleken på dessa filer, vilket gör dem lättare att hantera. Om du använder Aspose.Cells för .NET har du möjlighet att enkelt justera komprimeringsnivån för dina arbetsböcker. Den här guiden leder dig genom processen steg för steg, och ger tydliga förklaringar av varje del av koden.

## Förutsättningar

Innan vi dyker in i koden, se till att du har följande förutsättningar:

1. Grundläggande kunskaper i C#: Bekantskap med C#-programmering hjälper dig att förstå kodavsnitten bättre.
2.  Aspose.Cells Library: Ladda ner och installera Aspose.Cells-biblioteket från[här](https://releases.aspose.com/cells/net/).
3. Visual Studio: En utvecklingsmiljö som Visual Studio är nödvändig för att köra koden.
4. .NET Framework: Se till att ditt projekt är konfigurerat med en kompatibel version av .NET Framework.

## Importera nödvändiga paket

För att komma igång måste du importera nödvändiga paket i ditt C#-projekt. Lägg till följande rader överst i din kodfil:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Dessa paket är viktiga för att arbeta med Excel-filer med Aspose.Cells-biblioteket. De`Aspose.Cells` namespace innehåller alla klasser som behövs för att manipulera Excel-filer, while`Aspose.Cells.Xlsb` ger alternativ för att spara filer i XLSB-format.

## Steg 1: Definiera käll- och utdatakataloger

Ställ först in katalogerna där dina källfiler finns och där du vill spara utdatafilerna:

```csharp
// Definiera käll- och utdatakataloger
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Se till att byta ut`"Your Document Directory\\"` med de faktiska sökvägarna till dina kataloger. Detta säkerställer att ditt program kan hitta de filer det behöver arbeta med.

## Steg 2: Ladda arbetsboken

Ladda sedan arbetsboken som du vill komprimera:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Här skapar vi en ny instans av`Workbook` klass och ladda en befintlig Excel-fil. Se till att filnamnet matchar det i din källkatalog.

## Steg 3: Ställ in sparalternativ

Konfigurera nu sparalternativen för din arbetsbok:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 De`XlsbSaveOptions`class låter dig ange olika alternativ när du sparar din arbetsbok i XLSB-formatet, inklusive komprimeringsnivåer.

## Steg 4: Mät kompressionstid för nivå 1

Börja med den första komprimeringsnivån och mät den tid det tar att spara arbetsboken:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Det här utdraget ställer in komprimeringstypen till nivå 1, sparar arbetsboken och mäter förfluten tid.

## Steg 5: Mät kompressionstid för nivå 6

Testa sedan prestandan med nivå 6-komprimering:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Detta steg liknar det föregående, men med en högre kompressionsnivå.

## Steg 6: Mät kompressionstid för nivå 9

Slutligen, utvärdera prestandan med den högsta komprimeringsnivån:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Det här steget ställer in komprimeringsnivån till nivå 9, där du sannolikt kommer att se den mest betydande minskningen av filstorleken, även om det kan ta längre tid att bearbeta.

## Steg 7: Slutlig utdata

När du har slutfört alla komprimeringsnivåer, mata ut ett meddelande som indikerar att processen har slutförts framgångsrikt:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Denna enkla rad bekräftar att ditt program har körts utan problem.

## Slutsats

Att justera komprimeringsnivån för dina arbetsböcker med Aspose.Cells för .NET är en enkel process som kan leda till betydande förbättringar i filstorlek och prestanda. Genom att följa stegen som beskrivs i den här guiden kan du effektivt implementera komprimering i dina applikationer, vilket förbättrar dina Excel-filhanteringsmöjligheter.

## FAQ's

### Vad är Aspose.Cells?  
Aspose.Cells är ett kraftfullt bibliotek för .NET som låter utvecklare skapa, manipulera och konvertera Excel-filer utan att behöva Microsoft Excel.

### Hur installerar jag Aspose.Cells?  
 Du kan ladda ner och installera Aspose.Cells från[Aspose hemsida](https://releases.aspose.com/cells/net/).

### Vilka kompressionsnivåer finns tillgängliga?  
Aspose.Cells stöder flera komprimeringsnivåer från nivå 1 (lägsta komprimering) till nivå 9 (högsta komprimering).

### Kan jag testa Aspose.Cells gratis?  
 Ja! Du kan få en gratis provversion av Aspose.Cells[här](https://releases.aspose.com/).

### Var kan jag hitta support för Aspose.Cells?  
 För frågor eller support, besök Asposes supportforum[här](https://forum.aspose.com/c/cells/9).