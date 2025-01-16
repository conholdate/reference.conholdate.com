---
title: Trendové čáry v grafech s Aspose.Slides pro .NET
linktitle: Trendové čáry v grafech s Aspose.Slides pro .NET
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Naučte se přidávat a přizpůsobovat trendové čáry v grafech pomocí Aspose.Slides for .NET. Tento obsáhlý průvodce pokrývá exponenciální, lineární, logaritmické, polynomiální a klouzavý průměr trendových čar pro vylepšení vizualizace vašich dat.
type: docs
weight: 12
url: /cs/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Zavedení  

Přidání trendových čar do grafů je klíčovou technikou pro analýzu trendů dat a předpovídání budoucích hodnot. S Aspose.Slides for .NET můžete plynule přidávat a přizpůsobovat trendové čáry do prezentačních grafů a vylepšovat tak vizualizaci dat. Tato příručka poskytuje podrobný návod pro přidávání trendových čar do různých typů grafů v prezentaci PowerPoint pomocí Aspose.Slides for .NET.  

## Předpoklady  

Než se pustíme do implementace, ujistěte se, že máte následující nastavení:  

1.  Aspose.Slides for .NET: Stáhněte a nainstalujte knihovnu z[stránka ke stažení](https://releases.aspose.com/slides/net/).  
2. Vývojové prostředí: Pro kódování použijte IDE, jako je Visual Studio.  
3. Základní znalost C#: Pro absolvování tohoto návodu je nutná znalost programování v C#.  

## Import požadovaných jmenných prostorů  

Chcete-li začít, importujte do svého projektu základní jmenné prostory:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Krok 1: Nastavení prezentace  

Nejprve inicializujte prázdnou prezentaci. To bude sloužit jako kontejner pro váš graf.  

```csharp
string dataDir = "Your/Documents/Directory";

// Ujistěte se, že adresář existuje
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Vytvořte novou prezentaci
Presentation presentation = new Presentation();
```

## Krok 2: Přidání grafu na snímek  

Nyní přidejte snímek a zahrňte seskupený sloupcový graf pro vizualizaci dat.  

```csharp
// Přidejte prázdný snímek
ISlide slide = presentation.Slides[0];

// Přidejte seskupený sloupcový graf
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Krok 3: Vyplnění dat grafu  

Naplňte graf ukázkovými daty.  

```csharp
// Přístup k výchozímu sešitu dat grafu
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Aktualizujte výchozí hodnoty kategorií a řad
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Krok 4: Přidání linií trendu  

### Exponenciální trendová linie  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Lineární trendová linie  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Logaritmická trendová linie  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Trendová linie klouzavého průměru  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Polynomiální trendová čára  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Power Trend Line  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Krok 5: Uložení prezentace  

Nakonec uložte prezentaci se všemi trendovými liniemi přidanými do vašeho grafu.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Závěr  

Pomocí Aspose.Slides pro .NET se přidávání trendových čar do grafů stává přímočarým úkolem. Tato funkce vám umožní efektivně prezentovat datové trendy a přidat do vašich prezentací profesionální dotek. Chcete-li začlenit různé typy trendových čar a pozvednout vizualizaci dat, postupujte podle výše uvedených kroků.  

## FAQ  

### Mohu přizpůsobit vzhled trendových čar?  
 Ano, můžete upravit barvu, tloušťku a styl trendových čar pomocí`Format.Line` vlastnictví.  

### Existuje podpora pro jiné typy grafů?  
Ano, Aspose.Slides for .NET podporuje různé typy grafů, včetně sloupcových, koláčových a spojnicových grafů.  

### Jak zobrazím rovnice a hodnoty R-squared?  
 Umožnit`DisplayEquation` a`DisplayRSquaredValue` vlastnosti pro trendovou linii, aby se tyto hodnoty zobrazily v grafu.  

### Mohu používat Aspose.Slides pro .NET s jinými jazyky?  
Ano, knihovna je kompatibilní s jakýmkoli jazykem podporovaným .NET, včetně VB.NET a F#.  

### Kde najdu další dokumentaci?  
 Navštivte[Aspose.Slides pro dokumentaci .NET](https://reference.aspose.com/slides/net/) pro více informací.