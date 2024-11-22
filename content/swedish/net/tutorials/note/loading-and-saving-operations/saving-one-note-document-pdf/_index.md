---
title: Spara OneNote-dokument i PDF med Aspose.Note för .NET
linktitle: Spara OneNote-dokument i PDF
second_title: Aspose.Note .NET API
description: Lär dig hur du effektivt sparar Microsoft OneNote-dokument som PDF-filer med Aspose.Note för .NET. Den här guiden leder dig genom de nödvändiga förutsättningarna och erbjuder användbara vanliga frågor.
type: docs
weight: 26
url: /sv/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Introduktion

I den här handledningen kommer vi att utforska hur man sparar dokument i PDF-format med Aspose.Note för .NET. Aspose.Note är ett kraftfullt bibliotek som gör det möjligt för utvecklare att arbeta med Microsoft OneNote-filer programmatiskt. Vi kommer att täcka förutsättningarna, importera namnutrymmen och tillhandahålla steg-för-steg-guider för att spara dokument till PDF i olika sidlayouter.

## Förutsättningar
1. Visual Studio: Se till att den är installerad.
2. Aspose.Note för .NET: Ladda ner och installera biblioteket.
3. C# Kunskap: Grundläggande förståelse för språket krävs.

## Importera nödvändiga namnområden
Innan du fortsätter, importera följande namnrymder i din kod:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Steg 1: Spara till PDF med Letter Page Settings
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Uppdatera den här sökvägen
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Laddar OneNote-dokumentet och sparar det som en PDF med sidinställningar i bokstavsstorlek.

## Steg 2: Spara till PDF med A4-sidinställningar (ingen höjdgräns)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Uppdatera den här sökvägen
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Liknar steg 1 men använder A4-sidor utan höjdbegränsningar.

## Slutsats
Handledningen visar framgångsrikt hur man konverterar OneNote-filer till PDF-format med Aspose.Note. Genom att använda olika sidinställningar får utvecklare flexibilitet i dokumenthantering.

## FAQ's
### Kan Aspose.Note hantera komplexa OneNote-filer?
Ja, det hanterar effektivt olika funktioner i komplexa OneNote-filer.

### Är Aspose.Note lämplig för kommersiella projekt?
Ja, du kan använda den för kommersiella tillämpningar efter att du har köpt en licens.

### Erbjuder Aspose.Note en gratis provperiod?
Ja, en gratis provperiod är tillgänglig för utforskning.

### Var kan jag hitta dokumentation för Aspose.Note?
Detaljerad dokumentation finns tillgänglig på Asposes referenssida.

### Behöver du ytterligare hjälp?
För frågor och support, se Aspose.Note-forumet.
