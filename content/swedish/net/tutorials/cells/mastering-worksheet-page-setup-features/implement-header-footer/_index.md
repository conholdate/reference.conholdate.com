---
title: Implementera sidhuvud och sidfot med Aspose.Cells för .NET
linktitle: Implementera sidhuvud och sidfot med Aspose.Cells för .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Upptäck hur du lyfter dina Excel-dokument genom att programmatiskt anpassa sidhuvuden och sidfötter med Aspose.Cells för .NET. Den här omfattande guiden leder dig genom varje steg – från att ställa in din arbetsbok till att dynamiskt infoga kalkylbladets namn.
type: docs
weight: 22
url: /sv/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Introduktion

Sidhuvuden och sidfötter är viktiga inslag i Excel-kalkylblad och ger viktig kontextuell information som filnamn, datum och sidnummer. Oavsett om du automatiserar rapporter eller genererar dynamiska filer, förenklar Aspose.Cells för .NET processen att anpassa sidhuvuden och sidfötter programmatiskt. Den här guiden erbjuder ett steg-för-steg-sätt för att förbättra dina Excel-filer med polerade och professionella sidhuvuden och sidfötter.

## Förutsättningar

Innan du dyker in, se till att du har följande:

1.  Aspose.Cells för .NET: Ladda ner och installera det från[här](https://releases.aspose.com/cells/net/).
2. IDE-installation: Använd Visual Studio eller din föredragna IDE med .NET-ramverket.
3.  Licens: Börja med en gratis provperiod, men överväg att skaffa en fullständig eller tillfällig licens för fullständig funktionalitet. Du kan[få en tillfällig licens](https://purchase.aspose.com/temporary-license/).

## Importera nödvändiga paket

Börja med att importera de nödvändiga namnrymden i ditt projekt:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Detta ger dig tillgång till de klasser och metoder som behövs för att arbeta med sidhuvuden, sidfötter och andra Excel-funktioner i Aspose.Cells.

## Steg 1: Skapa en arbetsbok och öppna sidinställningar

Börja med att skapa en ny arbetsbok och komma åt arbetsbladets sidinställningar. Det är här du kommer att ändra inställningarna för sidhuvud och sidfot.

```csharp
// Definiera sökvägen för att spara ditt dokument
string dataDir = "Your Document Directory";

// Instantiera ett arbetsboksobjekt
Workbook excel = new Workbook();
```

 Här, a`Workbook` objekt representerar din Excel-fil. De`PageSetup` egenskapen för kalkylbladet låter dig anpassa sidhuvuden och sidfötter.

## Steg 2: Öppna kalkylbladet och egenskaperna för sidinställningar

 Varje kalkylblad i Aspose.Cells har en`PageSetup` egenskap som styr layoutfunktioner, inklusive sidhuvuden och sidfötter. Skaffa`PageSetup` objekt för ditt kalkylblad:

```csharp
// Skaffa referensen till PageSetup för det första kalkylbladet
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Nu,`pageSetup` innehåller de inställningar som krävs för att anpassa sidhuvuden och sidfötter.

## Steg 3: Ställ in den vänstra delen av rubriken

Rubriker består av tre sektioner: vänster, mitten och höger. Låt oss börja med att ställa in den vänstra delen för att visa kalkylbladets namn.

```csharp
// Ange kalkylbladsnamn i den vänstra delen av rubriken
pageSetup.SetHeader(0, "&A");
```

 Använder`&A`visar kalkylbladets namn dynamiskt, vilket är särskilt användbart för arbetsböcker med flera ark.

## Steg 4: Lägg till datum och tid i mitten av rubriken

Lägg sedan till aktuellt datum och tid i mittsektionen av rubriken och använd ett anpassat teckensnitt för styling.

```csharp
// Ställ in datum och tid i mitten av rubriken med fet stil
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

På denna rad:
- `&D` infogar aktuellt datum.
- `&T` infogar aktuell tid.
- `"Times New Roman,Bold"` använder ett djärvt Times New Roman-teckensnitt.

## Steg 5: Visa filnamnet i den högra delen av rubriken

För att slutföra rubriken, visa filnamnet på höger sida med en angiven teckenstorlek.

```csharp
// Visa filnamnet i den högra delen av rubriken med anpassad teckenstorlek
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Här,`&F` representerar filnamnet och`&12` ställer in teckenstorleken till 12.

## Steg 6: Lägg till anpassad text i den vänstra sidfotssektionen

Låt oss nu ställa in den vänstra sidfotssektionen med anpassad text och en specifik typsnittsstil.

```csharp
// Lägg till anpassad text med typsnittsstil till den vänstra delen av sidfoten
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

 det här exemplet, texten`123` är formaterad med "Courier New"-teckensnittet i storlek 14, medan resten förblir i standardsidfoten.

## Steg 7: Infoga sidnummer i mitten av sidfoten

Att inkludera sidnummer i sidfoten hjälper läsarna att spåra flersidiga dokument.

```csharp
// Infoga sidnummer i mitten av sidfoten
pageSetup.SetFooter(1, "&P");
```

 De`&P` kod lägger till det aktuella sidnumret i sidfotens mittsektion.

## Steg 8: Visa totalt antal sidor i höger sidfotssektion

Komplettera sidfoten genom att visa det totala antalet sidor i det högra avsnittet.

```csharp
// Visa det totala antalet sidor i den högra delen av sidfoten
pageSetup.SetFooter(2, "&N");
```

 De`&N` koden ger det totala antalet sidor och informerar läsarna om dokumentets längd.

## Steg 9: Spara arbetsboken

Slutligen, spara arbetsboken för att generera en Excel-fil med anpassade sidhuvuden och sidfötter.

```csharp
// Spara arbetsboken
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Den här raden sparar filen med dina anpassningar på plats.

## Slutsats

Anpassning av sidhuvuden och sidfötter i Excel-kalkylblad förbättrar dina dokuments professionalism. Med Aspose.Cells för .NET kan du enkelt styra dessa element, från att visa kalkylbladsnamn till att infoga anpassad text, datum, tider och dynamiska sidnummer. Nu när du har lärt dig stegen kan du lyfta dina Excel-automationsprojekt.

## FAQ's

### Kan jag använda olika typsnitt för olika sektioner av sidhuvuden och sidfötter?
Ja, Aspose.Cells låter dig ange unika typsnitt för varje sektion av sidhuvudet och sidfoten.

### Hur tar jag bort sidhuvuden och sidfötter?
 Rensa sidhuvuden och sidfötter genom att ställa in deras text till en tom sträng med`SetHeader` eller`SetFooter`.

### Kan jag infoga bilder i sidhuvuden eller sidfötter med Aspose.Cells för .NET?
För närvarande stöder Aspose.Cells främst text i sidhuvuden och sidfötter. Bilder kan kräva alternativa metoder, som att infoga dem direkt i kalkylbladet.

### Stöder Aspose.Cells dynamisk data i sidhuvuden och sidfötter?  
 Ja, du kan använda olika dynamiska koder (som`&D`för datum eller`&P` för sidnummer) för att lägga till dynamiskt innehåll.

### Hur kan jag justera sidhuvudet eller sidfotens höjd?  
 Aspose.Cells tillhandahåller alternativ inom`PageSetup` klass för att justera sidhuvuds- och sidfotsmarginaler, vilket ger dig kontroll över avståndet.