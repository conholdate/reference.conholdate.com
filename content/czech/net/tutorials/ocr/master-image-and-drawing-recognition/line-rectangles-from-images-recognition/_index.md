---
title: Vyjmutí čárových obdélníků z rozpoznávání obrázků
linktitle: Vyjmutí čárových obdélníků z rozpoznávání obrázků
second_title: Aspose.OCR .NET API
description: Naučte se, jak implementovat optické rozpoznávání znaků (OCR) ve vašich aplikacích .NET pomocí Aspose.OCR. Tento komplexní průvodce vás provede procesem extrahování obdélníků pro rozpoznané čáry.
type: docs
weight: 10
url: /cs/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Zavedení

Vítejte ve světě Aspose.OCR for .NET, působivého nástroje určeného k integraci optického rozpoznávání znaků (OCR) do vašich aplikací .NET. Ať už jste zkušený vývojář nebo zvědavý nováček, tento průvodce vás provede kroky k získání obdélníků představujících čáry z rozpoznaného textu v obrázcích.

## Předpoklady

Než začnete, ujistěte se, že máte na svém místě následující:

- Základní znalost vývoje C# a .NET.
- Integrované vývojové prostředí (IDE), jako je Visual Studio.
-  Nainstalována knihovna Aspose.OCR for .NET. Můžete si jej stáhnout[zde](https://releases.aspose.com/ocr/net/).
- Ukázkový obrázek obsahující text pro rozpoznání.

## Požadované jmenné prostory

Chcete-li začít, musíte do projektu přidat potřebné jmenné prostory. Zahrňte tyto řádky do horní části souboru C#:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Chcete-li načíst obdélníky pro čáry v obrazu OCR, postupujte takto.

## Krok 1: Nastavte adresář dokumentů

Zadejte adresář, kde se nachází váš soubor obrázku:

```csharp
// Definujte cestu k adresáři dokumentů
string dataDir = "Your Document Directory";
```

 Nezapomeňte vyměnit`"Your Document Directory"` se skutečnou cestou.

## Krok 2: Inicializujte Aspose.OCR

 Vytvořte instanci souboru`AsposeOcr` třídy pro přístup k jeho funkcím:

```csharp
// Inicializujte Aspose.OCR API
AsposeOcr api = new AsposeOcr();
```

## Krok 3: Zadejte cestu obrázku

Definujte úplnou cestu k souboru obrázku, který chcete zpracovat:

```csharp
// Zadejte úplnou cestu k obrázku
string fullPath = dataDir + "sample.png";
```

## Krok 4: Rozpoznejte obrázek a získejte obdélníky pro čáry

 Nyní můžete použít`GetRectangles` metoda extrahování obdélníků rozpoznaných textových řádků:

```csharp
// Načíst obdélníky pro čáry v určeném obrázku
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Krok 5: Výstup výsledků

Nakonec vytiskněte souřadnice každého detekovaného obdélníku čáry do konzoly:

```csharp
// Zobrazte souřadnice detekovaných obdélníků
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Závěr

Gratuluji! Úspěšně jste načetli obdélníky pro čáry v obrazu OCR pomocí Aspose.OCR for .NET. Tato technologie otevírá četné možnosti pro extrakci a zpracování textu ve vašich aplikacích.

## FAQ

### Mohu použít Aspose.OCR pro .NET s jakýmkoli typem obrázku?

Ano, Aspose.OCR podporuje různé formáty obrázků a poskytuje flexibilitu pro vaše aplikace OCR.

### Jaká je míra přesnosti rozpoznávání OCR?

Aspose.OCR používá pokročilé algoritmy k dosažení vysoké přesnosti v rozpoznávání textu, vhodné pro různé scénáře.

### Je k dispozici zkušební verze?

 Ano, funkce Aspose.OCR pro .NET můžete prozkoumat stažením souboru[zkušební verze zdarma](https://releases.aspose.com/).

### Kde najdu podrobnou dokumentaci?

 Komplexní dokumentaci lze nalézt[zde](https://reference.aspose.com/ocr/net/), nabízející podrobné informace a pokyny.

### Potřebujete další pomoc nebo máte otázky?

 Zapojte se do diskuze na[Fórum Aspose.OCR](https://forum.aspose.com/c/ocr/16) za podporu komunity.