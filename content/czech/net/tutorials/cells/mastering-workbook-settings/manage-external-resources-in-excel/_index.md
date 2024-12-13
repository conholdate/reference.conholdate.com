---
title: Spravujte externí zdroje v aplikaci Excel pomocí Aspose.Cells pro .NET
linktitle: Spravujte externí zdroje v aplikaci Excel pomocí Aspose.Cells pro .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Objevte, jak bezproblémově ovládat externí zdroje v sešitech aplikace Excel pomocí Aspose.Cells for .NET. Tento komplexní průvodce vás provede každým krokem – od implementace vlastního poskytovatele streamu až po vykreslování listů.
type: docs
weight: 10
url: /cs/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## Zavedení

Při práci s daty v Excelu může bezproblémová správa externích zdrojů výrazně zlepšit funkčnost vaší aplikace. Pokud chcete ovládat obrázky a další externí prvky v sešitech aplikace Excel pomocí Aspose.Cells pro .NET, jste na správném místě! Tato příručka vás provede procesem krok za krokem a umožní vám implementovat přizpůsobené řešení pro snadnou manipulaci s těmito zdroji.

## Předpoklady

Než se vrhneme na aspekty kódování, ujistěte se, že máte následující nastavení:

1. Visual Studio: IDE pro psaní a testování vašich aplikací .NET. Visual Studio se doporučuje pro jeho rozsáhlou podporu a uživatelsky přívětivé rozhraní.
2.  Aspose.Cells for .NET: Stáhněte si knihovnu z[Stránka vydání Aspose Cells](https://releases.aspose.com/cells/net/).
3. Základní znalost C#: Znalost konceptů C# a .NET vám pomůže lépe porozumět implementaci.
4. Nastavte svůj projekt: Ujistěte se, že váš projekt odkazuje na knihovnu Aspose.Cells, kterou můžete přidat prostřednictvím NuGet Package Manager v sadě Visual Studio.
5. Vzorové soubory: Připravte si vzorový soubor Excel, který obsahuje externí zdroje (např. propojené obrázky) pro účely demonstrace.

Jakmile máte všechny tyto předpoklady na místě, začněme spravovat externí zdroje pomocí Aspose.Cells.

## Importujte balíčky
Chcete-li začít s kódováním, budete muset importovat potřebné balíčky do souboru C#. Zde je to, co potřebujete:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## Krok 1: Definujte adresáře

Nejprve zadejte zdrojový a výstupní adresář, kde jsou uloženy vaše soubory a kam chcete uložit výstupní soubory.

```csharp
// Definujte zdrojový adresář
static string sourceDir = @"C:\Path\To\Your\Documents\"; // Přizpůsobte cestu
// Definujte výstupní adresář
static string outputDir = @"C:\Path\To\Your\Output\";
```

Ujistěte se, že jste nahradili cesty skutečnými adresáři na vašem počítači.

### Krok 2: Implementujte rozhraní IStreamProvider

 Dále vytvořte vlastní třídu, která implementuje`IStreamProvider` rozhraní. Tato třída bude řídit, jak se přistupuje k externím zdrojům, jako jsou obrázky.

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // V případě potřeby vyčistěte zdroje
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // Otevřete datový proud souboru pro externí prostředek
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 V`InitStream` otevřeme soubor, který slouží jako váš externí zdroj, a přiřadíme jej k`Stream` vlastnictví.

### Krok 3: Načtěte soubor Excel

Nyní načteme sešit aplikace Excel, který obsahuje externí zdroj.

```csharp
public static void Execute()
{
    // Načtěte soubor Excel
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // Přiřaďte vlastního poskytovatele streamu
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

Tento úryvek načte váš soubor Excel a přiřadí vlastního poskytovatele streamu pro práci s externími zdroji.

### Krok 4: Otevřete sešit

Po načtení sešitu získáte snadný přístup k požadovanému listu.

```csharp
    // Otevřete první pracovní list
    Worksheet worksheet = workbook.Worksheets[0];
```

K libovolnému listu můžete přistupovat zadáním jeho indexu.

### Krok 5: Nakonfigurujte možnosti obrázku a tisku

Nakonfigurováním možností obrázku nebo tisku definujte, jak chcete, aby výstupní obraz vypadal.

```csharp
    // Zadejte možnosti obrázku nebo tisku
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

Volba PNG zajišťuje ostrý a jasný výstup.

### Krok 6: Vykreslení listu na obrázek

Nyní přichází ta vzrušující část – vykreslení listu do obrazového souboru!

```csharp
    // Vytvořte vykreslení listu a převeďte list na obrázek
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

Tento kód převede celý list na obrázek PNG, který se uloží do zadaného výstupního adresáře.

## Závěr

Gratuluji! Nyní jste se naučili, jak ovládat externí zdroje v souborech aplikace Excel pomocí Aspose.Cells for .NET. Tato funkce nejen rozšíří možnosti vaší aplikace, ale také zjednoduší způsob správy datových sad a prezentací. Podle výše uvedených kroků můžete toto řešení přizpůsobit tak, aby vyhovovalo jedinečným požadavkům vašeho projektu.

## FAQ

### Co je Aspose.Cells?
Aspose.Cells je robustní knihovna určená pro vývojáře .NET k vytváření, manipulaci a správě souborů aplikace Excel bez nutnosti aplikace Microsoft Excel.

### Jak si mohu stáhnout Aspose.Cells pro .NET?
 Můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/cells/net/).

### Je k dispozici bezplatná zkušební verze?
 Ano! Aspose nabízí bezplatnou zkušební verzi Aspose.Cells, která je k dispozici na jejich[stránka vydání](https://releases.aspose.com/cells/net/).

### Jaké typy souborů Aspose.Cells podporuje?
Aspose.Cells podporuje různé formáty Excelu, včetně XLS, XLSX, CSV a dalších.

### Kde najdu podporu pro Aspose.Cells?
 Navštivte[Fórum Aspose](https://forum.aspose.com/c/cells/9) za pomoc a podporu komunity.