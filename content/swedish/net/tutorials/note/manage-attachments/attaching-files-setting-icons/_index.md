---
title: Bifoga filer och inställningsikoner i Aspose.Note för .NET
linktitle: Bifoga fil och ange ikon i Aspose.Note
second_title: Aspose.Note .NET API
description: Lär dig steg-för-steg hur du bifogar filer och ställer in anpassade ikoner i Microsoft OneNote-dokument med Aspose.Note för .NET. Förbättra din .NET-applikation med sömlös dokumenthantering och anpassningsfunktioner.
type: docs
weight: 10
url: /sv/net/tutorials/note/manage-attachments/attaching-files-setting-icons/
---
## Introduktion

Aspose.Note for .NET är ett avancerat bibliotek designat för utvecklare att skapa, manipulera och konvertera Microsoft OneNote-filer programmatiskt. En utmärkande funktion i det här biblioteket är dess förmåga att bifoga filer till OneNote-dokument och anpassa deras ikoner. I den här guiden kommer vi att utforska hur du kan utnyttja Aspose.Note för .NET för att sömlöst bifoga filer och ställa in anpassade ikoner, vilket berikar din OneNote-dokumentfunktionalitet.

## Förutsättningar

Innan du implementerar lösningen, se till att du har följande:

- Utvecklingsmiljö: Visual Studio eller liknande IDE konfigurerad för .NET-utveckling.
-  Biblioteksinstallation: Installera[Aspose.Note för .NET](https://releases.aspose.com/words/net/) bibliotek.
- Programmeringskunskap: Grundläggande förståelse för C#.

## Importera nödvändiga namnområden

Lägg till dessa namnrymder till ditt projekt för viktig funktionalitet:

```csharp
using System.IO;
using Aspose.Note;
using System;
using System.Collections.Generic;
using System.Drawing.Imaging;
```

Nedan följer en detaljerad steg-för-steg implementering.

## Steg 1: Skapa ett nytt OneNote-dokument

 Initiera ett nytt OneNote-dokument med hjälp av`Document` klass.

```csharp
Document doc = new Document();
```

## Steg 2: Lägg till en ny sida

Lägg till en sida i dokumentet för att organisera dina anteckningar och bilagor.

```csharp
Aspose.Note.Page page = new Aspose.Note.Page(doc);
```

## Steg 3: Skapa en disposition

 Skapa en`Outline` objekt, som fungerar som behållare för element på din OneNote-sida.

```csharp
Outline outline = new Outline(doc);
```

## Steg 4: Initiera ett dispositionselement

 En`OutlineElement` kommer att hålla bilagan och dess tillhörande ikon.

```csharp
OutlineElement outlineElem = new OutlineElement(doc);
```

## Steg 5: Bifoga en fil och ange dess ikon

Ange filen som ska bifogas och ange en ikon för den.

```csharp
string dataDir = "Your Document Directory";

using (var stream = File.OpenRead(dataDir + "icon.jpg"))
{
    AttachedFile attachedFile = new AttachedFile(doc, dataDir + "attachment.txt", stream, ImageFormat.Jpeg);
    outlineElem.AppendChildLast(attachedFile);
}
```

## Steg 6: Montera dokumentstrukturen

 Lägg till`OutlineElement` till`Outline` , och`Outline` till`Page`.

```csharp
outline.AppendChildLast(outlineElem);
page.AppendChildLast(outline);
```

## Steg 7: Lägg till sidan i dokumentet

Slutligen, inkludera sidan i ditt OneNote-dokument.

```csharp
doc.AppendChildLast(page);
```

## Steg 8: Spara dokumentet

Exportera ditt uppdaterade dokument med filbilagan och ikonen.

```csharp
dataDir = dataDir + "AttachFileAndSetIcon_out.one";
doc.Save(dataDir);
```

## Slutsats

Genom att följa stegen som beskrivs i den här guiden kan du enkelt bifoga filer och ställa in anpassade ikoner i OneNote-dokument med Aspose.Note för .NET. Denna funktion kan avsevärt förbättra dokumentorganisationen och användarupplevelsen, vilket gör dina applikationer mer robusta och funktionsrika.

## FAQ's

### Kan flera filer bifogas till en enda anteckning?
Ja, du kan bifoga flera filer genom att upprepa bifogningsprocessen för varje fil.

### Vilka bildformat stöds för ikoner?
Aspose.Note stöder JPEG-, PNG-, BMP- och GIF-format för bifogade ikoner.

### Är det möjligt att bifoga filer dynamiskt från externa webbadresser?
 Du kan ladda ner filer med .NET-bibliotek som`HttpClient` och fäst dem sedan med Aspose.Note.

### Finns det några begränsningar för filstorleken för bilagor?
Det finns ingen explicit storleksgräns som införs av Aspose.Note, men se till att dina systemresurser kan hantera stora filer.

### Kan ikoner ändra storlek innan de ställs in?
Ja, du kan manipulera ikonbilden med .NET`System.Drawing` biblioteket innan du bifogar det.

 För ytterligare hjälp, utforska[dokumentation](https://reference.aspose.com/words/net/) eller nå ut till[Aspose stöd](https://forum.aspose.com/c/words/8).