---
title: Hitta maximalt antal rader och kolumner i XLS- och XLSX-format
linktitle: Hitta maximalt antal rader och kolumner i XLS- och XLSX-format
second_title: Aspose.Cells .NET Excel Processing API
description: Upptäck hur du effektivt hanterar stora datamängder i Excel genom att använda Aspose.Cells for .NET-biblioteket. Den här guiden ger ett steg-för-steg tillvägagångssätt för att identifiera det maximala antalet rader och kolumner som stöds av både XLS- och XLSX-filformaten.
type: docs
weight: 11
url: /sv/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Introduktion

Att hantera stora datamängder i Excel kan vara utmanande, särskilt när det gäller gränserna för olika filformat. Denna handledning guidar dig genom att använda Aspose.Cells för .NET-biblioteket för att bestämma det maximala antalet rader och kolumner som stöds av formaten XLS (Excel 97-2003) och XLSX (Excel 2007 och senare). I slutet kommer du att vara rustad att hantera Excel-relaterade uppgifter effektivt.

## Förutsättningar

Innan du börjar, se till att du har följande:

1. [.NET Framework](https://dotnet.microsoft.com/en-us/download) eller[.NET Core](https://dotnet.microsoft.com/en-us/download) installerat på ditt system.
2. [Aspose.Cells för .NET](https://releases.aspose.com/cells/net/) bibliotek som laddas ner och refereras till i ditt projekt (du kan också installera det via[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Importera nödvändiga paket

Lägg till följande med hjälp av satser överst i din C#-fil för att importera nödvändiga paket från Aspose.Cells-biblioteket:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Steg 1: Maximalt antal rader och kolumner för XLS-format

Låt oss börja med att hitta det maximala antalet rader och kolumner som stöds av XLS-formatet.

```csharp
// Skriv ut meddelande om XLS-format.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Skapa en arbetsbok i XLS-format.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Hämta maximalt antal rader och kolumner.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Visa resultaten.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Skriv ut ett meddelande för att indikera att vi arbetar med XLS-formatet.
2.  Skapa en`Workbook` instans för XLS-formatet med hjälp av`FileFormatType.Excel97To2003`.
3.  Få maximalt antal rader och kolumner med`wb.Settings.MaxRow` och`wb.Settings.MaxColumn`, lägga till 1 eftersom dessa är nollbaserade.
4. Mata ut det maximala antalet rader och kolumner till konsolen.

## Steg 2: Maximalt antal rader och kolumner för XLSX-format

Därefter kommer vi att utforska det maximala antalet rader och kolumner som stöds av XLSX-formatet.

```csharp
// Skriv ut meddelande om XLSX-format.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Skapa en arbetsbok i XLSX-format.
wb = new Workbook(FileFormatType.Xlsx);

// Hämta maximalt antal rader och kolumner.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Visa resultaten.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Skriv ut ett meddelande som anger att vi arbetar med XLSX-formatet.
2.  Skapa en`Workbook` instans för XLSX-formatet med hjälp av`FileFormatType.Xlsx`.
3. Hämta och mata ut det maximala antalet rader och kolumner som tidigare.

## Steg 3: Visa ett framgångsmeddelande

Efter att ha utfört stegen, låt oss indikera framgång.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Slutsats

I den här handledningen lärde du dig hur du använder Aspose.Cells for .NET-biblioteket för att hitta maximalt antal rader och kolumner som stöds av XLS- och XLSX-filformat. Att förstå dessa gränser är viktigt för effektiv Excel-datahantering, vilket säkerställer att dina datauppsättningar är i linje med formatmöjligheter.

## FAQ's

### Vad är det maximala antalet rader som stöds av XLS-formatet?
Det maximala antalet rader som stöds av XLS-formatet är 65 536.

### Vad är det maximala antalet kolumner som stöds av XLS-formatet?
Det maximala antalet kolumner som stöds av XLS-formatet är 256.

### Vad är det maximala antalet rader som stöds av XLSX-formatet?
Det maximala antalet rader som stöds av XLSX-formatet är 1 048 576.

### Vad är det maximala antalet kolumner som stöds av XLSX-formatet?
Det maximala antalet kolumner som stöds av XLSX-formatet är 16 384.

### Kan jag använda Aspose.Cells for .NET-biblioteket med andra Excel-filformat?
 Ja, Aspose.Cells för .NET stöder olika filformat, inklusive XLS, XLSX, ODS och mer. Kontrollera[dokumentation](https://reference.aspose.com/cells/net/) för information om funktioner och funktioner som stöds.