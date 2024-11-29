---
title: Konvertera XPS till PDF med Aspose.Page för .NET
linktitle: Konvertera XPS till PDF
second_title: Aspose.Page .NET API
description: Upptäck hur du sömlöst konverterar XPS-dokument (XML Paper Specification) till PDF (Portable Document Format) med det kraftfulla Aspose.Page for .NET-biblioteket.
type: docs
weight: 11
url: /sv/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introduktion

den här handledningen kommer vi att utforska hur du konverterar XPS-dokument (XML Paper Specification) till PDF (Portable Document Format) med hjälp av det mångsidiga Aspose.Page for .NET-biblioteket. Detta kraftfulla bibliotek förenklar dokumentkonvertering och erbjuder olika anpassningsalternativ, vilket gör det till ett utmärkt val för utvecklare.

## Förutsättningar

Innan vi börjar, se till att du har följande på plats:

-  Aspose.Page for .NET Library: Ladda ner och installera Aspose.Page for .NET-biblioteket från[Aspose.Page dokumentation](https://reference.aspose.com/page/net/).
  
- Utvecklingsmiljö: Konfigurera en .NET-utvecklingsmiljö med Visual Studio eller annan kompatibel IDE.

- XPS-dokument: Ha XPS-filen som du vill konvertera redo, lagrad i en angiven katalog.

## Steg 1: Importera nödvändiga namnutrymmen

Börja med att importera det nödvändiga namnutrymmet för att komma åt Aspose.Page-funktionerna:

```csharp
using Aspose.Page.XPS;
```

## Steg 2: Initiera dokumentkatalogen

Definiera katalogsökvägen där dina dokument lagras:

```csharp
string dataDir = "Your Document Directory";
```

 Se till att byta ut`"Your Document Directory"` med den faktiska sökvägen till katalogen som innehåller ditt XPS-dokument.

### Steg 3: Öppna PDF- och XPS-strömmar

Initiera sedan strömmar för både ingångs-XPS-filen och PDF-filen:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Se till att du har angett rätt sökväg för dina filer.

### Steg 4: Ladda XPS-dokumentet

Ladda nu ditt XPS-dokument med Aspose.Page-biblioteket:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Steg 5: Konfigurera PDF-sparalternativ

Ställ in sparalternativen för din PDF, inklusive bildkvalitet och komprimeringsparametrar:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Ställ in JPEG-kvalitetsnivån
    ImageCompression = PdfImageCompression.Jpeg, // Använd JPEG-komprimering för bilder
    TextCompression = PdfTextCompression.Flate, // Använd Flate-komprimering för text
    PageNumbers = new int[] { 1, 2, 6 } // Ange sidnummer som ska inkluderas
};
```

Justera gärna dessa parametrar efter dina krav.

### Steg 6: Skapa PDF-renderingsenheten

Skapa en renderingsenhet för PDF-formatet:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Steg 7: Spara dokumentet som PDF

Slutligen, spara XPS-dokumentet till PDF med den angivna enheten och alternativen:

```csharp
document.Save(device, options);
```

## Slutsats

Grattis! Du har framgångsrikt konverterat ett XPS-dokument till PDF med Aspose.Page för .NET. Detta bibliotek förenklar inte bara dokumentkonvertering utan erbjuder också omfattande möjligheter för hantering av olika format.

## FAQ's

### Kan jag konvertera flera XPS-filer till en enda PDF?

Absolut! Du kan iterera genom flera XPS-filer och slå samman dem till ett enda PDF-dokument efter samma konverteringssteg.

### Vilka andra utdataformat stöder Aspose.Page för .NET?

Förutom PDF stöder Aspose.Page för .NET en rad olika format, inklusive TIFF, JPEG och PNG.

### Hur kan jag anpassa utseendet på den konverterade PDF-filen?

 Du kan justera parametrarna i`PdfSaveOptions` objekt, såsom JPEG-kvalitet och komprimeringsinställningar, för att uppnå önskat utseende.

### Finns det en testversion tillgänglig för Aspose.Page för .NET?

 Ja, du kan prova Aspose.Page för .NET med en gratis provperiod tillgänglig[här](https://releases.aspose.com/).

### Var kan jag hitta communitysupport för Aspose.Page för .NET?

För samhällsdiskussioner och stöd, besök[Aspose.Page forum](https://forum.aspose.com/c/page/39).