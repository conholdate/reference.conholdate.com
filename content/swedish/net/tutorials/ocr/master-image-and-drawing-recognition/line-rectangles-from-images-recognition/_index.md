---
title: Extrahera linjerektanglar från bildigenkänning
linktitle: Extrahera linjerektanglar från bildigenkänning
second_title: Aspose.OCR .NET API
description: Lär dig hur du implementerar Optical Character Recognition (OCR) i dina .NET-applikationer med Aspose.OCR. Den här omfattande guiden leder dig genom processen att extrahera rektanglar för igenkända linjer.
type: docs
weight: 10
url: /sv/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Introduktion

Välkommen till Aspose.OCR-världen för .NET, ett imponerande verktyg designat för att integrera optisk teckenigenkänning (OCR) i dina .NET-applikationer. Oavsett om du är en erfaren utvecklare eller en nyfiken nykomling, kommer den här guiden att leda dig genom stegen för att få rektanglar som representerar linjer från igenkänd text i bilder.

## Förutsättningar

Innan du börjar, se till att du har följande på plats:

- Grundläggande kunskap om C# och .NET utveckling.
- En integrerad utvecklingsmiljö (IDE) som Visual Studio.
-  Aspose.OCR för .NET-biblioteket installerat. Du kan ladda ner den[här](https://releases.aspose.com/ocr/net/).
- En exempelbild som innehåller text för igenkänning.

## Obligatoriska namnutrymmen

För att börja måste du lägga till de nödvändiga namnrymden till ditt projekt. Inkludera dessa rader överst i din C#-fil:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Följ dessa steg för att hämta rektanglar för linjer i en OCR-bild.

## Steg 1: Konfigurera din dokumentkatalog

Ange katalogen där din bildfil finns:

```csharp
// Definiera sökvägen till din dokumentkatalog
string dataDir = "Your Document Directory";
```

 Se till att byta ut`"Your Document Directory"` med den faktiska vägen.

## Steg 2: Initiera Aspose.OCR

 Skapa en instans av`AsposeOcr` klass för att komma åt dess funktioner:

```csharp
// Initiera Aspose.OCR API
AsposeOcr api = new AsposeOcr();
```

## Steg 3: Ange bildsökvägen

Definiera hela sökvägen till bildfilen du vill bearbeta:

```csharp
// Ange hela sökvägen till bilden
string fullPath = dataDir + "sample.png";
```

## Steg 4: Känn igen bild och få rektanglar för linjer

 Nu kan du använda`GetRectangles` metod för att extrahera rektanglar av igenkända textrader:

```csharp
// Hämta rektanglar för linjer i den angivna bilden
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Steg 5: Mata ut resultaten

Skriv slutligen ut koordinaterna för varje upptäckt linjerektangel till konsolen:

```csharp
// Visa koordinaterna för de upptäckta rektanglarna
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Slutsats

Grattis! Du har framgångsrikt hämtat rektanglar för linjer i en OCR-bild med Aspose.OCR för .NET. Denna teknik öppnar upp för många möjligheter för textextraktion och bearbetning i dina applikationer.

## FAQ's

### Kan jag använda Aspose.OCR för .NET med vilken typ av bild som helst?

Ja, Aspose.OCR stöder olika bildformat, vilket ger flexibilitet för dina OCR-applikationer.

### Vilken är noggrannheten för OCR-igenkänningen?

Aspose.OCR använder avancerade algoritmer för att uppnå hög noggrannhet i textigenkänning, lämplig för olika scenarier.

### Finns en testversion tillgänglig?

 Ja, du kan utforska funktionerna i Aspose.OCR för .NET genom att ladda ner[gratis provperiod](https://releases.aspose.com/).

### Var kan jag hitta detaljerad dokumentation?

 Omfattande dokumentation kan hittas[här](https://reference.aspose.com/ocr/net/), erbjuder djupgående information och riktlinjer.

### Behöver du ytterligare hjälp eller har frågor?

 Gå med i diskussionen på[Aspose.OCR-forum](https://forum.aspose.com/c/ocr/16) för samhällsstöd.