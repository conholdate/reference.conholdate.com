---
title: Zpětné volání pro ukládání stránky v dokumentech aplikace Word
linktitle: Zpětné volání pro ukládání stránky v dokumentech aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se snadno převést každou stránku dokumentu aplikace Word na jednotlivé obrázky PNG pomocí Aspose.Words for .NET. Tato příručka poskytuje podrobné pokyny, včetně příkladů kódu.
type: docs
weight: 10
url: /cs/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Zavedení

Potřebovali jste někdy převést každou stránku dokumentu aplikace Word na jednotlivé obrázky? Ať už chcete vytvořit miniatury pro náhled nebo rozdělit zdlouhavou sestavu do stravitelných vizuálů, Aspose.Words pro .NET tento úkol zjednoduší a zefektivní. V této příručce vás provedeme procesem nastavení zpětného volání při ukládání stránky, aby se každá stránka vašeho dokumentu uložila jako obrázek PNG. Začněme!

## Předpoklady

Před potápěním se ujistěte, že máte následující:

1.  Aspose.Words for .NET: Stáhněte a nainstalujte jej z[zde](https://releases.aspose.com/words/net/).
2. Visual Studio: Bude fungovat jakákoli verze, ale pro tuto příručku použijeme Visual Studio 2019.
3. Základní znalost C#: Znalost C# vám pomůže hladce pokračovat.

## Krok 1: Importujte potřebné jmenné prostory

Nejprve musíme importovat požadované jmenné prostory. To nám umožňuje přistupovat k nezbytným třídám a metodám, aniž bychom pokaždé museli zadávat celý jmenný prostor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 2: Definujte svůj adresář dokumentů

Dále nastavte cestu k adresáři dokumentů. Zde je umístěn váš vstupní dokument aplikace Word a kde budou uloženy výstupní obrázky.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 3: Vložte svůj dokument

Nyní načteme dokument, který chcete zpracovat. Ujistěte se, že váš dokument s názvem „Rendering.docx“ je v zadaném adresáři.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 4: Nakonfigurujte možnosti uložení obrázku

Nastavíme možnosti pro ukládání obrázků a určíme, že chceme stránky uložit jako soubory PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Zde,`PageSet` definuje rozsah stránek k uložení a`PageSavingCallback` ukazuje na naši vlastní třídu zpětného volání.

## Krok 5: Implementujte zpětné volání pro ukládání stránky

Nyní musíme implementovat třídu zpětného volání, která se stará o to, jak se každá stránka ukládá.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Tato třída implementuje`IPageSavingCallback` rozhraní. V`PageSaving` způsob pojmenování specifikujeme pro každou uloženou stránku.

## Krok 6: Uložte dokument jako obrázky

Nakonec dokument uložíme pomocí nakonfigurovaných možností.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Závěr

Gratuluji! Úspěšně jste pomocí Aspose.Words for .NET nastavili zpětné volání pro uložení každé stránky dokumentu aplikace Word jako samostatný obrázek PNG. Tato technika je neuvěřitelně užitečná pro různé aplikace, od vytváření náhledů stránek až po generování jednotlivých obrázků stránek pro zprávy.

## FAQ

### Mohu ukládat stránky v jiných formátech než PNG?
 Ano! Změnou nastavení můžete stránky ukládat ve formátech, jako je JPEG, BMP a TIFF`SaveFormat` v`ImageSaveOptions`.

### Jak mohu uložit pouze konkrétní stránky?
 Chcete-li uložit konkrétní stránky, upravte`PageSet` parametr v`ImageSaveOptions` zahrnout pouze požadované stránky.

### Je možné upravit kvalitu obrazu?
 Absolutně! Kvalitu výstupního obrazu můžete ovládat nastavením vlastností jako`ImageSaveOptions.JpegQuality`.

### Jak mohu efektivně zpracovávat velké dokumenty?
U velkých dokumentů zvažte zpracování stránek v dávkách, abyste efektivně řídili využití paměti.

### Kde najdu další informace o Aspose.Words pro .NET?
 Komplexní návody a příklady naleznete na[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/).