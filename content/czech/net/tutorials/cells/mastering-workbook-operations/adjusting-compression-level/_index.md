---
title: Úprava úrovně komprese v sešitu
linktitle: Úprava úrovně komprese v sešitu
second_title: Aspose.Cells .NET Excel Processing API
description: Objevte, jak efektivně spravovat velké soubory aplikace Excel úpravou úrovní komprese pomocí Aspose.Cells for .NET. Tento podrobný průvodce pokrývá vše od nastavení adresářů po měření kompresních časů, což vám pomůže optimalizovat velikost souboru a zvýšit výkon.
type: docs
weight: 14
url: /cs/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Zavedení

Správa velkých souborů aplikace Excel může být výzvou, zejména pokud jde o efektivitu ukládání a přenosu. Naštěstí komprese souborů může výrazně snížit velikost těchto souborů a usnadnit manipulaci s nimi. Pokud používáte Aspose.Cells pro .NET, máte možnost snadno upravit úroveň komprese vašich sešitů. Tato příručka vás provede procesem krok za krokem a poskytne jasné vysvětlení každé části kódu.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte následující předpoklady:

1. Základní znalost C#: Znalost programování v C# vám pomůže lépe porozumět úryvkům kódu.
2.  Knihovna Aspose.Cells: Stáhněte a nainstalujte knihovnu Aspose.Cells z[zde](https://releases.aspose.com/cells/net/).
3. Visual Studio: Ke spuštění kódu je nutné vývojové prostředí, jako je Visual Studio.
4. .NET Framework: Ujistěte se, že je váš projekt nastaven s kompatibilní verzí rozhraní .NET Framework.

## Import nezbytných balíčků

Chcete-li začít, musíte do svého projektu C# importovat potřebné balíčky. Přidejte následující řádky na začátek souboru kódu:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Tyto balíčky jsou nezbytné pro práci se soubory Excel pomocí knihovny Aspose.Cells. The`Aspose.Cells` jmenný prostor obsahuje všechny třídy potřebné k manipulaci se soubory aplikace Excel`Aspose.Cells.Xlsb` poskytuje možnosti pro ukládání souborů ve formátu XLSB.

## Krok 1: Definujte zdrojové a výstupní adresáře

Nejprve nastavte adresáře, kde jsou umístěny vaše zdrojové soubory a kam chcete uložit výstupní soubory:

```csharp
// Definujte zdrojové a výstupní adresáře
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Nezapomeňte vyměnit`"Your Document Directory\\"` se skutečnými cestami k vašim adresářům. To zajistí, že váš program dokáže najít soubory, se kterými potřebuje pracovat.

## Krok 2: Načtěte sešit

Dále načtěte sešit, který chcete komprimovat:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Zde vytvoříme novou instanci`Workbook` třídy a načtěte existující soubor Excel. Ujistěte se, že název souboru odpovídá názvu ve zdrojovém adresáři.

## Krok 3: Nastavte možnosti uložení

Nyní nakonfigurujte možnosti uložení sešitu:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 The`XlsbSaveOptions`class umožňuje určit různé možnosti při ukládání sešitu ve formátu XLSB, včetně úrovní komprese.

## Krok 4: Změřte dobu komprese pro úroveň 1

Začněte s první úrovní komprese a změřte čas potřebný k uložení sešitu:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Tento fragment nastaví typ komprese na úroveň 1, uloží sešit a změří uplynulý čas.

## Krok 5: Změřte dobu komprese pro úroveň 6

Dále otestujte výkon s kompresí úrovně 6:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Tento krok je podobný předchozímu, ale s vyšší úrovní komprese.

## Krok 6: Změřte dobu komprese pro úroveň 9

Nakonec vyhodnoťte výkon s nejvyšší úrovní komprese:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Tento krok nastaví úroveň komprese na úroveň 9, kde pravděpodobně zaznamenáte nejvýraznější zmenšení velikosti souboru, i když zpracování může trvat déle.

## Krok 7: Konečný výstup

Po dokončení všech úrovní komprese vydejte zprávu o úspěšném dokončení procesu:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Tento jednoduchý řádek potvrzuje, že váš program proběhl bez problémů.

## Závěr

Úprava úrovně komprese vašich sešitů pomocí Aspose.Cells for .NET je přímočarý proces, který může vést k výraznému zlepšení velikosti souboru a výkonu. Dodržováním kroků popsaných v této příručce můžete efektivně implementovat kompresi do svých aplikací a vylepšit tak možnosti správy souborů Excel.

## FAQ

### Co je Aspose.Cells?  
Aspose.Cells je výkonná knihovna pro .NET, která umožňuje vývojářům vytvářet, manipulovat a převádět soubory aplikace Excel, aniž by potřebovali Microsoft Excel.

### Jak nainstaluji Aspose.Cells?  
 Aspose.Cells si můžete stáhnout a nainstalovat z[Aspose webové stránky](https://releases.aspose.com/cells/net/).

### Jaké úrovně komprese jsou k dispozici?  
Aspose.Cells podporuje více úrovní komprese od úrovně 1 (nejnižší komprese) po úroveň 9 (nejvyšší komprese).

### Mohu testovat Aspose.Cells zdarma?  
 Ano! Můžete získat bezplatnou zkušební verzi Aspose.Cells[zde](https://releases.aspose.com/).

### Kde najdu podporu pro Aspose.Cells?  
 Máte-li jakékoli dotazy nebo podporu, navštivte fórum podpory Aspose[zde](https://forum.aspose.com/c/cells/9).