---
title: Kitöltött téglalap létrehozása
linktitle: Kitöltött téglalap létrehozása
second_title: Aspose.PDF for .NET API Reference
description: Fedezze fel a PDF-manipuláció erejét az Aspose.PDF for .NET segítségével ebben a lépésenkénti oktatóanyagban. Ismerje meg, hogyan hozhat létre programozottan tetszetős PDF-dokumentumokat kitöltött téglalapok rajzolásával.
type: docs
weight: 50
url: /hu/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Bevezetés

Szeretett volna már vizuálisan lenyűgöző PDF-eket készíteni programozottan? Ha igen, akkor jó helyen jársz! Ebben az oktatóanyagban megvizsgáljuk az Aspose.PDF for .NET-et, egy hatékony könyvtárat, amely leegyszerűsíti a PDF-dokumentumok kezelését. Ma egy kitöltött téglalap létrehozására fogunk összpontosítani egy PDF-fájlban. Akár tapasztalt fejlesztő, akár csak most kezdő, ez az útmutató barátságos és vonzó módon végigvezeti Önt minden lépésen. Szóval, fogd meg a kódoló kalapot, és kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy rendelkezik a következőkkel:

1. Visual Studio: Telepítse a Visual Studio-t a gépére, mivel kiváló IDE a .NET fejlesztéshez.
2. Aspose.PDF for .NET: Töltse le és telepítse az Aspose.PDF könyvtárat innen[itt](https://releases.aspose.com/pdf/net/).
3. Alapvető C# ismerete: A C# programozás ismerete segít jobban megérteni a kódrészleteket.

## 1. lépés: Hozzon létre egy új projektet

1. Nyissa meg a Visual Studio-t, és hozzon létre egy új konzolalkalmazás-projektet.
2. Nevezze el megfelelően a projektjét.

## 2. lépés: Adja hozzá az Aspose.PDF hivatkozást

1. Kattintson a jobb gombbal a projektre a Solution Explorerben.
2. Válassza a NuGet-csomagok kezelése lehetőséget.
3. Keresse meg az Aspose.PDF fájlt, és telepítse a legújabb verziót.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Most, hogy mindent beállítottunk, merüljünk el a kódban!

## 3. lépés: Állítsa be a dokumentumkönyvtárat

Adja meg a PDF mentési útvonalat:

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal a gépén, ahová menteni szeretné a PDF-fájlt.

## 4. lépés: Hozzon létre egy dokumentumpéldányt

Új PDF dokumentum inicializálása:

```csharp
//Dokumentumpéldány létrehozása
Document doc = new Document();
```

## 5. lépés: Adjon hozzá egy oldalt a dokumentumhoz

Minden PDF-nek legalább egy oldalra van szüksége. Adjunk hozzá egyet:

```csharp
// Oldal hozzáadása a PDF-fájl oldalgyűjteményéhez
Page page = doc.Pages.Add();
```

## 6. lépés: Hozzon létre egy grafikonpéldányt

 A`Graph` példány vászonként működik alakzatok rajzolásához:

```csharp
// Graph példány létrehozása
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## 7. lépés: Adja hozzá a grafikont az oldalhoz

Csatolja a grafikont az oldalhoz:

```csharp
// Grafikon objektum hozzáadása az oldalpéldány bekezdésgyűjteményéhez
page.Paragraphs.Add(graph);
```

## 8. lépés: Hozzon létre egy téglalappéldányt

Határozza meg a téglalap helyzetét és méretét:

```csharp
// Téglalap példány létrehozása
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## 9. lépés: Adja meg a kitöltés színét

Válasszon színt a téglalaphoz. Ebben a példában a pirosat használjuk:

```csharp
// Adja meg a Graph objektum kitöltési színét
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## 10. lépés: Adja hozzá a téglalapot a diagramhoz

Adja hozzá a téglalapot a grafikonhoz:

```csharp
// Téglalap objektum hozzáadása a Graph objektum alakzatgyűjteményéhez
graph.Shapes.Add(rect);
```

## 11. lépés: Mentse el a PDF-dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// PDF fájl mentése
doc.Save(dataDir);
```

## 12. lépés: Megerősítő üzenet

Nyomtasson egy megerősítő üzenetet a siker jelzésére:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Következtetés

Gratulálok! Sikeresen létrehozott egy kitöltött téglalapot egy PDF-dokumentumban az Aspose.PDF for .NET használatával. Ez a nagy teljesítményű könyvtár a lehetőségek világát nyitja meg a PDF-kezelés számára, lehetővé téve, hogy lenyűgöző dokumentumokat készítsen programozottan. Függetlenül attól, hogy jelentéseket, számlákat vagy bármilyen más típusú PDF-et készít, az Aspose.PDF mindenre kiterjed.

## GYIK

### Mi az Aspose.PDF for .NET?
Az Aspose.PDF for .NET egy olyan könyvtár, amely lehetővé teszi a fejlesztők számára PDF-dokumentumok programozott létrehozását, kezelését és konvertálását.

### Használhatom ingyenesen az Aspose.PDF-et?
 Igen, az Aspose ingyenes próbaverziót kínál, amellyel felfedezheti a könyvtár funkcióit. Letöltheti[itt](https://releases.aspose.com/).

### Van mód az Aspose.PDF támogatására?
 Teljesen! Az Aspose fórumon keresztül kaphat támogatást[itt](https://forum.aspose.com/c/pdf/10).

### Hogyan vásárolhatom meg az Aspose.PDF-et?
 Az Aspose.PDF-et a vásárlási oldalon vásárolhatja meg[itt](https://purchase.aspose.com/buy).

### Milyen típusú alakzatokat hozhatok létre az Aspose.PDF segítségével?
Az Aspose.PDF könyvtár használatával különféle alakzatokat hozhat létre, például téglalapokat, köröket, vonalakat és egyebeket.