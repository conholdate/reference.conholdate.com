---
title: Bradleyho binarizační algoritmus
linktitle: Bradleyho binarizační algoritmus
second_title: Aspose.PDF pro .NET API Reference
description: Naučte se převádět stránky PDF na vysoce kvalitní binární obrázky TIFF pomocí binarizačního algoritmu bradley v Aspose.PDF pro .NET. Tento podrobný průvodce obsahuje příklad kódu.
type: docs
weight: 30
url: /cs/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Zavedení

tomto tutoriálu vás provedeme procesem převodu stránky PDF na obrázek TIFF pomocí Bradleyho binarizačního algoritmu. Aspose.PDF for .NET tento úkol zjednodušuje a umožňuje vám snadno automatizovat a zefektivnit pracovní toky dokumentů.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.PDF pro .NET: Stáhněte si knihovnu z[zde](https://releases.aspose.com/pdf/net/).
- Visual Studio (nebo jakékoli C# IDE).
- Základní znalost C#.
-  Platná licence nebo a[dočasná licence](https://purchase.aspose.com/temporary-license/) od Aspose.

## Krok 1: Nastavte svůj projekt

Nejprve vytvořte nový projekt C# ve svém IDE a importujte potřebné jmenné prostory:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Krok 2: Definujte adresář dokumentů

Zadejte cestu k adresáři, kde je umístěn váš dokument PDF, a také výstupní cesty pro obrázky TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Cesta k vašemu souboru PDF
```

V tomto adresáři budou uloženy jak zdrojové soubory PDF, tak převedené soubory TIFF.

## Krok 3: Načtěte dokument PDF

Otevřete dokument PDF, který chcete převést:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Nahradit`PageToTIFF.pdf` s názvem vašeho PDF souboru.

## Krok 4: Zadejte výstupní cesty

Definujte výstupní cesty pro vygenerované soubory TIFF:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Krok 5: Nastavte rozlišení obrázku

Nastavte rozlišení pro obrázky TIFF. Vyšší DPI zajistí lepší kvalitu obrazu:

```csharp
Resolution resolution = new Resolution(300);
```

## Krok 6: Nakonfigurujte nastavení TIFF

Nakonfigurujte nastavení pro obrázek TIFF, včetně komprese a barevné hloubky:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Pomocí 1bpp (1bit na pixel) připravíte obraz pro binární výstup.

## Krok 7: Vytvořte zařízení TIFF

Vytvořte zařízení TIFF, které zpracuje převod:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Krok 8: Převeďte stránku PDF na TIFF

Převeďte první stránku PDF na obrázek TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Krok 9: Použijte Bradleyův binarizační algoritmus

Nyní použijte Bradleyův algoritmus pro převod obrázku TIFF ve stupních šedi na binární obrázek:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 The`BinarizeBradley` metoda přebírá dva proudy souborů (vstup a výstup) a prahovou hodnotu. Pro optimální výsledky upravte práh podle potřeby.

## Krok 10: Potvrďte úspěšnou konverzi

Nakonec potvrďte, že převod byl úspěšný:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Závěr

Gratuluji! Úspěšně jste převedli stránku PDF na obrázek TIFF a použili jste Bradleyův binarizační algoritmus pomocí Aspose.PDF pro .NET. Tento proces je nezbytný pro archivaci dokumentů, OCR a další profesionální aplikace. Díky vysoce kvalitnímu rozlišení a účinné kompresi budou obrázky vašich dokumentů jasné a jejich velikost bude zvládnutelná.

## FAQ

### Co je to Bradleyho algoritmus?
Bradleyho algoritmus je binarizační technika, která převádí obrázky ve stupních šedi na binární obrázky určením adaptivního prahu pro každý pixel na základě jeho okolí.

### Mohu pomocí této metody převést více stránek PDF na TIFF?
 Ano, můžete upravit`Process` metoda pro procházení všech stránek v dokumentu pro převod.

### Jaké je optimální rozlišení pro převod PDF na TIFF?
Pro vysoce kvalitní obrázky se obecně doporučuje rozlišení 300 DPI, ale toto můžete upravit podle svých konkrétních potřeb.

### Co znamená 1bpp v barevné hloubce?
1bpp (1 bit na pixel) znamená, že obrázek bude černobílý, přičemž každý pixel bude buď zcela černý, nebo zcela bílý.

### Je Bradleyův algoritmus vhodný pro OCR?
Ano, Bradleyův algoritmus se často používá při předběžném zpracování OCR, protože zvyšuje kontrast textu v naskenovaných dokumentech a zlepšuje přesnost rozpoznávání.