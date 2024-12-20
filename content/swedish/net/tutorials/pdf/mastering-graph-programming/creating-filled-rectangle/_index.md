---
title: Skapar fylld rektangel
linktitle: Skapar fylld rektangel
second_title: Aspose.PDF för .NET API Referens
description: Lås upp kraften i PDF-manipulation med Aspose.PDF för .NET i denna steg-för-steg-handledning. Lär dig hur du programmatiskt skapar visuellt tilltalande PDF-dokument genom att rita fyllda rektanglar.
type: docs
weight: 50
url: /sv/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introduktion

Har du någonsin velat skapa visuellt fantastiska PDF-filer programmatiskt? I så fall är du på rätt plats! I den här handledningen kommer vi att utforska Aspose.PDF för .NET, ett kraftfullt bibliotek som förenklar manipulering av PDF-dokument. Idag kommer vi att fokusera på att skapa en fylld rektangel i en PDF-fil. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här guiden att leda dig genom varje steg på ett vänligt och engagerande sätt. Så ta tag i din kodningshatt och låt oss komma igång!

## Förutsättningar

Innan vi dyker in i koden, se till att du har följande:

1. Visual Studio: Installera Visual Studio på din maskin, eftersom det är en utmärkt IDE för .NET-utveckling.
2. Aspose.PDF för .NET: Ladda ner och installera Aspose.PDF-biblioteket från[här](https://releases.aspose.com/pdf/net/).
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering hjälper dig att förstå kodavsnitten bättre.

## Steg 1: Skapa ett nytt projekt

1. Öppna Visual Studio och skapa ett nytt konsolapplikationsprojekt.
2. Namnge ditt projekt på lämpligt sätt.

## Steg 2: Lägg till Aspose.PDF-referens

1. Högerklicka på ditt projekt i Solution Explorer.
2. Välj Hantera NuGet-paket.
3. Sök efter Aspose.PDF och installera den senaste versionen.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Nu när vi har allt inrättat, låt oss dyka in i koden!

## Steg 3: Konfigurera din dokumentkatalog

Ange sökvägen där din PDF ska sparas:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen på din maskin där du vill spara PDF:en.

## Steg 4: Skapa en dokumentinstans

Initiera ett nytt PDF-dokument:

```csharp
//Skapa dokumentinstans
Document doc = new Document();
```

## Steg 5: Lägg till en sida i dokumentet

Varje PDF behöver minst en sida. Låt oss lägga till en:

```csharp
// Lägg till sida till sidor samling av PDF-fil
Page page = doc.Pages.Add();
```

## Steg 6: Skapa en grafinstans

 A`Graph` instans fungerar som en duk för att rita former:

```csharp
// Skapa Graph-instans
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Steg 7: Lägg till grafen på sidan

Bifoga grafen till sidan:

```csharp
// Lägg till grafobjekt till styckesamling av sidinstanser
page.Paragraphs.Add(graph);
```

## Steg 8: Skapa en rektangelinstans

Definiera rektangelns position och storlek:

```csharp
// Skapa rektangelinstans
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Steg 9: Ange fyllningsfärg

Välj en färg för din rektangel. För det här exemplet använder vi rött:

```csharp
// Ange fyllningsfärg för Graph-objektet
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Steg 10: Lägg till rektangeln i grafen

Lägg till rektangeln i grafen:

```csharp
// Lägg till rektangelobjekt i formsamlingen av Graph-objekt
graph.Shapes.Add(rect);
```

## Steg 11: Spara PDF-dokumentet

Slutligen, spara ditt dokument i den angivna katalogen:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Spara PDF-fil
doc.Save(dataDir);
```

## Steg 12: Bekräftelsemeddelande

Skriv ut ett bekräftelsemeddelande för att indikera framgång:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Slutsats

Grattis! Du har framgångsrikt skapat en fylld rektangel i ett PDF-dokument med Aspose.PDF för .NET. Detta kraftfulla bibliotek öppnar upp en värld av möjligheter för PDF-manipulation, så att du kan skapa fantastiska dokument programmatiskt. Oavsett om du skapar rapporter, fakturor eller någon annan typ av PDF, har Aspose.PDF dig täckt.

## FAQ's

### Vad är Aspose.PDF för .NET?
Aspose.PDF för .NET är ett bibliotek som låter utvecklare skapa, manipulera och konvertera PDF-dokument programmatiskt.

### Kan jag använda Aspose.PDF gratis?
 Ja, Aspose erbjuder en gratis testversion som du kan använda för att utforska bibliotekets funktioner. Du kan ladda ner den[här](https://releases.aspose.com/).

### Finns det något sätt att få support för Aspose.PDF?
 Absolut! Du kan få support via Aspose-forumet[här](https://forum.aspose.com/c/pdf/10).

### Hur kan jag köpa Aspose.PDF?
 Du kan köpa Aspose.PDF genom att besöka köpsidan[här](https://purchase.aspose.com/buy).

### Vilka typer av former kan jag skapa med Aspose.PDF?
Du kan skapa olika former, inklusive rektanglar, cirklar, linjer och mer, med hjälp av biblioteket Aspose.PDF.