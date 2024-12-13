---
title: A tömörítési szint beállítása a munkafüzetben
linktitle: A tömörítési szint beállítása a munkafüzetben
second_title: Aspose.Cells .NET Excel Processing API
description: Fedezze fel, hogyan kezelhet hatékonyan nagy Excel-fájlokat a tömörítési szintek beállításával az Aspose.Cells for .NET segítségével. Ez a részletes útmutató a könyvtárak beállításától a tömörítési idő méréséig mindent lefed, segít optimalizálni a fájlméretet és javítani a teljesítményt.
type: docs
weight: 14
url: /hu/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Bevezetés

nagyméretű Excel-fájlok kezelése kihívást jelenthet, különösen a tárolás és az átvitel hatékonyságát illetően. Szerencsére a fájltömörítés jelentősen csökkentheti ezen fájlok méretét, így könnyebben kezelhetőek. Ha az Aspose.Cells for .NET-et használja, könnyen beállíthatja a munkafüzetek tömörítési szintjét. Ez az útmutató lépésről lépésre végigvezeti a folyamaton, világos magyarázatot adva a kód minden egyes részéhez.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

1. Alapvető C# ismerete: A C# programozás ismerete segít jobban megérteni a kódrészleteket.
2.  Aspose.Cells Library: Töltse le és telepítse az Aspose.Cells könyvtárat innen[itt](https://releases.aspose.com/cells/net/).
3. Visual Studio: A kód futtatásához olyan fejlesztői környezetre van szükség, mint a Visual Studio.
4. .NET-keretrendszer: Győződjön meg arról, hogy projektje a .NET-keretrendszer kompatibilis verziójával van beállítva.

## A szükséges csomagok importálása

kezdéshez importálnia kell a szükséges csomagokat a C# projektbe. Adja hozzá a következő sorokat a kódfájl tetejéhez:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Ezek a csomagok nélkülözhetetlenek az Aspose.Cells könyvtárat használó Excel-fájlok kezeléséhez. A`Aspose.Cells` névtér tartalmazza az Excel fájlok kezeléséhez szükséges összes osztályt, míg`Aspose.Cells.Xlsb` lehetőséget biztosít a fájlok XLSB formátumban történő mentésére.

## 1. lépés: Forrás- és kimeneti könyvtárak meghatározása

Először állítsa be azokat a könyvtárakat, ahol a forrásfájlok találhatók, és ahová menteni szeretné a kimeneti fájlokat:

```csharp
// Forrás- és kimeneti könyvtárak meghatározása
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Mindenképpen cserélje ki`"Your Document Directory\\"` a könyvtárak tényleges elérési útjaival. Ez biztosítja, hogy a program megtalálja azokat a fájlokat, amelyekkel dolgoznia kell.

## 2. lépés: Töltse be a munkafüzetet

Ezután töltse be a tömöríteni kívánt munkafüzetet:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Itt létrehozunk egy új példányt a`Workbook` osztályt, és töltsön be egy meglévő Excel fájlt. Győződjön meg arról, hogy a fájlnév megegyezik a forráskönyvtárban lévővel.

## 3. lépés: Állítsa be a mentési beállításokat

Most konfigurálja a munkafüzet mentési beállításait:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 A`XlsbSaveOptions`osztály lehetővé teszi különböző beállítások megadását a munkafüzet XLSB formátumban történő mentésekor, beleértve a tömörítési szinteket is.

## 4. lépés: Mérje meg az 1. szint tömörítési idejét

Kezdje az első tömörítési szinttel, és mérje meg a munkafüzet mentéséhez szükséges időt:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Ez a kódrészlet 1. szintre állítja a tömörítési típust, elmenti a munkafüzetet, és méri az eltelt időt.

## 5. lépés: Mérje meg a 6. szint tömörítési idejét

Ezután tesztelje a teljesítményt 6-os szintű tömörítéssel:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Ez a lépés hasonló az előzőhöz, de magasabb tömörítési szinttel.

## 6. lépés: Mérje meg a 9. szint tömörítési idejét

Végül értékelje a teljesítményt a legmagasabb tömörítési szint mellett:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Ez a lépés a tömörítési szintet 9-es szintre állítja, ahol valószínűleg a fájlméret legjelentősebb csökkenése tapasztalható, bár a feldolgozás tovább tarthat.

## 7. lépés: Végső kimenet

Az összes tömörítési szint teljesítése után adjon ki egy üzenetet, amely jelzi, hogy a folyamat sikeresen befejeződött:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Ez az egyszerű sor megerősíti, hogy a program problémamentesen futott.

## Következtetés

A munkafüzetek tömörítési szintjének beállítása az Aspose.Cells for .NET használatával egyszerű folyamat, amely jelentős javulást eredményezhet a fájlméretben és a teljesítményben. Az ebben az útmutatóban ismertetett lépések követésével hatékonyan valósíthatja meg a tömörítést az alkalmazásaiban, javítva ezzel az Excel fájlkezelési képességeit.

## GYIK

### Mi az Aspose.Cells?  
Az Aspose.Cells egy hatékony .NET-könyvtár, amely lehetővé teszi a fejlesztők számára Excel-fájlok létrehozását, kezelését és konvertálását Microsoft Excel nélkül.

### Hogyan telepíthetem az Aspose.Cells-t?  
 Az Aspose.Cells letölthető és telepíthető a[Aspose honlapja](https://releases.aspose.com/cells/net/).

### Milyen tömörítési szintek állnak rendelkezésre?  
Az Aspose.Cells több tömörítési szintet támogat, az 1. szinttől (legalacsonyabb tömörítés) a 9. szintig (legmagasabb tömörítés).

### Ingyenesen tesztelhetem az Aspose.Cells-t?  
 Igen! Az Aspose.Cells ingyenes próbaverzióját kaphatja meg[itt](https://releases.aspose.com/).

### Hol találok támogatást az Aspose.Cells számára?  
 Kérdéseivel vagy támogatásával keresse fel az Aspose támogatási fórumát[itt](https://forum.aspose.com/c/cells/9).