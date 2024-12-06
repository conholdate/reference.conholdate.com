---
title: Sidspara återuppringning i Word-dokument
linktitle: Sidspara återuppringning i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du enkelt konverterar varje sida i ett Word-dokument till individuella PNG-bilder med Aspose.Words för .NET. Den här guiden ger steg-för-steg-instruktioner, inklusive kodexempel.
type: docs
weight: 10
url: /sv/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Introduktion

Har du någonsin behövt konvertera varje sida i ett Word-dokument till individuella bilder? Oavsett om du vill skapa miniatyrer för en förhandsvisning eller dela upp en lång rapport i lättsmälta bilder, gör Aspose.Words för .NET den här uppgiften enkel och effektiv. I den här guiden går vi igenom processen för att ställa in en sidsparande återuppringning för att spara varje sida i ditt dokument som en PNG-bild. Låt oss komma igång!

## Förutsättningar

Innan du dyker in, se till att du har följande:

1.  Aspose.Words för .NET: Ladda ner och installera det från[här](https://releases.aspose.com/words/net/).
2. Visual Studio: Alla versioner fungerar, men vi kommer att använda Visual Studio 2019 för den här guiden.
3. Grundläggande C#-kunskap: Bekantskap med C# hjälper dig att följa med smidigt.

## Steg 1: Importera nödvändiga namnområden

Först måste vi importera de nödvändiga namnrymden. Detta tillåter oss att komma åt de nödvändiga klasserna och metoderna utan att skriva hela namnutrymmet varje gång.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 2: Definiera din dokumentkatalog

Ange sedan sökvägen till din dokumentkatalog. Det är här ditt inmatade Word-dokument finns och där de utgående bilderna kommer att sparas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 3: Ladda ditt dokument

Låt oss nu ladda dokumentet du vill bearbeta. Se till att ditt dokument, som heter "Rendering.docx," finns i den angivna katalogen.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 4: Konfigurera bildsparalternativ

Vi ställer in alternativen för att spara bilder och anger att vi vill spara sidorna som PNG-filer.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Här,`PageSet` definierar intervallet av sidor som ska sparas, och`PageSavingCallback` pekar på vår anpassade återuppringningsklass.

## Steg 5: Implementera sidsparande återuppringning

Nu måste vi implementera callback-klassen som hanterar hur varje sida sparas.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Denna klass implementerar`IPageSavingCallback` gränssnitt. I den`PageSaving` metod, anger vi namnmönstret för varje sparad sida.

## Steg 6: Spara dokumentet som bilder

Slutligen sparar vi dokumentet med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Slutsats

Grattis! Du har framgångsrikt ställt in en sidsparande återuppringning för att spara varje sida i ett Word-dokument som en separat PNG-bild med Aspose.Words för .NET. Den här tekniken är otroligt användbar för olika applikationer, från att skapa sidförhandsvisningar till att generera individuella sidbilder för rapporter.

## FAQ's

### Kan jag spara sidor i andra format än PNG?
 Ja! Du kan spara sidor i format som JPEG, BMP och TIFF genom att ändra`SaveFormat` i`ImageSaveOptions`.

### Hur kan jag spara endast specifika sidor?
 För att spara specifika sidor, justera`PageSet` parameter in`ImageSaveOptions` att endast inkludera önskade sidor.

### Är det möjligt att anpassa bildkvaliteten?
 Absolut! Du kan styra bildkvaliteten genom att ställa in egenskaper som`ImageSaveOptions.JpegQuality`.

### Hur kan jag hantera stora dokument effektivt?
För stora dokument, överväg att bearbeta sidor i omgångar för att hantera minnesanvändningen effektivt.

### Var kan jag hitta mer information om Aspose.Words för .NET?
 För omfattande guider och exempel, kolla in[Aspose.Words dokumentation](https://reference.aspose.com/words/net/).