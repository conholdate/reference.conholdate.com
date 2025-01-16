---
title: Extrahujte zvuk z hypertextových odkazů v aplikaci PowerPoint pomocí Aspose.Slides
linktitle: Extrahujte zvuk z hypertextových odkazů
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Naučte se extrahovat zvuk z hypertextových odkazů v prezentacích PowerPoint pomocí Aspose.Slides for .NET. Tento průvodce krok za krokem poskytuje jasné pokyny.
type: docs
weight: 12
url: /cs/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Zavedení

multimediálních prezentacích zvuk výrazně zvyšuje účinek vašich snímků. Pokud jste se někdy setkali s powerpointovou prezentací se zvukovými hypertextovými odkazy a přemýšleli jste, jak tento zvuk extrahovat pro další použití, jste na správném místě. Tato příručka vás provede procesem extrahování zvuku z hypertextových odkazů v prezentaci PowerPoint pomocí knihovny Aspose.Slides for .NET.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

### Aspose.Slides pro knihovnu .NET

 Ujistěte se, že máte nainstalovanou knihovnu Aspose.Slides for .NET. Pokud jste tak ještě neučinili, můžete si jej stáhnout z[Aspose.Slides pro .NET dokumentaci](https://reference.aspose.com/slides/net/).

### PowerPointová prezentace se zvukovými hypertextovými odkazy

Budete potřebovat prezentaci PowerPoint (PPTX), která obsahuje hypertextové odkazy s přidruženým zvukem. Tato prezentace bude vaším zdrojem pro extrakci zvuku.

## Import požadovaných jmenných prostorů

Chcete-li efektivně používat Aspose.Slides pro .NET, budete muset do svého projektu C# importovat následující jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Nyní, když máme vše na svém místě, pojďme si rozdělit proces extrakce do jednoduchých kroků.

## Krok 1: Definujte adresář dokumentů

 Začněte zadáním adresáře, kde je umístěna vaše prezentace PowerPoint. Nahradit`"Your Document Directory"` se skutečnou cestou.

```csharp
string dataDir = "Your Document Directory";
```

## Krok 2: Načtěte prezentaci PowerPoint

 Dále načtěte prezentaci PowerPoint (PPTX), která obsahuje hypertextový odkaz na zvuk. Nahradit`"HyperlinkSound.pptx"` se skutečným názvem souboru prezentace.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Pokračujte dalším krokem.
}
```

## Krok 3: Přístup ke zvuku hypertextového odkazu

Načtěte hypertextový odkaz z prvního obrazce na prvním snímku. Pokud má tento hypertextový odkaz přidružený zvuk, můžeme přistoupit k jeho extrakci.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Pokračujte dalším krokem.
}
```

## Krok 4: Extrahujte zvuk z hypertextového odkazu

Pokud hypertextový odkaz obsahuje zvuk, můžeme jej extrahovat jako bajtové pole a uložit jako mediální soubor.

```csharp
// Extrahujte zvuk hypertextového odkazu jako bajtové pole
byte[] audioData = link.Sound.BinaryData;

// Zadejte cestu, kam chcete extrahovaný zvuk uložit
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Uložte extrahovaný zvuk do mediálního souboru
File.WriteAllBytes(outMediaPath, audioData);
```

Gratuluji! Úspěšně jste extrahovali zvuk z hypertextového odkazu v prezentaci PowerPoint pomocí Aspose.Slides for .NET. Nyní můžete tento zvuk použít ve svých multimediálních projektech.

## Závěr

Aspose.Slides for .NET nabízí výkonný a uživatelsky příjemný způsob, jak extrahovat zvuk z hypertextových odkazů v prezentacích PowerPoint. Pomocí kroků uvedených v této příručce můžete snadno znovu použít zvukový obsah z prezentací k vylepšení svých projektů.

## FAQ

### Je Aspose.Slides for .NET bezplatná knihovna?
 Ne, Aspose.Slides for .NET je komerční knihovna, ale můžete si stáhnout bezplatnou zkušební verzi a prozkoumat její funkce z[zde](https://releases.aspose.com/).

### Mohu extrahovat zvuk ze starších formátů PowerPoint, jako je PPT?
Ano, Aspose.Slides for .NET podporuje formáty PPTX i PPT pro extrakci zvuku.

### Existuje komunitní fórum pro podporu Aspose.Slides?
 Absolutně! Můžete získat pomoc a sdílet zkušenosti v[Komunitní fórum Aspose.Slides](https://forum.aspose.com/).

### Mohu si zakoupit dočasnou licenci pro Aspose.Slides pro krátkodobý projekt?
Ano, dočasnou licenci pro potřeby vašeho krátkodobého projektu můžete získat návštěvou[tento odkaz](https://purchase.aspose.com/temporary-license/).

### Jsou podporovány jiné zvukové formáty pro extrakci kromě MPG?
Ano, Aspose.Slides for .NET umožňuje extrakci v různých audio formátech. Po extrakci můžete zvuk převést do preferovaného formátu.