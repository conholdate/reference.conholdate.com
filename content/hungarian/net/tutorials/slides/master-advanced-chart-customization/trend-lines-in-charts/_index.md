---
title: Trendvonalak diagramokon az Aspose.Slides segítségével .NET-hez
linktitle: Trendvonalak diagramokon az Aspose.Slides segítségével .NET-hez
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Ismerje meg, hogyan adhat hozzá trendvonalakat és hogyan szabhat testre diagramokat az Aspose.Slides for .NET segítségével. Ez az átfogó útmutató az adatok megjelenítésének javítása érdekében exponenciális, lineáris, logaritmikus, polinomiális és mozgóátlagos trendvonalakat tartalmaz.
type: docs
weight: 12
url: /hu/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Bevezetés  

A trendvonalak diagramokhoz való hozzáadása kulcsfontosságú technika az adattrendek elemzéséhez és a jövőbeli értékek előrejelzéséhez. Az Aspose.Slides for .NET segítségével zökkenőmentesen hozzáadhat és testreszabhat trendvonalakat prezentációs diagramjaihoz, javítva az adatok megjelenítését. Ez az útmutató részletes áttekintést nyújt a trendvonalak különféle diagramtípusokhoz való hozzáadásához egy PowerPoint-prezentációban az Aspose.Slides for .NET használatával.  

## Előfeltételek  

Mielőtt belevágnánk a megvalósításba, győződjön meg arról, hogy rendelkezik a következő beállításokkal:  

1.  Aspose.Slides for .NET: Töltse le és telepítse a könyvtárat a[letöltési oldal](https://releases.aspose.com/slides/net/).  
2. Fejlesztési környezet: Használjon olyan IDE-t, mint a Visual Studio a kódoláshoz.  
3. Alapvető C# ismeretek: Az oktatóanyag követéséhez a C# programozás ismerete szükséges.  

## Kötelező névterek importálása  

Kezdésként importálja az alapvető névtereket a projektbe:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 1. lépés: A prezentáció beállítása  

Először inicializáljon egy üres prezentációt. Ez a diagram tárolójaként fog szolgálni.  

```csharp
string dataDir = "Your/Documents/Directory";

// Győződjön meg arról, hogy a könyvtár létezik
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Hozzon létre egy új prezentációt
Presentation presentation = new Presentation();
```

## 2. lépés: Diagram hozzáadása a diához  

Most adjon hozzá egy diát, és vegyen fel egy fürtözött oszlopdiagramot az adatok megjelenítéséhez.  

```csharp
// Adjon hozzá egy üres diát
ISlide slide = presentation.Slides[0];

// Adjon hozzá egy fürtözött oszlopdiagramot
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## 3. lépés: A diagramadatok feltöltése  

Töltse fel a diagramot mintaadatokkal.  

```csharp
// Az alapértelmezett diagramadatok munkafüzet elérése
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Frissítse az alapértelmezett kategóriákat és sorozatértékeket
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## 4. lépés: Trendvonalak hozzáadása  

### Exponenciális trendvonal  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Lineáris trendvonal  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Logaritmikus trendvonal  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Mozgóátlag Trendvonal  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Polinom trendvonal  

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

## 5. lépés: A prezentáció mentése  

Végül mentse el a prezentációt a diagramhoz hozzáadott összes trendvonallal.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Következtetés  

Az Aspose.Slides for .NET használatával a trendvonalak hozzáadása a diagramokhoz egyszerű feladattá válik. Ez a funkció lehetővé teszi, hogy hatékonyan mutassa be az adattrendeket, és professzionális hatást adjon prezentációihoz. Kövesse a fenti lépéseket a különböző trendvonaltípusok beépítéséhez és az adatok megjelenítésének javításához.  

## GYIK  

### Testreszabhatom a trendvonalak megjelenését?  
 Igen, testreszabhatja a trendvonalak színét, vastagságát és stílusát a segítségével`Format.Line` ingatlan.  

### Van-e támogatás más diagramtípusokhoz?  
Igen, az Aspose.Slides for .NET különféle diagramtípusokat támogat, beleértve a sáv-, kör- és vonaldiagramokat.  

### Hogyan jeleníthetek meg egyenleteket és R-négyzet értékeket?  
 Engedélyezés`DisplayEquation` és`DisplayRSquaredValue` tulajdonságait egy trendvonalhoz, hogy megjelenítse ezeket az értékeket a diagramon.  

### Használhatom az Aspose.Slides for .NET-et más nyelvekkel?  
Igen, a könyvtár kompatibilis bármely .NET által támogatott nyelvvel, beleértve a VB.NET-et és az F#-ot is.  

### Hol találok további dokumentációt?  
 Látogassa meg a[Aspose.Slides a .NET dokumentációhoz](https://reference.aspose.com/slides/net/) további információkért.