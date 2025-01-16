---
title: Možnosti značek grafu na datovém bodu v Aspose.Slides .NET
linktitle: Možnosti značek grafu na datovém bodu v Aspose.Slides .NET
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Naučte se, jak vylepšit své PowerPoint grafy pomocí přizpůsobených možností značek pomocí Aspose.Slides pro .NET. Tento podrobný průvodce pokrývá předpoklady, vytváření grafů, formátování datových bodů a další.
type: docs
weight: 11
url: /cs/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Zavedení

Začlenění vizuálních pomůcek do prezentací je zásadní pro účinnou komunikaci. Aspose.Slides for .NET poskytuje robustní nástroje pro vytváření a přizpůsobení grafů, což umožňuje vývojářům vylepšit jejich prezentace dat. Jednou z výjimečných funkcí je možnost používat možnosti značek grafu na datových bodech, což umožňuje přesné přizpůsobení pro grafy s profesionálním vzhledem. Tento článek vás provede všemi kroky potřebnými k dosažení tohoto cíle.

## Předpoklady

Než budete pokračovat, ujistěte se, že:

-  Nainstalovaný Aspose.Slides for .NET: Stáhněte si jej z[zde](https://releases.aspose.com/slides/net/).
- Základní nastavení: Soubor prezentace, například „Test.pptx“ ve vašem pracovním adresáři.
- Vývojové prostředí: Visual Studio nebo ekvivalentní, nakonfigurované pro .NET.

## Import požadovaných jmenných prostorů

Přidejte do projektu potřebné jmenné prostory pro bezproblémový vývoj:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Krok 1: Vytvořte graf ve své prezentaci

Začněte vytvořením výchozího grafu na prvním snímku prezentace:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 To přidává a`LineWithMarkers` graf do snímku se zadanými rozměry.

## Krok 2: Načtěte index listu dat grafu

Výchozí index listu dat grafu je nezbytný pro další přizpůsobení:

```csharp
int defaultWorksheetIndex = 0;
```

## Krok 3: Otevřete sešit dat grafu

Chcete-li manipulovat s daty grafu, načtěte přidružený sešit:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Krok 4: Konfigurace řady grafů a přidání datových bodů

Vymažte výchozí řadu a přidejte nové datové body pro svou řadu:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Přidejte datové body do řady
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Krok 5: Použijte obrázkové výplně na značky datových bodů

Pomocí vlastních obrázků mohou být datové značky vizuálně přitažlivé:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Nastavte vlastní obrázky pro značky
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Krok 6: Přizpůsobte velikost značky

Upravte velikost značek, abyste zlepšili viditelnost:

```csharp
series.Marker.Size = 20;
```

## Krok 7: Uložte aktualizovanou prezentaci

Uložte přizpůsobenou prezentaci na požadované místo:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Závěr

Aspose.Slides for .NET vybavuje vývojáře nástroji pro vytváření profesionálních grafů s bohatými možnostmi přizpůsobení. Využitím možností značek grafů můžete výrazně zlepšit vizuální přitažlivost a jasnost svých prezentací. Tento podrobný průvodce zajišťuje, že i složité úpravy lze snadno implementovat.

## FAQ

### Mohu pro přizpůsobení značky použít jakýkoli formát obrázku?
Ano, Aspose.Slides podporuje různé formáty obrázků, včetně JPEG, PNG a BMP, pro přizpůsobení značek.

### Jak po vytvoření změním typ grafu?
 Chcete-li změnit typ grafu, přejděte na`chart.Type` vlastnost a přiřadit jinou`ChartType`.

### Je Aspose.Slides for .NET kompatibilní se staršími verzemi aplikace PowerPoint?
Ano, podporuje zpětnou kompatibilitu se staršími formáty PowerPoint, což zajišťuje všestrannost.

### Mohu dynamicky aktualizovat data grafu?
 Absolutně. Použijte`IChartDataWorkbook` pro programovou aktualizaci dat grafu.

### Kde najdu další zdroje?
 Prozkoumat[Dokumentace Aspose.Slides](https://reference.aspose.com/slides/net/)nebo se připojte k[komunitních fórech](https://forum.aspose.com/) za podporu.