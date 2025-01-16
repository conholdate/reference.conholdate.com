---
title: Speciális diagram testreszabás az Aspose.Slides segítségével .NET-hez
linktitle: Speciális diagram testreszabás az Aspose.Slides segítségével .NET-hez
second_title: Aspose.Slides .NET PowerPoint Processing API
description: A .NET-hez készült Aspose.Slides-ben rejlő teljes potenciál kiaknázása fejlett diagram-testreszabási technikák elsajátításával. Ez a lépésenkénti útmutató mindent lefed az alapvető diagramkészítéstől a bonyolult részletekig, mint például a rácsvonalak, a tengelyek címei és az egyéni színek.
type: docs
weight: 10
url: /hu/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Bevezetés

A vizuálisan tetszetős és informatív diagramok készítése elengedhetetlen a hatékony adatmegjelenítéshez. Az Aspose.Slides for .NET hatékony eszközöket kínál a diagramok testreszabásához, lehetővé téve a diagramok minden aspektusának testreszabását. Ebben az oktatóanyagban az Aspose.Slides for .NET használatával végzett diagramok testreszabásának fejlett technikáit vizsgáljuk meg.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

1.  Aspose.Slides for .NET Library: Töltse le és telepítse az Aspose.Slides könyvtárat innen:[itt](https://releases.aspose.com/slides/net/).
2. .NET fejlesztői környezet: .NET fejlesztői környezet beállítása, például a Visual Studio.
3. C# alapismeretek: A C# programozás ismerete előnyt jelent, hiszen C# kódot fogunk írni.

Most bontsuk le a speciális diagram testreszabási folyamatot egyértelmű lépésekre.

## 1. lépés: Hozzon létre egy új prezentációt

Kezdje új prezentáció létrehozásával a diagram megtartásához.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "Your Document Directory";

// Ha nem létezik, hozzon létre könyvtárat.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Példányosítsa a bemutatót
Presentation pres = new Presentation();
```

## 2. lépés: Nyissa meg az első diát

Ezután nyissa meg az első diát, amelyhez hozzá szeretné adni a diagramot.

```csharp
// Nyissa meg az első diát
ISlide slide = pres.Slides[0];
```

## 3. lépés: Adjon hozzá egy mintadiagramot

Most adjunk hozzá egy vonaldiagramot jelölőkkel a diához.

```csharp
// Adjon hozzá egy minta diagramot
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## 4. lépés: Állítsa be a diagram címét

A diagram címének megadása alapvető kontextust biztosít.

```csharp
// Állítsa be a diagram címét
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 5. lépés: A főbb rácsvonalak testreszabása

A jobb olvashatóság érdekében javíthatja az értéktengely rácsvonalait.

```csharp
// Testreszabhatja az értéktengely főbb rácsvonalait
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## 6. lépés: A kisebb rácsvonalak testreszabása

Hasonlóképpen testreszabhatja az értéktengely kisebb rácsvonalait.

```csharp
// Kisebb rácsvonalak testreszabása az értéktengelyhez
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 7. lépés: Határozza meg az értéktengely számformátumát

Az értéktengelyen megjelenő számokat formázhatja.

```csharp
// Állítsa be az érték tengelyszámának formátumát
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## 8. lépés: Állítsa be a maximális és minimális értékeket

Határozza meg a diagram maximális és minimális értékét.

```csharp
// Állítsa be a diagram maximális és minimális értékeit
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## 9. lépés: Az értéktengely szövegtulajdonságainak testreszabása

Az értéktengely szövegtulajdonságainak javítása javítja az olvashatóságot.

```csharp
// Testreszabhatja az Értéktengely szövegtulajdonságait
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## 10. lépés: Adja hozzá az értéktengely címét

Cím hozzáadása az értéktengelyhez tisztázhatja, hogy mit jelentenek az adatok.

```csharp
// Állítsa be az értéktengely címét
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 11. lépés: A főbb rácsvonalak testreszabása a kategóriatengelyhez

Most javítsuk ki a kategóriatengely főbb rácsvonalait.

```csharp
// A főbb rácsvonalak testreszabása a kategória tengelyhez
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## 12. lépés: A kisebb rácsvonalak testreszabása a kategóriatengelyhez

Hasonlóképpen testreszabhatja a kisebb rácsvonalakat a kategóriatengelyhez.

```csharp
// Kisebb rácsvonalak testreszabása a kategória tengelyhez
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 13. lépés: A kategóriatengely szövegtulajdonságainak testreszabása

kategóriatengely-címkék betűstílusának és megjelenésének javítása.

```csharp
// A kategóriatengely szövegtulajdonságainak testreszabása
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## 14. lépés: Adja hozzá a kategória tengely címét

Ha szükséges, a kategóriatengelyhez címet is adhat.

```csharp
// Állítsa be a kategória tengely címét
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 15. lépés: További testreszabások

Fejlessze tovább diagramját további testreszabásokkal, például jelmagyarázatokkal, falszínekkel és telekterület-beállításokkal.

```csharp
// További testreszabások (opcionális)

// A Legends szövegtulajdonságainak testreszabása
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// A diagram jelmagyarázatainak megjelenítése átfedő diagram nélkül
chart.Legend.Overlay = true;

// Beállítási táblázat hátsó fal színe
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Állítsa be a diagram padlószínét
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Állítsa be a Terület színét
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Mentse el a bemutatót
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Következtetés

Ebben az átfogó útmutatóban az Aspose.Slides for .NET használatával fejlett diagram-testreszabási technikákat ismertettünk. Megtanulta, hogyan hozhat létre prezentációt, hogyan adhat hozzá diagramot, finomítja a megjelenését, és hogyan szabhat testre különféle diagramelemeket, például rácsvonalakat, tengelycímkéket és jelmagyarázatokat. 

## GYIK

### A .NET mely verzióit támogatja az Aspose.Slides for .NET?
Az Aspose.Slides for .NET különféle .NET-verziókat támogat, beleértve a .NET-keretrendszert és a .NET Core-t. A támogatott verziók teljes listáját a dokumentációban találja.

### Létrehozhatok diagramokat adatforrásokból, például Excel-fájlokból?
Igen, az Aspose.Slides lehetővé teszi diagramok létrehozását külső adatforrásokból, például Excel-táblázatokból. A részletes példákat a dokumentációban találja.

### Hogyan adhatok egyéni adatcímkéket diagramsorozatomhoz?
 Egyéni adatcímkék hozzáadásához nyissa meg a`DataLabels` a sorozat tulajdonságait, és szükség szerint testreszabhatja a címkéket. Kódmintákat találhat a dokumentációban.

### Exportálható a diagram különböző formátumokba, például PDF-be vagy képekbe?
Teljesen! Az Aspose.Slides lehetővé teszi a diagramokkal ellátott prezentációk exportálását különféle formátumokba, beleértve a PDF- és képformátumokat.

### Hol találok további oktatóanyagokat és példákat az Aspose.Slides for .NET-hez?
 Látogassa meg az Aspose.Slides-t[weboldal](https://reference.aspose.com/slides/net/) kiterjedt oktatóanyagokért, kódpéldákért és dokumentációért.