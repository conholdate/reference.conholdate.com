---
title: Styr externa resurser med Aspose.Cells för .NET
linktitle: Styr externa resurser med Aspose.Cells för .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Lås upp den fulla potentialen hos dina Excel till PDF-konverteringar med Aspose.Cells för .NET. I den här omfattande guiden lär du dig hur du hanterar externa resurser, såsom bilder, för att säkerställa att dina PDF-filer återspeglar dina exakta formateringskrav.
type: docs
weight: 12
url: /sv/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Introduktion

dagens digitala landskap är konvertering av Excel-kalkylblad till PDF-dokument en vanlig och viktig uppgift. Oavsett om du förbereder rapporter, finansiella data eller presentationsmaterial är det avgörande att se till att dina PDF-filer reflekterar det avsedda formatet. Aspose.Cells för .NET tillhandahåller ett kraftfullt bibliotek som låter dig kontrollera denna konverteringsprocess i detalj, särskilt när du hanterar externa resurser som bilder. I den här guiden kommer vi att utforska hur man effektivt hanterar externa resurser under konverteringsprocessen från Excel till PDF med Aspose.Cells. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande redo:

1. Visual Studio eller någon .NET-kompatibel IDE: Detta kommer att vara din utvecklingsmiljö.
2.  Aspose.Cells för .NET: Om du inte har installerat det ännu, besök[Aspose nedladdningar](https://releases.aspose.com/cells/net/) sida för att få den senaste versionen.
3. Grundläggande kunskaper i C#: Bekantskap med C# kommer att vara fördelaktigt. Om du behöver förtydliganden om några begrepp, slå gärna upp dem.
4. Exempel på Excel-fil: Förbered en Excel-fil, till exempel "samplePdfSaveOptions_StreamProvider.xlsx," som innehåller externa resurser som du vill konvertera.
5. Bildfil för testning: Använd en bildfil som "newPdfSaveOptions_StreamProvider.png" som en extern resurs under konverteringen.

## Importera nödvändiga paket

För att börja måste du importera de nödvändiga namnrymden från Aspose.Cells-biblioteket. Lägg till följande med hjälp av direktiv överst i din C#-fil:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Dessa namnrymder tillhandahåller de viktigaste klasserna och metoderna för dina uppgifter.

## Steg 1: Skapa en strömleverantörsklass

 Skapa först en strömleverantörsklass som implementerar`IStreamProvider` gränssnitt. Denna klass gör att du kan kontrollera hur externa resurser laddas.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Ladda bilden till en minnesström
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Denna metod anropas när strömmen är stängd, för närvarande loggar ett felsökningsmeddelande.
- InitStream: Denna metod läser den externa bildfilen som en byte-array, konverterar den till en minnesström och tilldelar den till`options.Stream` egendom.

## Steg 2: Ställ in käll- och utdatakataloger

Därefter definierar du katalogerna för din Excel-fil och PDF-filen.

```csharp
// Källkatalog
string sourceDir = "Your Document Directory";
// Utdatakatalog
string outputDir = "Your Document Directory";
```

 Ersätta`"Your Document Directory"` med den faktiska sökvägen på ditt system där dina filer finns.

## Steg 3: Ladda din Excel-fil

Ladda nu Excel-filen som du vill skapa PDF-filen från.

```csharp
// Ladda källfilen i Excel som innehåller externa bilder
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 De`Workbook` klass från Aspose.Cells representerar din Excel-fil, som kan innehålla olika externa resurser som bilder.

## Steg 4: Ställ in PDF-sparalternativ

Innan du sparar arbetsboken som en PDF, ange önskade sparaalternativ.

```csharp
// Ange PDF-sparalternativ - Stream Provider
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Spara varje ark på en ny sida
};
```

 Detta skapar en instans av`PdfSaveOptions` , så att du kan anpassa PDF-formatet. De`OnePagePerSheet` alternativet säkerställer att varje Excel-ark visas på en separat sida i den slutliga PDF-filen.

## Steg 5: Tilldela din strömleverantör

 Anslut din`Workbook` exempel med`MyStreamProvider` klass du skapade tidigare.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Den här raden säkerställer att när externa resurser påträffas under konverteringen, kommer din anpassade leverantör att hantera dem därefter.

## Steg 6: Spara arbetsboken som PDF

Spara nu din Excel-arbetsbok som en PDF.

```csharp
// Spara arbetsboken till PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Genom att ringa till`Save` metod på arbetsboksobjektet och skickar utdatakatalogen tillsammans med PDF-alternativen, konverterar du Excel-filen till en välformaterad PDF.

## Steg 7: Bekräfta framgångsrik exekvering

Slutligen är det god praxis att bekräfta att processen slutfördes framgångsrikt.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Detta meddelande kommer att informera dig om statusen för din operation och ge användbar feedback.

## Slutsats

Du har nu bemästrat processen att kontrollera externa resurser under Excel till PDF-konverteringar med Aspose.Cells! Genom att följa dessa steg kan du säkerställa att dina dokument innehåller bilder och andra externa element på ett korrekt sätt, vilket resulterar i en polerad slutprodukt varje gång.

## FAQ's

### Vad är Aspose.Cells?
Aspose.Cells är ett kraftfullt bibliotek för .NET-utvecklare som gör det möjligt att skapa, manipulera, konvertera och rendera Excel-filer i olika format.

### Hur laddar jag ner Aspose.Cells?
 Du kan ladda ner den senaste versionen från[Ladda ner länk](https://releases.aspose.com/cells/net/).

### Kan jag prova Aspose.Cells gratis?
 Ja! Du kan få tillgång till en gratis provperiod genom att besöka[Gratis provsida](https://releases.aspose.com/).

### Var kan jag hitta support för Aspose.Cells?
 För supportrelaterade frågor, besök[Aspose Supportforum](https://forum.aspose.com/c/cells/9).

### Hur kan jag få en tillfällig licens för Aspose.Cells?
 Du kan ansöka om en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).
