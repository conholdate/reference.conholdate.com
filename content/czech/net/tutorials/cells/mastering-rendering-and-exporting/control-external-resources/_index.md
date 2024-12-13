---
title: Ovládejte externí zdroje pomocí Aspose.Cells pro .NET
linktitle: Ovládejte externí zdroje pomocí Aspose.Cells pro .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Odemkněte plný potenciál svých převodů Excel do PDF pomocí Aspose.Cells pro .NET. V této obsáhlé příručce se dozvíte, jak spravovat externí zdroje, jako jsou obrázky, a zajistit, aby vaše soubory PDF přesně odpovídaly vašim požadavkům na formátování.
type: docs
weight: 12
url: /cs/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Zavedení

dnešní digitální krajině je převod tabulek Excelu na dokumenty PDF běžným a zásadním úkolem. Ať už připravujete zprávy, finanční data nebo prezentační materiály, je zásadní zajistit, aby vaše soubory PDF odpovídaly zamýšlenému formátu. Aspose.Cells for .NET poskytuje výkonnou knihovnu, která vám umožňuje podrobně řídit tento proces převodu, zejména při práci s externími zdroji, jako jsou obrázky. V této příručce prozkoumáme, jak efektivně spravovat externí zdroje během procesu převodu Excelu do PDF pomocí Aspose.Cells. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte připraveno následující:

1. Visual Studio nebo jakékoli IDE kompatibilní s .NET: Toto bude vaše vývojové prostředí.
2.  Aspose.Cells for .NET: Pokud jste jej ještě nenainstalovali, navštivte[Aspose ke stažení](https://releases.aspose.com/cells/net/) stránku pro získání nejnovější verze.
3. Základní znalost C#: Výhodou bude znalost C#. Pokud potřebujete objasnit nějaké pojmy, neváhejte si je vyhledat.
4. Ukázkový soubor aplikace Excel: Připravte soubor aplikace Excel, například „samplePdfSaveOptions_StreamProvider.xlsx“, který obsahuje externí zdroje, které chcete převést.
5. Soubor obrázku pro testování: Během převodu použijte soubor obrázku jako „newPdfSaveOptions_StreamProvider.png“ jako externí zdroj.

## Importujte potřebné balíčky

Chcete-li začít, budete muset importovat požadované jmenné prostory z knihovny Aspose.Cells. Přidejte následující pomocí direktiv v horní části souboru C#:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Tyto jmenné prostory poskytují základní třídy a metody pro vaše úkoly.

## Krok 1: Vytvořte třídu poskytovatele streamu

 Nejprve vytvořte třídu poskytovatele streamu, která implementuje`IStreamProvider` rozhraní. Tato třída vám umožní řídit, jak se načítají externí zdroje.

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
        
        // Načtěte obrázek do paměťového toku
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Tato metoda je volána, když je datový proud zavřený a aktuálně protokoluje ladicí zprávu.
- InitStream: Tato metoda načte soubor externího obrázku jako bajtové pole, převede jej na paměťový proud a přiřadí jej`options.Stream` vlastnictví.

## Krok 2: Nastavte zdrojové a výstupní adresáře

Dále definujte adresáře pro váš soubor Excel a výstupní PDF.

```csharp
// Zdrojový adresář
string sourceDir = "Your Document Directory";
// Výstupní adresář
string outputDir = "Your Document Directory";
```

 Nahradit`"Your Document Directory"` se skutečnou cestou ve vašem systému, kde jsou umístěny vaše soubory.

## Krok 3: Načtěte soubor Excel

Nyní načtěte soubor Excel, ze kterého chcete vytvořit PDF.

```csharp
// Načtěte zdrojový soubor Excel obsahující externí obrázky
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 The`Workbook` class z Aspose.Cells představuje váš soubor Excel, který může obsahovat různé externí zdroje, jako jsou obrázky.

## Krok 4: Nastavte možnosti uložení PDF

Před uložením sešitu jako PDF určete požadované možnosti uložení.

```csharp
// Zadejte možnosti uložení PDF – Poskytovatel streamu
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Uložte každý list na novou stránku
};
```

 Tím se vytvoří instance`PdfSaveOptions` , což vám umožní přizpůsobit formát PDF. The`OnePagePerSheet` Tato volba zajišťuje, že se každý list Excelu zobrazí na samostatné stránce ve výsledném PDF.

## Krok 5: Přiřaďte svého poskytovatele streamování

 Připojte svůj`Workbook` příklad s`MyStreamProvider` třídu, kterou jste dříve vytvořili.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Tento řádek zajišťuje, že kdykoli během převodu narazíte na externí zdroje, váš vlastní poskytovatel je bude odpovídajícím způsobem spravovat.

## Krok 6: Uložte sešit jako PDF

Nyní uložte sešit aplikace Excel jako PDF.

```csharp
// Uložte sešit do PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Zavoláním na`Save` metodou na objekt sešitu a předáním výstupního adresáře spolu s možnostmi PDF převedete soubor Excel do dobře formátovaného PDF.

## Krok 7: Potvrďte úspěšné provedení

Nakonec je dobrým zvykem potvrdit, že proces byl úspěšně dokončen.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Tato zpráva vás bude informovat o stavu vaší operace a poskytne užitečnou zpětnou vazbu.

## Závěr

Nyní jste zvládli proces ovládání externích zdrojů během převodů Excel do PDF pomocí Aspose.Cells! Dodržením těchto kroků můžete zajistit, aby vaše dokumenty přesně obsahovaly obrázky a další externí prvky, což pokaždé vede k vyleštěnému konečnému produktu.

## FAQ

### Co je Aspose.Cells?
Aspose.Cells je výkonná knihovna pro vývojáře .NET, která umožňuje vytváření, manipulaci, konverzi a vykreslování souborů aplikace Excel v různých formátech.

### Jak stáhnu Aspose.Cells?
 Nejnovější verzi si můžete stáhnout z[Odkaz ke stažení](https://releases.aspose.com/cells/net/).

### Mohu vyzkoušet Aspose.Cells zdarma?
 Ano! Přístup k bezplatné zkušební verzi získáte na adrese[Bezplatná zkušební stránka](https://releases.aspose.com/).

### Kde najdu podporu pro Aspose.Cells?
 Pro dotazy týkající se podpory navštivte stránku[Fórum podpory Aspose](https://forum.aspose.com/c/cells/9).

### Jak mohu získat dočasnou licenci pro Aspose.Cells?
 Můžete požádat o dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).
