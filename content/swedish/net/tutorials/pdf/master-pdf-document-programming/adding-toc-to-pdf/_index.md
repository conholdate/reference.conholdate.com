---
title: Lägga till en innehållsförteckning till ett PDF-dokument
linktitle: Lägga till en innehållsförteckning till ett PDF-dokument
second_title: Aspose.PDF för .NET API Referens
description: Denna handledning visar hur man lägger till en innehållsförteckning (TOC) till ett PDF-dokument med Aspose.Pdf för .NET.
type: docs
weight: 40
url: /sv/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Introduktion

Att skapa en innehållsförteckning (TOC) i ett PDF-dokument kan avsevärt förbättra dess navigering och tillgänglighet. I den här guiden kommer vi att visa hur man lägger till en innehållsförteckning till en PDF-fil med Aspose.Pdf för .NET.

## Förutsättningar

Innan du börjar, se till att du har följande:

1.   Aspose.PDF för .NET: Ladda ner och installera den senaste versionen från[här](https://releases.aspose.com/pdf/net/).
2.  Utvecklingsmiljö: Konfigurera en .NET-utvecklingsmiljö som Visual Studio.
3.   Licens: Begär en tillfällig licens om det behövs; besök gärna[Aspose.Pdf Licenssida](https://asposepdf.com/developers) för mer information.

Importera nödvändiga bibliotek

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Steg 1: Ladda PDF-dokumentet

Ladda din befintliga PDF-fil där du vill lägga till innehållsförteckningen. Ange sökvägen till din dokumentkatalog.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Steg 2: Infoga en ny sida för innehållsförteckning

Infoga en ny sida i början av PDF-dokumentet. Den här sidan kommer att fungera som innehållsförteckning (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Steg 3: Skapa ett TOC-informationsobjekt

Skapa ett objekt som kommer att representera TOC-informationen. Lägg till en titel och länka till den för bättre navigering.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Steg 4: Definiera TOC-element

Definiera elementen (eller rubrikerna) som kommer att visas i innehållsförteckningen. Dessa element kan hjälpa läsarna att navigera till specifika delar av dokumentet.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Steg 5: Skapa TOC-rubriker

Skapa rubriker för de två första elementen i innehållsförteckningen. Dessa rubriker kommer att länka till sina respektive sidor.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Steg 6: Spara PDF-filen med innehållsförteckningen

Slutligen, spara den uppdaterade PDF-filen.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Bekräftelsemeddelande

Visa ett bekräftelsemeddelande för att låta användaren veta att processen är klar.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Slutsats

Med Aspose.PDF för .NET är det inte bara enkelt att lägga till en innehållsförteckning till en PDF-fil utan också anpassningsbart. Oavsett om du behöver skapa enkla navigeringslänkar eller komplexa strukturer, har det här verktyget dig täckt. Så nästa gång du arbetar med en lång PDF, glöm inte att lägga till en innehållsförteckning för den professionella touchen.

## FAQ's

### Kan jag anpassa utseendet på innehållsförteckningen i Aspose.PDF?

Ja, du kan helt anpassa innehållsförteckningens utseende, inklusive teckensnitt, storlek och justering.

### Hur lägger jag till underrubriker i innehållsförteckningen?

 Du kan lägga till underrubriker genom att justera`Heading` nivå (t.ex.`Heading(2)`).

### Är det möjligt att uppdatera innehållsförteckningen automatiskt om dokumentet ändras?

Nej, innehållsförteckningen uppdateras inte automatiskt. Du måste återskapa den om dokumentstrukturen ändras.

### Kan jag länka TOC-poster till externa dokument?

Ja, du kan använda hyperlänkar för att länka TOC-poster till externa PDF-filer eller URL:er.

### Stöder Aspose.PDF innehållsförteckningar på flera nivåer?

Ja, Aspose.PDF stöder innehållsförteckningar på flera nivåer för komplexa dokument med undersektioner.
