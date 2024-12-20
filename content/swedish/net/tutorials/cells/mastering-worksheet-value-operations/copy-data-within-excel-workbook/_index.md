---
title: Kopiera data i Excel-arbetsbok med Aspose.Cells för .NET
linktitle: Kopiera data i Excel-arbetsbok med Aspose.Cells för .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Lär dig hur du effektivt kopierar data i en Excel-arbetsbok med Aspose.Cells för .NET. Följ den här steg-för-steg-guiden för att enkelt duplicera ark, överföra data och hantera Excel-filer med lätthet.
type: docs
weight: 12
url: /sv/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Introduktion

I den här detaljerade guiden kommer vi att visa hur man kopierar data inom samma arbetsbok med Aspose.Cells för .NET. Genom att följa de steg-för-steg-instruktioner som beskrivs nedan får du lära dig hur du programmatiskt duplicerar ark och bevarar deras innehåll och formatering.

## Förutsättningar för att kopiera data i Excel med Aspose.Cells

Innan vi går in i kodningsprocessen, låt oss se till att du har allt på plats:

1. Aspose.Cells for .NET Library: Du måste ha Aspose.Cells for .NET-biblioteket installerat. Du kan ladda ner den senaste versionen från[Aspose.Cells för .NET nedladdningssida](https://releases.aspose.com/cells/net/).
2. Utvecklingsmiljö: En .NET-kompatibel IDE som Visual Studio är nödvändig för att skriva och köra din kod.
3.  Aspose-licens: Du kan använda antingen en gratis provperiod eller en köpt licens. För mer information, besök[här](https://purchase.aspose.com/temporary-license/).

När förutsättningarna är inställda är du redo att börja arbeta med biblioteket.

## Importera nödvändiga paket

För att börja måste du importera de relevanta namnområdena från Aspose.Cells. Detta gör att du kan arbeta med Excel-filer med de klasser och metoder som tillhandahålls av Aspose.Cells.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Dessa namnutrymmen ger dig tillgång till`Workbook` klass (för att arbeta med Excel-filer) och`WorksheetCollection` (för åtkomst till flera ark i en arbetsbok).

## Steg 1: Initiera filsökvägar för arbetsbok

För att hålla din kod organiserad är det viktigt att definiera filsökvägarna där din arbetsbok finns och var du tänker spara den ändrade filen. Så här kan du ange sökvägarna:

```csharp
// Definiera katalogsökvägen där Excel-filen finns.
string dataDir = "Your Directory Path";

// Definiera den fullständiga sökvägen till inmatningsarbetsboken.
string inputPath = dataDir + "book1.xls";
```

 Ersätta`"Your Directory Path"` med den faktiska sökvägen till din katalog som innehåller arbetsboken. Detta hjälper till att säkerställa att koden är flexibel och att du kan hantera sökvägar effektivt.

## Steg 2: Öppna arbetsboken för att komma åt data

 Nu när filsökvägarna är inställda är nästa steg att ladda Excel-arbetsboken i en`Workbook` objekt. Detta låter dig komma åt dess innehåll för manipulation.

```csharp
// Ladda Excel-filen i Workbook-objektet.
Workbook wb = new Workbook(inputPath);
```

 Med den här raden har du lyckats ladda`book1.xls` in i`wb` objekt, vilket gör dess data tillgänglig.

## Steg 3: Öppna kalkylbladssamlingen

 När arbetsboken har laddats kan du komma åt arken som finns i den. Aspose.Cells tillhandahåller`Worksheets`samling, som låter dig interagera med varje kalkylblad i arbetsboken.

```csharp
// Hämta kalkylbladssamlingen från arbetsboken.
WorksheetCollection sheets = wb.Worksheets;
```

 De`sheets` objekt ger dig nu tillgång till alla kalkylblad inom`book1.xls`, och du kan utföra olika operationer på dem, inklusive kopiering av data från ett ark till ett annat.

## Steg 4: Kopiera data från ett ark till ett annat

 För att kopiera data från ett kalkylblad till ett annat inom samma arbetsbok erbjuder Aspose.Cells en lättanvänd metod som heter`AddCopy`. Den här metoden skapar en dubblett av det angivna kalkylbladet och lägger till det i arbetsboken.

```csharp
// Kopiera data från "Sheet1" till ett nytt ark i arbetsboken.
sheets.AddCopy("Sheet1");
```

 I det här exemplet kopierar vi data från "Sheet1" till ett nytt ark. De`AddCopy` metoden duplicerar hela arket och bevarar allt dess innehåll, inklusive formler, formatering och värden.

## Steg 5: Spara den modifierade arbetsboken

 Efter att ha kopierat data kan du spara den ändrade arbetsboken med ett nytt namn eller plats. Detta görs genom att ringa till`Save`metod på`Workbook` objekt.

```csharp
//Spara den ändrade arbetsboken med ett nytt namn.
wb.Save(dataDir + "book1_copy.xls");
```

 Detta kommer att spara arbetsboken med det kopierade arket som`book1_copy.xls` i den angivna katalogen. Du kan ändra filnamnet och sökvägen efter dina behov.

## Slutsats

Att kopiera data i en Excel-arbetsbok med Aspose.Cells för .NET är en enkel uppgift, och den här guiden innehåller de steg som krävs för att göra det effektivt. Oavsett om du duplicerar hela ark eller specifika dataintervall, erbjuder Aspose.Cells ett robust och flexibelt API som gör Excel-automatisering enkel och effektiv.

## FAQ's

### Kan jag kopiera flera ark samtidigt?

Aspose.Cells stöder inte kopiering av flera ark i ett enda samtal. Du kan dock gå igenom de ark du vill kopiera och kopiera dem individuellt.

### Hur kan jag byta namn på det kopierade arket?

När du har kopierat arket kan du byta namn på det enligt följande:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Är Aspose.Cells kompatibel med .NET Core?

Ja, Aspose.Cells är fullt kompatibel med både .NET Framework och .NET Core-miljöer.

### Hur hanterar Aspose.Cells formatering under kopiering?

 De`AddCopy`Metoden bevarar allt innehåll och formatering vid kopiering av ark, vilket säkerställer att den kopierade informationen ser identisk ut med originalet.

### Kan jag kopiera ett ark till en annan arbetsbok?

 Ja, du kan kopiera ett ark till en annan arbetsbok genom att använda`Copy` metod med hänvisning till målarbetsboken.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```