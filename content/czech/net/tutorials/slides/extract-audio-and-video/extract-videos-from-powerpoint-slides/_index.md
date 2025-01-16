---
title: Extrahujte videa z PowerPoint Slides pomocí Aspose.Slides
linktitle: Extrahujte videa z PowerPoint Slides
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Objevte, jak snadno extrahovat vložené video soubory z prezentací PowerPoint pomocí Aspose.Slides for .NET. Tento komplexní průvodce krok za krokem pokrývá vše od nastavení prostředí až po ukládání extrahovaných videí.
type: docs
weight: 14
url: /cs/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Zavedení

Aspose.Slides for .NET je výkonná knihovna, která vývojářům umožňuje programově pracovat s prezentacemi v PowerPointu. V této příručce vás provedeme procesem extrahování videí vložených do snímků aplikace PowerPoint pomocí Aspose.Slides for .NET. 

## Předpoklady

Než začnete, ujistěte se, že máte následující:

-  Aspose.Slides for .NET: Získejte a nainstalujte knihovnu z[Aspose webové stránky](https://purchase.aspose.com/buy).
-  PowerPointová prezentace: Připravte si PowerPointový soubor (např.`Video.pptx`) s videem, které chcete extrahovat.

## Nezbytné jmenné prostory

Chcete-li pracovat s Aspose.Slides pro .NET, musíte importovat příslušné jmenné prostory. Zahrňte do svého kódu následující:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Krok 1: Zadejte adresář dokumentů

Nejprve definujte cestu k prezentaci PowerPoint:

```csharp
string dataDir = "Your Document Directory";
```

 Nahradit`"Your Document Directory"` se skutečnou cestou k adresáři obsahujícímu váš soubor PowerPoint.

## Krok 2: Načtěte prezentaci

 Načtěte prezentaci PowerPoint do a`Presentation` objekt:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Tím se inicializuje`Presentation` objekt se zadaným souborem PowerPoint.

## Krok 3: Iterujte snímky a tvary

Dále procházejte každý snímek v prezentaci a zkontrolujte snímky videa:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Pokračujte v extrahování videa
        }
    }
}
```

## Krok 4: Extrahujte data videa

Jakmile najdete snímek videa, extrahujte jeho vlastnosti a binární data:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Uložte tvar jako rámeček videa
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Získejte příponu souboru
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Krok 5: Uložte video

Nakonec zapište extrahovaná data videa do souboru:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Tento kód vytvoří nový soubor ve vašem určeném adresáři a zapíše do něj data videa.

## Závěr

S Aspose.Slides pro .NET je extrahování videí ze snímků aplikace PowerPoint jednoduchý proces. Podle této příručky můžete snadno spravovat multimediální obsah ve svých aplikacích .NET a obohacovat tak uživatelskou zkušenost a funkčnost.

## FAQ

### Co je Aspose.Slides pro .NET?
Aspose.Slides for .NET je knihovna navržená pro práci s prezentacemi PowerPoint, která uživatelům umožňuje vytvářet, upravovat a manipulovat s prezentačními soubory programově.

### Kde najdu dokumentaci k Aspose.Slides pro .NET?
 Máte přístup k úplné dokumentaci[zde](https://reference.aspose.com/slides/net/).

### Je Aspose.Slides pro .NET k dispozici pro bezplatnou zkušební verzi?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tento odkaz](https://releases.aspose.com/).

### Jak mohu získat dočasnou licenci pro Aspose.Slides pro .NET?
 Je možné žádat o dočasné licence[zde](https://purchase.aspose.com/temporary-license/).

### Kde mohu získat podporu pro Aspose.Slides pro .NET?
 Podpora je k dispozici prostřednictvím[Fórum Aspose.Slides](https://forum.aspose.com/).