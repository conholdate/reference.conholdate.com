---
title: Ändra PDF-sidans orientering
linktitle: Ändra PDF-sidans orientering
second_title: Aspose.PDF för .NET API Referens
description: Upptäck hur du enkelt justerar sidorienteringen för PDF-filer med Aspose.PDF för .NET. Den här steg-för-steg-guiden ger tydliga instruktioner om hur du laddar, roterar och sparar dina dokument.
type: docs
weight: 10
url: /sv/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Introduktion

Har du någonsin stött på en PDF-fil där sidriktningen är helt fel? Oavsett om det är ett dokument som har skannats felaktigt eller ett som helt enkelt behöver en annan layout, kan justering av orienteringen göra en värld av skillnad. Lyckligtvis erbjuder Aspose.PDF för .NET ett kraftfullt och användarvänligt sätt att manipulera PDF-filer, inklusive att ändra orienteringen på sidorna. I den här guiden går vi igenom processen steg-för-steg, oavsett om du vill byta från stående till liggande eller vice versa.

## Förutsättningar

Innan vi dyker in i detaljerna, se till att du har följande på plats:

-  Aspose.PDF för .NET: Se till att du har Aspose.PDF-biblioteket installerat. Om du inte har gjort det här än så kan du[ladda ner den här](https://releases.aspose.com/pdf/net/).
- En .NET-utvecklingsmiljö: Du kan använda Visual Studio, JetBrains Rider eller vilken annan IDE du föredrar för .NET-utveckling.
- Grundläggande kunskaper om C#: Bekantskap med C# hjälper dig att följa med lättare.
- En PDF-fil: Ha ett exempel på en PDF-fil redo för testning. Du kan skapa en eller ladda ner ett prov online.

 Om du precis har börjat, överväg att prova Aspose.PDF med en[gratis tillfällig licens](https://purchase.aspose.com/temporary-license/) innan du bestämmer dig för det[köpa den fullständiga versionen](https://purchase.aspose.com/buy).

## Importera namnområden

För att manipulera PDF-sidor måste du först importera de nödvändiga namnrymden i ditt C#-projekt. Lägg till följande rader överst i din kodfil:

```csharp
using System.IO;
using Aspose.Pdf;
```

Nu när vi har allt klart, låt oss komma igång!

## Steg 1: Ladda PDF-dokumentet

 Det första steget är att ladda PDF-filen du vill ändra. Använd`Document` klass från namnområdet Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Se till att byta ut`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din PDF-fil.

## Steg 2: Gå igenom varje sida

Därefter går vi igenom varje sida i PDF-dokumentet. Detta gör att vi kan tillämpa orienteringsändringen på alla sidor:

```csharp
foreach (Page page in doc.Pages)
{
    // Manipulera varje sida
}
```

## Steg 3: Öppna sidans MediaBox

 Varje PDF-sida har en`MediaBox` som definierar dess gränser. Vi måste komma åt detta för att kontrollera den aktuella orienteringen och göra justeringar:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 De`MediaBox` ger sidans mått, inklusive bredd och höjd.

## Steg 4: Byt bredd och höjd

För att ändra sidriktningen byter vi bredd- och höjdvärdena. Denna justering kommer att ändra dimensionerna på sidan:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Här beräknar vi de nya dimensionerna och placerar om det nedre vänstra hörnet (`LLY`) i enlighet med detta.

## Steg 5: Uppdatera MediaBox och CropBox

 Nu när vi har de nya dimensionerna kommer vi att tillämpa dessa ändringar på`MediaBox` och`CropBox` för att säkerställa att sidan visas korrekt:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Steg 6: Rotera sidan

För att slutföra orienteringsändringen roterar vi sidan. Detta är enkelt med Aspose.PDF:

```csharp
page.Rotate = Rotation.on90; // Vrid 90 grader
```

Denna rad vänder effektivt sidan till önskad orientering.

## Steg 7: Spara PDF-filen

Efter att ha ändrat orienteringen på alla sidor, spara det uppdaterade dokumentet i en ny fil:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Se till att ange ett nytt filnamn för att undvika att skriva över originaldokumentet.

## Slutsats

Och där har du det! Att ändra sidriktningen för en PDF-fil med Aspose.PDF för .NET är en enkel process. Genom att ladda dokumentet, gå igenom sidorna, uppdatera MediaBox och spara filen kan du enkelt anpassa layouten för att möta dina behov. Oavsett om du korrigerar ett dåligt skannat dokument eller formaterar sidor för presentation, bör den här guiden hjälpa dig att få jobbet gjort effektivt.

## FAQ's

### Kan jag rotera specifika sidor istället för alla sidor i PDF-filen?  
Ja, du kan modifiera slingan för att rikta in sig på specifika sidor genom deras index istället för att iterera genom alla sidor.

### Vad är`MediaBox`?  
 De`MediaBox` definierar storleken och formen på sidan i en PDF-fil, och bestämmer var innehållet placeras.

### Fungerar Aspose.PDF för .NET med andra filformat?  
Ja, Aspose.PDF kan hantera olika filformat, inklusive HTML, XML, XPS och mer.

### Finns det en gratisversion av Aspose.PDF för .NET?  
 Ja, du kan börja med en[gratis provperiod](https://releases.aspose.com/) eller begära en[tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Kan jag ångra ändringarna när de har sparats?  
När du har sparat dokumentet är ändringarna permanenta. Det är tillrådligt att arbeta på en kopia eller behålla en säkerhetskopia av originalfilen.