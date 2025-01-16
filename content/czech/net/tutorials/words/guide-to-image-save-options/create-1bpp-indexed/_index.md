---
title: Vytvořte indexované 1Bpp
linktitle: Vytvořte indexované 1Bpp
second_title: Aspose.Words API pro zpracování dokumentů
description: Tato příručka obsahuje podrobné pokyny a ukázkový kód, které vám pomohou efektivně vytvářet indexované obrázky 1Bpp pro účely archivace, tisku nebo úspory místa.
type: docs
weight: 10
url: /cs/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Zavedení

Potřebovali jste někdy převést dokument aplikace Word na černobílý obrázek? Ať už jde o digitální archivaci, tisk nebo jen úsporu místa, převod vašich dokumentů na indexovaný obrázek 1Bpp může být neuvěřitelně užitečný. V této příručce si projdeme přímou metodu, jak toho dosáhnout pomocí Aspose.Words for .NET. Začněme!

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Stáhněte a nainstalujte knihovnu z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Přestože je Visual Studio oblíbenou volbou, bude fungovat každé IDE, které podporuje .NET.
- Základní znalost C#: Znalost C# vám pomůže, ale budeme mít věci jednoduché.
- Ukázkový dokument Word: Připravte si dokument pro převod.

## Krok 1: Importujte potřebné jmenné prostory

Chcete-li používat Aspose.Words, musíte importovat příslušné jmenné prostory. To je nezbytné pro přístup ke třídám a metodám potřebným pro manipulaci s dokumenty.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 2: Nastavte adresář dokumentů

Zadejte cestu k adresáři, kde je uložen dokument aplikace Word a kam chcete uložit převedený obrázek.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Krok 3: Načtěte dokument aplikace Word

Načtěte dokument aplikace Word do souboru`Aspose.Words.Document` objekt. Tento objekt umožňuje programově manipulovat s dokumentem.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 4: Nakonfigurujte možnosti uložení obrázku

 Dále nastavte`ImageSaveOptions` definovat, jak bude dokument uložen jako obrázek. Nakonfigurujeme jej tak, aby se ukládal ve formátu PNG s indexovaným barevným režimem 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Převeďte pouze první stránku
    ImageColorMode = ImageColorMode.BlackAndWhite, // Nastavit na černou a bílou
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Použijte indexovaný formát 1Bpp
};
```

- SaveFormat.Png: Určuje, že výstupní formát bude PNG.
- PageSet(1): Označuje, že bude převedena pouze první stránka dokumentu.
- ImageColorMode.BlackAndWhite: Zajistí, že obrázek bude černobílý.
- ImagePixelFormat.Format1bppIndexed: Nastaví formát pixelů na indexovaný 1Bpp, optimalizuje se pro prostor.

## Krok 5: Uložte dokument jako obrázek

 Nakonec použijte`Save` metoda`Document` objekt pro uložení převedeného obrázku.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Závěr

Gratuluji! Úspěšně jste převedli dokument aplikace Word na indexovaný obrázek o velikosti 1 Bpp pomocí Aspose.Words for .NET. Tato metoda je nejen efektivní, ale také vám pomůže vytvořit vysoce kontrastní obrázky vhodné pro různé aplikace. Neváhejte a integrujte tuto funkci do svých projektů. Šťastné kódování!

## FAQ

### Co je 1Bpp indexovaný obrázek?
Indexovaný obrázek 1Bpp (1 bit na pixel) je formát černobílého obrázku, kde je každý pixel reprezentován jedním bitem, buď 0, nebo 1. Tento formát je vysoce prostorově nenáročný, takže je ideální pro archivaci.

### Mohu převést více stránek dokumentu aplikace Word najednou?
 Ano! Jednoduše upravte`PageSet` nemovitost v`ImageSaveOptions` zahrnout více stránek nebo nastavit převod celého dokumentu.

### Potřebuji licenci k používání Aspose.Words pro .NET?
 Ano, pro plnou funkčnost je nutná licence. Můžete získat a[dočasná licence zde](https://purchase.aspose.com/temporary-license/).

### Na jaké další formáty obrázků mohu převést svůj dokument Word?
 Aspose.Words podporuje různé formáty, včetně JPEG, BMP a TIFF. Stačí změnit`SaveFormat` v`ImageSaveOptions`do požadovaného formátu.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Pro komplexní dokumentaci navštivte[Stránka dokumentace Aspose.Words for .NET](https://reference.aspose.com/words/net/).