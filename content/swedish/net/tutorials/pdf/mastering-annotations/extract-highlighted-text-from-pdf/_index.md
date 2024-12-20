---
title: Extrahera markerad text från PDF-filer med Aspose.PDF för .NET
linktitle: Extrahera markerad text från PDF-filer med Aspose.PDF för .NET
second_title: Aspose.PDF för .NET API Referens
description: Lås upp potentialen hos dina PDF-dokument genom att lära dig hur du extraherar markerad text med Aspose.PDF för .NET. Den här omfattande guiden leder dig genom varje steg, från installation till implementering.
type: docs
weight: 60
url: /sv/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Introduktion

När du arbetar med PDF-filer kan extrahering av markerad text vara avgörande för dataanalys, innehållsgranskning eller organisering av anteckningar. Om du använder Aspose.PDF för .NET har du tur. Denna handledning ger tydliga, steg-för-steg-instruktioner om hur du effektivt extraherar markerad text från ett PDF-dokument.

## Förutsättningar

Innan du börjar, se till att du har följande på plats:

-  Aspose.PDF för .NET Library: Ladda ner biblioteket från[släpp sida](https://releases.aspose.com/pdf/net/).
- Utvecklingsmiljö: En arbetsmiljö som Visual Studio.
- Grundläggande kunskaper i C#: Bekantskap med C# och objektorienterad programmering är nödvändig.
-  Aspose-licens: Även om du kan börja med en gratis provperiod, en[tillfällig licens](https://purchase.aspose.com/temporary-license/) eller en fullständig licens från[här](https://purchase.aspose.com/buy) kommer att ge obegränsad åtkomst.

## Importera nödvändiga namnområden

Börja med att importera de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Dessa namnutrymmen ger tillgång till de klasser och metoder som behövs för att hantera PDF-dokument och anteckningar.

## Steg 1: Konfigurera din projektkatalog

Ange katalogen där din PDF-fil finns:

```csharp
// Sökväg till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Se till att ersätta sökvägen med den faktiska katalogen för din PDF-fil.

## Steg 2: Ladda PDF-dokumentet

Ladda PDF-dokumentet med följande kod:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Se till att den angivna filen finns i den givna katalogen.

## Steg 3: Få åtkomst till kommentarer på sidan

För att komma åt anteckningarna, gå igenom anteckningarna på önskad sida (i det här fallet den första sidan):

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Denna kod filtrerar för`TextMarkupAnnotation` typer, som representerar höjdpunkter.

## Steg 4: Extrahera den markerade texten

Extrahera och visa nu texten från de markerade anteckningarna:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

Detta hämtar alla markerade textfragment som är associerade med markeringen och skriver ut dem till konsolen.

## Slutsats

Att extrahera markerad text från en PDF med Aspose.PDF för .NET är enkelt och kan avsevärt förbättra din dokumenthanteringsprocess. Genom att följa stegen som beskrivs ovan kan du effektivt samla in markerad text för olika applikationer, såsom rapportberedning eller dataanalys.

## FAQ's

### Kan jag extrahera andra typer av kommentarer?
 Ja, justera helt enkelt`if` villkor för att inkludera olika anteckningstyper som`TextAnnotation` eller`StampAnnotation`.

### Hur kan jag extrahera markerad text från alla PDF-sidor?
Du kan gå igenom alla sidor med:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Är en licens nödvändig för Aspose.PDF för .NET?
 En gratis provperiod är tillgänglig, men överväg en[tillfällig licens](https://purchase.aspose.com/temporary-license/) eller en fullständig licens för fullständig åtkomst.

### Kan jag spara den extraherade texten till en fil?
Absolut! Du kan ändra koden för att skriva extraherad text till en textfil.

### Stöder Aspose.PDF andra plattformar?
Ja, Aspose.PDF stöder även Java och andra plattformar, vilket ger liknande funktionalitet.