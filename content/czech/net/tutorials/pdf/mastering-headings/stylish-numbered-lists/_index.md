---
title: Stylové číslované seznamy pomocí Aspose.PDF pro .NET
linktitle: Stylové číslované seznamy pomocí Aspose.PDF pro .NET
second_title: Aspose.PDF pro .NET API Reference
description: Objevte, jak vytvořit krásně číslované seznamy v dokumentech PDF pomocí Aspose.PDF pro .NET. Tato příručka vás provede procesem použití různých stylů číslování – například římských číslic.
type: docs
weight: 10
url: /cs/net/programming-with-headings/stylish-numbered-lists/
---
## Zavedení

Potřebovali jste někdy ve svých dokumentech PDF vytvořit dobře strukturované, číslované seznamy? Ať už se jedná o právní dokumenty, zprávy nebo prezentace, efektivní styly číslování jsou zásadní pro uspořádání vašeho obsahu. S Aspose.PDF for .NET můžete snadno použít různé styly číslování na vaše nadpisy PDF, což vede k vyleštěným a profesionálním dokumentům.

## Předpoklady

Než se pustíme do kódování, ujistěte se, že máte připraveno následující:

1.  Aspose.PDF pro .NET: Stáhněte si nejnovější verzi z[zde](https://releases.aspose.com/pdf/net/).
2. Vývojové prostředí: Budete potřebovat Visual Studio nebo jakékoli IDE kompatibilní s .NET.
3. .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework 4.0 nebo vyšší.
4.  Licence: Můžete použít dočasnou licenci z[zde](https://purchase.aspose.com/temporary-license/) nebo prozkoumat[zkušební verze zdarma](https://releases.aspose.com/) možnosti.

## Import požadovaných balíčků

Začněte importováním potřebných jmenných prostorů do vašeho projektu:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Krok 1: Nastavení dokumentu

Začněme vytvořením nového dokumentu PDF a nakonfigurováním jeho rozvržení, včetně velikosti stránky a okrajů.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Nastavte rozměry a okraje stránky
pdfDoc.PageInfo.Width = 612.0; // 8,5 palce
pdfDoc.PageInfo.Height = 792.0; // 11 palců
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // 1 palec okraje
```

Toto nastavení dává dokumentu standardní velikost letter s jednopalcovými okraji na všech stranách.

## Krok 2: Přidání stránky do PDF

Dále do dokumentu PDF přidáme prázdnou stránku, kde později použijeme styly číslování.

```csharp
// Přidejte do dokumentu PDF novou stránku
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Použijte stejná nastavení jako v dokumentu
```

## Krok 3: Vytvoření plovoucího boxu

FloatingBox vám umožňuje umístit obsah nezávisle na toku stránky, což vám dává větší kontrolu nad rozložením.

```csharp
//Vytvořte FloatingBox pro strukturovaný obsah
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Krok 4: Přidání nadpisů s římskými číslicemi

Nyní přidáme náš první nadpis s číslováním malými římskými číslicemi.

```csharp
// Vytvořte první nadpis římskými číslicemi
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Krok 5: Přidání druhého nadpisu s vlastním počátečním číslem

Dále přidáme druhý nadpis, počínaje římskou číslicí 13.

```csharp
// Vytvořte druhý nadpis začínající římskou číslicí 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Krok 6: Přidání nadpisu s abecedním číslováním

Pro zpestření přidáme třetí nadpis pomocí abecedního číslování malými písmeny.

```csharp
// Vytvořte nadpis s abecedním číslováním
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Krok 7: Uložení PDF

Nakonec uložme soubor PDF do požadovaného adresáře.

```csharp
// Uložte dokument PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Závěr

Gratuluji! Úspěšně jste použili různé styly číslování – římské číslice a abecedy – na nadpisy v souboru PDF pomocí Aspose.PDF for .NET. Flexibilita Aspose.PDF vám umožňuje řídit rozvržení stránky, styly číslování a umístění obsahu, což vám umožňuje vytvářet dobře organizované a profesionální dokumenty PDF.

## FAQ

### Mohu na stejný dokument PDF použít různé styly čísel?  
Ano, v jednom dokumentu můžete kombinovat různé styly číslování, jako jsou římské číslice, arabské číslice a abecední číslování.

### Jak mohu upravit počáteční číslo pro nadpisy?  
 Počáteční číslo pro jakýkoli nadpis můžete nastavit pomocí`StartNumber` vlastnictví.

### Existuje způsob, jak resetovat posloupnost číslování?  
 Ano, číslování můžete resetovat úpravou`StartNumber` vlastnost pro každý nadpis.

### Mohu na nadpisy kromě číslování použít i tučný styl nebo kurzívu?  
 Absolutně! Styly nadpisů můžete upravit úpravou vlastností, jako je písmo, velikost, tučné písmo a kurzíva pomocí`TextState` objekt.

### Jak získám dočasnou licenci pro Aspose.PDF?  
 Dočasnou licenci můžete získat od[zde](https://purchase.aspose.com/temporary-license/) testování Aspose.PDF bez omezení.