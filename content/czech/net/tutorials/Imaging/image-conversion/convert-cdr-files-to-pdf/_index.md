---
title: Převeďte soubory CorelDRAW (CDR) do PDF pomocí Aspose.Imaging v .NET
linktitle: Převeďte soubory CorelDRAW (CDR) do PDF pomocí Aspose.Imaging v .NET
second_title: Aspose.Imaging .NET Image Processing API
description: V tomto komplexním podrobném průvodci se dozvíte, jak plynule převádět soubory CorelDRAW (CDR) do PDF pomocí Aspose.Imaging for .NET.
type: docs
weight: 10
url: /cs/net/tutorials/imaging/image-conversion/convert-cdr-files-to-pdf/
---
## Zavedení

V grafickém designu a zpracování dokumentů je převod souborů CorelDRAW (CDR) do PDF běžným požadavkem. Aspose.Imaging for .NET poskytuje efektivní způsob, jak tuto konverzi provést. Tento výukový program nabízí podrobného průvodce doplněného příklady kódu pro zajištění hladkého procesu.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

1.  Aspose.Imaging pro .NET: Stáhněte a nainstalujte jej z[Aspose webové stránky](https://releases.aspose.com/imaging/net/).
2. Soubor CDR: Připravte soubor CorelDRAW (CDR), který chcete převést.
3. Vývojové prostředí: Nechte si nastavit Visual Studio nebo jiný vývojový nástroj .NET.

## Krok 1: Importujte potřebné jmenné prostory

Začněte importováním požadovaných jmenných prostorů z Aspose.Imaging:

```csharp
using Aspose.Imaging;
using Aspose.Imaging.FileFormats.Cdr;
using Aspose.Imaging.FileFormats.Pdf;
using Aspose.Imaging.ImageOptions;
```

## Krok 2: Načtěte soubor CDR

Načtěte soubor CDR s následujícím kódem:

```csharp
string dataDir = "Your Document Directory";
string inputFileName = Path.Combine(dataDir, "YourFile.cdr");

using (var image = (VectorMultipageImage)Image.Load(inputFileName))
{
    // Pokračujte dalšími kroky
}
```

## Krok 3: Nakonfigurujte možnosti rastrování stránky

Vytvořte možnosti pro rastrování každé stránky obrazu CDR:

```csharp
var pageOptions = CreatePageOptions<CdrRasterizationOptions>(image.Size);
```

## Krok 4: Nastavte velikost stránky

Definujte metodu pro nastavení možností rastrování na základě velikosti stránky:

```csharp
private static VectorRasterizationOptions CreatePageOptions<TOptions>(Size pageSize) where TOptions : VectorRasterizationOptions, new()
{
    var options = new TOptions { PageSize = pageSize };
    return options;
}
```

## Krok 5: Vytvořte možnosti PDF

Nastavte možnosti PDF, které zahrnují vaše nastavení rastrování:

```csharp
var options = new PdfOptions
{
    MultiPageOptions = new MultiPageOptions
    {
        PageRasterizationOptions = pageOptions
    }
};
```

## Krok 6: Export do PDF

Nakonec exportujte obrázek CDR do souboru PDF se zadanými možnostmi:

```csharp
image.Save(Path.Combine(dataDir, "YourFile.pdf"), options);
```

## Krok 7: Vyčištění dočasných souborů (volitelné)

Pokud chcete soubor PDF po zpracování smazat, uveďte tento řádek:

```csharp
File.Delete(Path.Combine(dataDir, "YourFile.pdf"));
```

## Závěr

Nyní jste úspěšně převedli soubor CDR do PDF pomocí Aspose.Imaging for .NET. Tato příručka zjednodušuje proces a zajišťuje srozumitelnost každého kroku.

## FAQ

### Co je Aspose.Imaging pro .NET?
Aspose.Imaging for .NET je robustní knihovna pro zpracování různých obrazových formátů, umožňující převod, manipulaci a editační úlohy.

### Je pro Aspose.Imaging pro .NET vyžadována licence?
 Ano, pro plnou funkčnost je nutná licence, kterou lze zakoupit[zde](https://purchase.conholdate.com/buy) . K dispozici je bezplatná zkušební verze[zde](https://releases.aspose.com/).

### Lze pomocí této knihovny převést do PDF jiné obrazové formáty?
Ano, Aspose.Imaging for .NET podporuje konverzi více obrazových formátů do PDF.

### Je možná dávková konverze?
Absolutně! Aspose.Imaging for .NET zvládne dávkové konverze mnoha obrazových souborů do PDF.

### Kde najdu další dokumentaci a podporu?
 Pro důkladnou dokumentaci navštivte[Aspose Imaging Documentation](https://reference.aspose.com/imaging/net/) . Pro podporu zkontrolujte[Aspose fóra](https://forum.aspose.com/).