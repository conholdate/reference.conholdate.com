---
title: Laddar lösenordsskyddade dokument
linktitle: Ladda lösenordsskyddade dokument
second_title: GroupDocs.Viewer .NET API
description: Upptäck hur du enkelt integrerar dokumentvisningsmöjligheter i dina .NET-applikationer med GroupDocs.Viewer. Denna handledning ger en omfattande, steg-för-steg-guide.
type: docs
weight: 12
url: /sv/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## Introduktion

I det digitala landskapet är förmågan att hantera och se olika dokumentformat avgörande för företag och privatpersoner. GroupDocs.Viewer för .NET erbjuder en robust lösning för utvecklare för att enkelt integrera dokumentvisningsmöjligheter i sina applikationer. Denna handledning guidar dig genom processen att ladda lösenordsskyddade dokument steg för steg, vilket säkerställer att du kan implementera den här funktionen sömlöst i dina projekt.

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  GroupDocs.Viewer för .NET installerat: Ladda ner det från[webbplats](https://releases.groupdocs.com/viewer/net/).
2. Lösenordsskyddat dokument: Ha ett lösenordsskyddat dokument redo för testning.

## Importera nödvändiga namnområden

Börja med att importera de nödvändiga namnrymden till ditt projekt:

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Steg 1: Definiera utdatakatalogen

Ange var du vill att den renderade utdata ska sparas:

```csharp
string outputDirectory = "Your Document Directory";
```
 Se till att byta ut`"Your Document Directory"` med den faktiska sökvägen du vill använda.

## Steg 2: Ställ in sidfilssökvägsformat

Definiera formatet för filsökvägarna för varje renderad sida:

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

 Detta kommer att generera vägar som`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`, etc.

## Steg 3: Konfigurera laddningsalternativ

Ställ in laddningsalternativen för ditt lösenordsskyddade dokument, inklusive lösenordet:

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  // Ersätt med ditt dokuments lösenord
};
```

## Steg 4: Initiera Viewer

Skapa en instans av GroupDocs.Viewer med ditt dokument och laddningsalternativen:

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    // Kod för visningsalternativ kommer att läggas till i nästa steg.
}
```
 Se till att byta ut`"Path_to_your_document"` med den faktiska sökvägen till ditt dokument.

## Steg 5: Konfigurera HTML-vyalternativ

Ställ in HTML-vyalternativen för att rendera dokumentet med inbäddade resurser:

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## Steg 6: Gör dokumentet

Gör nu dokumentet med de konfigurerade visnings- och visningsalternativen:

```csharp
viewer.View(options);
```

## Steg 7: Visa ett framgångsmeddelande

Slutligen, informera användaren om att dokumentet har renderats framgångsrikt:

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Slutsats

den här handledningen undersökte vi hur man laddar lösenordsskyddade dokument med GroupDocs.Viewer för .NET. Genom att följa dessa steg kan utvecklare enkelt integrera den här funktionen i sina applikationer, så att användare kan se skyddade dokument utan ansträngning.

## FAQ's

### Kan GroupDocs.Viewer hantera andra dokumentformat än lösenordsskyddade dokument?

Ja, GroupDocs.Viewer stöder ett brett utbud av format, inklusive PDF, DOCX, XLSX, PPTX och mer.

### Är GroupDocs.Viewer kompatibel med .NET Core?

Absolut! GroupDocs.Viewer är kompatibel med både .NET Framework och .NET Core-miljöer.

### Kan jag anpassa renderingsalternativen för dokumenten?

Ja, GroupDocs.Viewer erbjuder olika renderingsalternativ, så att du kan skräddarsy visningsupplevelsen efter dina behov.

### Stöder GroupDocs.Viewer dokumentkommentarer?

Ja, det stöder dokumentkommentarer, vilket gör det möjligt för användare att lägga till kommentarer, höjdpunkter och andra anteckningar.

### Finns det en testversion tillgänglig för GroupDocs.Viewer?

 Ja, du kan få en gratis provperiod från[webbplats](https://releases.groupdocs.com/).