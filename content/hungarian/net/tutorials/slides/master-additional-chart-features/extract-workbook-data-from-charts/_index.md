---
title: Kivonja a munkafüzet adatait diagramokból az Aspose.Slides segítségével .NET-hez
linktitle: Kivonja a munkafüzet adatait diagramokból az Aspose.Slides segítségével .NET-hez
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Használja ki PowerPoint prezentációiban rejlő lehetőségeket, ha megtanulja, hogyan állíthatja helyre a munkafüzet adatait diagramokból az Aspose.Slides for .NET segítségével. Ez a lépésenkénti oktatóanyag végigvezeti a folyamaton, megkönnyítve a diagramadatok kinyerését és hatékony felhasználását.
type: docs
weight: 12
url: /hu/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## Bevezetés

PowerPoint prezentációkkal való munka kihívást jelenthet, különösen akkor, ha értékes adatokat nyer ki beágyazott diagramokból. Szerencsére az Aspose.Slides for .NET robusztus megoldást kínál, amely leegyszerűsíti ezt a folyamatot. Ebben az oktatóanyagban lépésről lépésre bemutatjuk, hogyan állíthat helyre munkafüzetet egy PowerPoint-prezentáción belüli diagramból.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjön meg arról, hogy készen áll a következőkre:

### Aspose.Slides .NET-hez

A fejlesztői környezetében telepíteni kell az Aspose.Slides for .NET programot. Ha még nem tette meg, letöltheti a weboldalról:

[Az Aspose.Slides letöltése .NET-hez](https://releases.aspose.com/slides/net/)

### PowerPoint bemutató

Tartsa kéznél a PowerPoint prezentációs fájlt, különösen azt, amely egy diagramot tartalmaz a visszaállítani kívánt kapcsolódó adatokkal.

## 1. lépés: Importálja a szükséges névtereket

Az Aspose.Slides hatékony használatához először importálnia kell a szükséges névtereket:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 2. lépés: Határozza meg a dokumentumkönyvtárat

Adja meg a könyvtárat, ahol a prezentációs fájl található:

```csharp
string dataDir = "Your Document Directory"; // Szükség szerint állítsa be ezt az utat
```

## 3. lépés: Töltse be a prezentációt

PowerPoint bemutatót betöltheti, miközben engedélyezi a munkafüzet helyreállítását a diagram gyorsítótárából. Íme, hogyan kell csinálni:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // A diagramadatok elérése és kezelése
    // A kódod ide kerül
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Ebben a lépésben a`LoadOptions` Az objektum lehetővé teszi a munkafüzet helyreállításának engedélyezését a`RecoverWorkbookFromChartCache` ingatlan.

## 4. lépés: Töltse le a diagramot, és nyissa meg a munkafüzetet

Itt az ideje, hogy beleássunk a diagramba, és lekérjük a kapcsolódó adatokat:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Szükség szerint állítsa be az indexet
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Mostantól igényei szerint dolgozhat a munkafüzet adataival
```

Az első dia első alakjának elérésével (amely várhatóan diagram lesz), megkapja a diagramadatok munkafüzetét, és szükség szerint módosíthatja vagy kivonhatja az adatokat.

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan lehet hatékonyan helyreállítani egy munkafüzetet egy PowerPoint-prezentáció diagramjából az Aspose.Slides for .NET segítségével. Az alábbi lépések követésével könnyedén kinyerheti és felhasználhatja a diagramadatokat elemzési igényeinek kielégítésére.

## GYIK

### Mi az Aspose.Slides for .NET?

Az Aspose.Slides for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Microsoft PowerPoint prezentációk programozott létrehozását, kezelését és konvertálását.

### Kipróbálhatom az Aspose.Slides for .NET programot vásárlás előtt?

 Igen! Az Aspose az Aspose.Slides ingyenes próbaverzióját kínálja .NET-hez. Vásárlás előtt felmérheti a képességeit.[Töltse le az ingyenes próbaverziót itt](https://releases.aspose.com/).

### Hol találom az Aspose.Slides for .NET dokumentációját?

 Hozzáférhet az Aspose.Slides for .NET átfogó dokumentációjához[itt](https://reference.aspose.com/slides/net/), amely példákat és API hivatkozásokat tartalmaz.

### Hogyan vásárolhatok licencet az Aspose.Slides for .NET számára?

 Licenc vásárlásához látogasson el az Aspose webhelyére, és használja a következő hivatkozást:[Vásároljon Aspose.Slides-t .NET-hez](https://purchase.aspose.com/buy).