---
title: Převod XPS do PDF pomocí Aspose.Page pro .NET
linktitle: Převod XPS do PDF
second_title: Aspose.Page .NET API
description: Objevte, jak plynule převádět dokumenty XPS (XML Paper Specification) do PDF (Portable Document Format) pomocí výkonné knihovny Aspose.Page for .NET.
type: docs
weight: 11
url: /cs/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Zavedení

tomto tutoriálu prozkoumáme, jak převést dokumenty XPS (XML Paper Specification) do PDF (Portable Document Format) pomocí všestranné knihovny Aspose.Page for .NET. Tato výkonná knihovna zjednodušuje převod dokumentů a nabízí různé možnosti přizpůsobení, což z ní činí vynikající volbu pro vývojáře.

## Předpoklady

Než začneme, ujistěte se, že máte na svém místě následující:

-  Knihovna Aspose.Page for .NET: Stáhněte a nainstalujte knihovnu Aspose.Page for .NET z[Dokumentace Aspose.Page](https://reference.aspose.com/page/net/).
  
- Vývojové prostředí: Nastavte vývojové prostředí .NET pomocí sady Visual Studio nebo jiného kompatibilního IDE.

- Dokument XPS: Připravte si soubor XPS, který chcete převést, a uložte jej do určeného adresáře.

## Krok 1: Importujte požadované jmenné prostory

Začněte importem potřebného jmenného prostoru pro přístup k funkcím Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Krok 2: Inicializujte adresář dokumentů

Definujte cestu k adresáři, kde jsou uloženy vaše dokumenty:

```csharp
string dataDir = "Your Document Directory";
```

 Nezapomeňte vyměnit`"Your Document Directory"` se skutečnou cestou k adresáři obsahujícímu váš dokument XPS.

### Krok 3: Otevřete PDF a XPS Streams

Dále inicializujte streamy pro vstupní soubor XPS i výstupní soubor PDF:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Ujistěte se, že máte pro soubory nastavenou správnou cestu.

### Krok 4: Vložte dokument XPS

Nyní načtěte svůj dokument XPS pomocí knihovny Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Krok 5: Nakonfigurujte možnosti uložení PDF

Nastavte možnosti uložení pro váš PDF, včetně parametrů kvality obrazu a komprese:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Nastavte úroveň kvality JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Pro obrázky použijte kompresi JPEG
    TextCompression = PdfTextCompression.Flate, // Použít Flate kompresi pro text
    PageNumbers = new int[] { 1, 2, 6 } // Zadejte čísla stránek, které chcete zahrnout
};
```

Tyto parametry si klidně upravte podle svých požadavků.

### Krok 6: Vytvořte zařízení pro vykreslování PDF

Vytvořte vykreslovací zařízení pro formát PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Krok 7: Uložte dokument jako PDF

Nakonec uložte dokument XPS do PDF pomocí zadaného zařízení a možností:

```csharp
document.Save(device, options);
```

## Závěr

Gratuluji! Úspěšně jste převedli dokument XPS do PDF pomocí Aspose.Page for .NET. Tato knihovna nejen zjednodušuje převod dokumentů, ale nabízí také rozsáhlé možnosti pro práci s různými formáty.

## FAQ

### Mohu převést více souborů XPS do jednoho PDF?

Absolutně! Můžete iterovat více soubory XPS a sloučit je do jednoho dokumentu PDF pomocí stejných kroků převodu.

### Jaké další výstupní formáty Aspose.Page for .NET podporuje?

Kromě PDF podporuje Aspose.Page for .NET řadu formátů, včetně TIFF, JPEG a PNG.

### Jak mohu přizpůsobit vzhled převedeného PDF?

 Parametry můžete upravit v`PdfSaveOptions` objekt, jako je kvalita JPEG a nastavení komprese, abyste dosáhli požadovaného vzhledu.

### Je k dispozici zkušební verze pro Aspose.Page pro .NET?

 Ano, můžete vyzkoušet Aspose.Page for .NET s bezplatnou zkušební verzí[zde](https://releases.aspose.com/).

### Kde najdu podporu komunity pro Aspose.Page for .NET?

Pro diskuse a podporu komunity navštivte stránku[Fórum Aspose.Page](https://forum.aspose.com/c/page/39).