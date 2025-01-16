---
title: Chart Marker Options on Data Point az Aspose.Slides .NET-ben
linktitle: Chart Marker Options on Data Point az Aspose.Slides .NET-ben
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Ismerje meg, hogyan javíthatja PowerPoint diagramjait testreszabott jelölőbeállításokkal az Aspose.Slides for .NET segítségével. Ez a részletes útmutató az előfeltételeket, a diagramok létrehozását, az adatpontok formázását és egyebeket ismerteti.
type: docs
weight: 11
url: /hu/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Bevezetés

A vizuális segédeszközök beépítése az előadásokba elengedhetetlen a hatásos kommunikációhoz. Az Aspose.Slides for .NET robusztus eszközöket biztosít diagramok létrehozásához és testreszabásához, lehetővé téve a fejlesztők számára, hogy javítsák adatbemutatóikat. Az egyik kiemelkedő szolgáltatás a diagramjelölő opciók adatpontokon való használatának lehetősége, amely lehetővé teszi a professzionális megjelenésű diagramok pontos testreszabását. Ez a cikk végigvezeti Önt az ehhez szükséges lépéseken.

## Előfeltételek

A folytatás előtt győződjön meg a következőkről:

-  Aspose.Slides for .NET Telepítve: Töltse le innen[itt](https://releases.aspose.com/slides/net/).
- Alapbeállítás: Egy prezentációs fájl, például "Test.pptx", a munkakönyvtárban.
- Fejlesztési környezet: Visual Studio vagy azzal egyenértékű, .NET-hez konfigurálva.

## Kötelező névterek importálása

Adja hozzá a szükséges névtereket a projekthez a zökkenőmentes fejlesztés érdekében:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 1. lépés: Hozzon létre egy diagramot a prezentációjában

Kezdje azzal, hogy a prezentáció első diáján hozzon létre egy alapértelmezett diagramot:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Ez hozzáteszi a`LineWithMarkers` diagramot a diához adott méretekkel.

## 2. lépés: A Chart Data Worksheet Index lekérése

Az alapértelmezett diagramadat-munkalapindex elengedhetetlen a további testreszabáshoz:

```csharp
int defaultWorksheetIndex = 0;
```

## 3. lépés: Nyissa meg a diagramadatok munkafüzetet

A diagramadatok kezeléséhez kérje le a kapcsolódó munkafüzetet:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## 4. lépés: Diagramsorozat konfigurálása és adatpontok hozzáadása

Alapértelmezett sorozatok törlése és új adatpontok hozzáadása a sorozatokhoz:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Adjon hozzá adatpontokat a sorozathoz
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## 5. lépés: Alkalmazza a képkitöltéseket az adatpontjelzőkre

Az egyéni képek vizuálisan vonzóvá tehetik az adatjelölőket:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Állítson be egyéni képeket a jelölőkhöz
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## 6. lépés: A jelölő méretének testreszabása

Módosítsa a markerek méretét a láthatóság javítása érdekében:

```csharp
series.Marker.Size = 20;
```

## 7. lépés: Mentse el a frissített prezentációt

Mentse el a testreszabott prezentációt a kívánt helyre:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Következtetés

Az Aspose.Slides for .NET olyan eszközökkel látja el a fejlesztőket, amelyek segítségével professzionális diagramokat hozhatnak létre gazdag testreszabási lehetőségekkel. A diagramjelölők lehetőségeinek kihasználásával jelentősen javíthatja prezentációinak vizuális vonzerejét és tisztaságát. Ez a lépésenkénti útmutató biztosítja, hogy még az összetett testreszabások is egyszerűen végrehajthatók.

## GYIK

### Használhatok bármilyen képformátumot a marker testreszabásához?
Igen, az Aspose.Slides különféle képformátumokat támogat, beleértve a JPEG-et, PNG-t és BMP-t a markerek testreszabásához.

### Hogyan módosíthatom a diagram típusát a létrehozás után?
 A diagram típusának módosításához nyissa meg a`chart.Type` tulajdonságot, és rendeljen hozzá egy másikat`ChartType`.

### Az Aspose.Slides for .NET kompatibilis a régebbi PowerPoint-verziókkal?
Igen, támogatja a régebbi PowerPoint formátumokkal való visszamenőleges kompatibilitást, ami sokoldalúságot biztosít.

### Frissíthetem dinamikusan a diagram adatait?
 Teljesen. Használja a`IChartDataWorkbook` a diagramadatok programozott frissítéséhez.

### Hol találok további forrásokat?
 Fedezze fel a[Aspose.Slides dokumentáció](https://reference.aspose.com/slides/net/)vagy csatlakozzon a[közösségi fórumokon](https://forum.aspose.com/) támogatásért.