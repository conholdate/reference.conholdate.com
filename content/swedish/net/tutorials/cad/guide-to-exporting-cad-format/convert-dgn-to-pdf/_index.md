---
title: Konvertera DGN till PDF i Aspose.CAD för .NET
linktitle: Konvertera DGN till PDF i Aspose.CAD för .NET
second_title: Aspose.CAD .NET - CAD- och BIM-filformat
description: Lär dig hur du enkelt konverterar DGN-filer till PDF med det kraftfulla Aspose.CAD-biblioteket för .NET. Denna steg-för-steg-guide är designad för utvecklare på alla nivåer.
type: docs
weight: 12
url: /sv/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Introduktion

Att navigera i CAD-filernas värld kan vara utmanande, men med Aspose.CAD för .NET kan utvecklare enkelt manipulera och konvertera olika CAD-format. Ett vanligt behov är att konvertera DGN-filer till PDF-filer, som vi kommer att utforska steg för steg i den här handledningen.

## Förutsättningar

För att följa med, se till att du har följande:

- Grundläggande kunskaper i C# och .NET framework.
-  Aspose.CAD för .NET-biblioteket installerat. Du kan ladda ner den[här](https://releases.aspose.com/cad/net/).
- Ett exempel på DGN-fil (t.ex. Nikon_D90_Camera.dgn). 

## Steg 1: Importera nödvändiga namnutrymmen

Börja med att importera de relevanta namnrymden i ditt C#-projekt:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Steg 2: Ladda DGN-filen

Ange katalogen för din DGN-fil och ladda den med följande kod:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Ytterligare bearbetning kommer att gå här...
}
```

## Steg 3: Konfigurera rasteriseringsalternativ

Ställ sedan in rastreringsalternativen för att definiera hur din DGN ska renderas i PDF:en:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Justera bredden efter behov
    PageHeight = 300, // Justera höjden efter behov
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Steg 4: Skapa PDF-alternativ

Definiera PDF-alternativen, integrera rastreringsinställningarna som konfigurerats tidigare:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Steg 5: Spara DGN som en PDF

Slutligen, spara DGN-filen som en PDF med hjälp av alternativen du har konfigurerat:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Slutsats

Grattis! Du har framgångsrikt konverterat en DGN-fil till en PDF med Aspose.CAD för .NET. Denna enkla handledning guidade dig genom att ladda DGN-filen, ställa in rastreringsalternativ och spara utdata som en PDF.

## FAQ's

### Behöver jag tidigare CAD-kunskaper för att använda Aspose.CAD?  
Absolut! Aspose.CAD är designat för att förenkla komplexa CAD-uppgifter, vilket gör det tillgängligt för alla utvecklare, oavsett deras CAD-kunskaper.

### Var kan jag hitta mer resurser och dokumentation för Aspose.CAD?  
 Du kan utforska omfattande guider och exempel i[Aspose.CAD-dokumentation](https://reference.aspose.com/cad/net/).

### Finns det en gratis testversion tillgänglig för Aspose.CAD?  
 Ja, en gratis provperiod kan erhållas[här](https://releases.aspose.com/).

### Hur kan jag få en tillfällig licens för Aspose.CAD?  
 Du kan begära tillfälliga licenser[här](https://purchase.conholdate.com/temporary-license/).

### Behöver du hjälp eller har frågor?  
 Gå med i konversationen i[Aspose.CAD-forum](https://forum.aspose.com/c/cad/19) för samhällsstöd och förfrågningar.