---
title: Keresse meg a maximális sorokat és oszlopokat XLS és XLSX formátumban
linktitle: Keresse meg a maximális sorokat és oszlopokat XLS és XLSX formátumban
second_title: Aspose.Cells .NET Excel Processing API
description: Fedezze fel, hogyan kezelhet hatékonyan nagy adatkészleteket az Excelben az Aspose.Cells for .NET könyvtár használatával. Ez az útmutató lépésről lépésre bemutatja az XLS és XLSX fájlformátumok által támogatott sorok és oszlopok maximális számát.
type: docs
weight: 11
url: /hu/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Bevezetés

A nagy adatkészletek Excelben való kezelése kihívást jelenthet, különösen a különféle fájlformátumok korlátai miatt. Ez az oktatóanyag végigvezeti Önt az Aspose.Cells for .NET könyvtár használatával, amellyel meghatározhatja az XLS (Excel 97-2003) és az XLSX (Excel 2007 és újabb) formátumok által támogatott sorok és oszlopok maximális számát. A végére fel lesz készülve az Excelhez kapcsolódó feladatok hatékony kezelésére.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1. [.NET-keretrendszer](https://dotnet.microsoft.com/en-us/download) vagy[.NET Core](https://dotnet.microsoft.com/en-us/download) telepítve van a rendszerére.
2. [Aspose.Cells for .NET](https://releases.aspose.com/cells/net/) letöltött és a projektben hivatkozott könyvtár (telepítheti a következőn keresztül is).[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## A szükséges csomagok importálása

szükséges csomagok Aspose.Cells könyvtárból való importálásához adja hozzá a következőket a C# fájl tetején található utasításokkal:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 1. lépés: Sorok és oszlopok maximális száma XLS formátumhoz

Kezdjük azzal, hogy megkeressük az XLS formátum által támogatott maximális sorokat és oszlopokat.

```csharp
// Nyomtasson üzenetet az XLS formátumról.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Hozzon létre egy munkafüzetet XLS formátumban.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Maximum sorok és oszlopok lekérése.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Jelenítse meg az eredményeket.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Nyomtasson ki egy üzenetet, jelezve, hogy az XLS formátummal dolgozunk.
2.  Hozzon létre a`Workbook` példa az XLS formátumhoz`FileFormatType.Excel97To2003`.
3.  Szerezze meg a maximális sorokat és oszlopokat ezzel`wb.Settings.MaxRow` és`wb.Settings.MaxColumn`, 1 hozzáadásával, mivel ezek nulla alapúak.
4. Írja ki a maximális sorokat és oszlopokat a konzolra.

## 2. lépés: Sorok és oszlopok maximális száma XLSX formátumhoz

Ezután megvizsgáljuk az XLSX formátum által támogatott maximális sorokat és oszlopokat.

```csharp
// Nyomtasson üzenetet az XLSX formátumról.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Hozzon létre egy munkafüzetet XLSX formátumban.
wb = new Workbook(FileFormatType.Xlsx);

// Maximum sorok és oszlopok lekérése.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Jelenítse meg az eredményeket.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Nyomtasson ki egy üzenetet, amely jelzi, hogy az XLSX formátummal dolgozunk.
2.  Hozzon létre a`Workbook` példa az XLSX formátumhoz`FileFormatType.Xlsx`.
3. Töltse le és adja ki a maximális sorokat és oszlopokat, mint korábban.

## 3. lépés: Sikerüzenet megjelenítése

A lépések végrehajtása után jelezzük a sikert.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Következtetés

Ebben az oktatóanyagban megtanulta, hogyan használhatja az Aspose.Cells for .NET könyvtárat az XLS és XLSX fájlformátumok által támogatott maximális sorok és oszlopok megkeresésére. E korlátok megértése elengedhetetlen a hatékony Excel adatkezeléshez, amely biztosítja, hogy az adatkészletek igazodjanak a formátumképességekhez.

## GYIK

### Mekkora az XLS formátum által támogatott sorok maximális száma?
Az XLS formátum által támogatott sorok maximális száma 65 536.

### Mennyi az XLS formátum által támogatott oszlopok maximális száma?
Az XLS formátum által támogatott oszlopok maximális száma 256.

### Mekkora az XLSX formátum által támogatott sorok maximális száma?
Az XLSX formátum által támogatott sorok maximális száma 1 048 576.

### Mennyi az XLSX formátum által támogatott oszlopok maximális száma?
Az XLSX formátum által támogatott oszlopok maximális száma 16 384.

### Használhatom az Aspose.Cells for .NET könyvtárat más Excel fájlformátumokkal?
 Igen, az Aspose.Cells for .NET különféle fájlformátumokat támogat, beleértve az XLS-t, az XLSX-et, az ODS-t és egyebeket. Ellenőrizze a[dokumentáció](https://reference.aspose.com/cells/net/) a támogatott szolgáltatásokkal és funkciókkal kapcsolatos részletekért.