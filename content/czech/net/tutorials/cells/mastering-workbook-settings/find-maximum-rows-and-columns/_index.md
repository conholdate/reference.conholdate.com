---
title: Najděte maximální počet řádků a sloupců ve formátech XLS a XLSX
linktitle: Najděte maximální počet řádků a sloupců ve formátech XLS a XLSX
second_title: Aspose.Cells .NET Excel Processing API
description: Objevte, jak efektivně spravovat velké datové sady v Excelu pomocí knihovny Aspose.Cells for .NET. Tato příručka poskytuje podrobný přístup k identifikaci maximálního počtu řádků a sloupců podporovaných formáty souborů XLS i XLSX.
type: docs
weight: 11
url: /cs/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Zavedení

Správa velkých datových sad v Excelu může být náročná, zejména s ohledem na limity různých formátů souborů. Tento tutoriál vás provede používáním knihovny Aspose.Cells for .NET k určení maximálního počtu řádků a sloupců podporovaných formáty XLS (Excel 97-2003) a XLSX (Excel 2007 a novější). Na konci budete schopni efektivně zvládnout úkoly související s Excelem.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

1. [.NET Framework](https://dotnet.microsoft.com/en-us/download) nebo[.NET Core](https://dotnet.microsoft.com/en-us/download) nainstalovaný ve vašem systému.
2. [Aspose.Cells pro .NET](https://releases.aspose.com/cells/net/) knihovna stažená a odkazovaná ve vašem projektu (můžete ji také nainstalovat přes[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Import požadovaných balíčků

Chcete-li importovat potřebné balíčky z knihovny Aspose.Cells, přidejte následující příkazy pomocí příkazů v horní části souboru C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Krok 1: Maximální počet řádků a sloupců pro formát XLS

Začněme zjištěním maximálního počtu řádků a sloupců podporovaných formátem XLS.

```csharp
// Vytiskněte zprávu o formátu XLS.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Vytvořte sešit ve formátu XLS.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Načíst maximální počet řádků a sloupců.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Zobrazit výsledky.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Vytiskněte zprávu, že pracujeme s formátem XLS.
2.  Vytvořte a`Workbook` například pro použití formátu XLS`FileFormatType.Excel97To2003`.
3.  Získejte maximální počet řádků a sloupců`wb.Settings.MaxRow` a`wb.Settings.MaxColumn`, přidáním 1, protože jsou založeny na nule.
4. Výstup maximálního počtu řádků a sloupců do konzoly.

## Krok 2: Maximální počet řádků a sloupců pro formát XLSX

Dále prozkoumáme maximální počet řádků a sloupců podporovaných formátem XLSX.

```csharp
// Vytiskněte zprávu o formátu XLSX.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Vytvořte sešit ve formátu XLSX.
wb = new Workbook(FileFormatType.Xlsx);

// Načíst maximální počet řádků a sloupců.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Zobrazit výsledky.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Vytiskněte zprávu o tom, že pracujeme s formátem XLSX.
2.  Vytvořte a`Workbook` například pro použití formátu XLSX`FileFormatType.Xlsx`.
3. Načtěte a vytiskněte maximální počet řádků a sloupců jako dříve.

## Krok 3: Zobrazení zprávy o úspěchu

Po provedení kroků označme úspěch.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Závěr

V tomto tutoriálu jste se naučili používat knihovnu Aspose.Cells for .NET k nalezení maximálního počtu řádků a sloupců podporovaných formáty souborů XLS a XLSX. Pochopení těchto limitů je nezbytné pro efektivní správu dat aplikace Excel, která zajistí, že vaše datové sady budou v souladu s možnostmi formátu.

## FAQ

### Jaký je maximální počet řádků podporovaných formátem XLS?
Maximální počet řádků podporovaných formátem XLS je 65 536.

### Jaký je maximální počet sloupců podporovaných formátem XLS?
Maximální počet sloupců podporovaných formátem XLS je 256.

### Jaký je maximální počet řádků podporovaných formátem XLSX?
Maximální počet řádků podporovaných formátem XLSX je 1 048 576.

### Jaký je maximální počet sloupců podporovaných formátem XLSX?
Maximální počet sloupců podporovaných formátem XLSX je 16 384.

### Mohu použít knihovnu Aspose.Cells for .NET s jinými formáty souborů aplikace Excel?
 Ano, Aspose.Cells for .NET podporuje různé formáty souborů, včetně XLS, XLSX, ODS a dalších. Zkontrolujte[dokumentace](https://reference.aspose.com/cells/net/) podrobnosti o podporovaných funkcích a funkcích.