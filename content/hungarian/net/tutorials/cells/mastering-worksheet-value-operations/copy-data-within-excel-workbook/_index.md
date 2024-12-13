---
title: Adatok másolása az Excel-munkafüzetben az Aspose.Cells for .NET használatával
linktitle: Adatok másolása az Excel-munkafüzetben az Aspose.Cells for .NET használatával
second_title: Aspose.Cells .NET Excel Processing API
description: Ismerje meg, hogyan másolhat hatékonyan adatokat egy Excel-munkafüzetben az Aspose.Cells for .NET segítségével. Kövesse ezt a lépésenkénti útmutatót a munkalapok egyszerű sokszorosításához, az adatok átviteléhez és az Excel-fájlok egyszerű kezeléséhez.
type: docs
weight: 12
url: /hu/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Bevezetés

Ebben a részletes útmutatóban bemutatjuk, hogyan lehet adatokat másolni ugyanabban a munkafüzetben az Aspose.Cells for .NET használatával. Az alábbiakban ismertetett lépésenkénti utasítások követésével megtanulhatja, hogyan lehet programozottan sokszorosítani a lapokat, megőrizni a tartalmukat és a formázásukat.

## Az adatok Excelben történő másolásának előfeltételei az Aspose.Cells segítségével

Mielőtt belemerülnénk a kódolási folyamatba, győződjünk meg arról, hogy minden a helyén van:

1. Aspose.Cells for .NET Library: telepítenie kell az Aspose.Cells for .NET könyvtárat. A legújabb verziót letöltheti a[Aspose.Cells for .NET letöltési oldal](https://releases.aspose.com/cells/net/).
2. Fejlesztői környezet: Egy .NET-kompatibilis IDE, például a Visual Studio szükséges a kód írásához és futtatásához.
3.  Aspose licenc: Használhat ingyenes próbaverziót vagy megvásárolt licencet. További információért látogasson el[itt](https://purchase.aspose.com/temporary-license/).

Az előfeltételek beállítása után készen áll a könyvtárral való munka megkezdésére.

## A szükséges csomagok importálása

A kezdéshez importálnia kell a megfelelő névtereket az Aspose.Cells fájlból. Ez lehetővé teszi, hogy az Aspose.Cells által biztosított osztályok és módszerek használatával Excel-fájlokkal dolgozzon.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Ezek a névterek hozzáférést biztosítanak a`Workbook` osztály (Excel fájlokkal való munkavégzéshez) és`WorksheetCollection` (több lap eléréséhez egy munkafüzeten belül).

## 1. lépés: Inicializálja a munkafüzet fájlútvonalait

kód rendszerezettségének megőrzéséhez elengedhetetlen a fájl elérési útjainak meghatározása, ahol a munkafüzet található, és hová kívánja menteni a módosított fájlt. A következőképpen adhatja meg az útvonalakat:

```csharp
// Határozza meg az Excel fájl elérési útját.
string dataDir = "Your Directory Path";

// Határozza meg a beviteli munkafüzet teljes elérési útját.
string inputPath = dataDir + "book1.xls";
```

 Cserélje ki`"Your Directory Path"` a munkafüzetet tartalmazó könyvtár tényleges elérési útjával. Ez segít abban, hogy a kód rugalmas legyen, és hatékonyan tudja kezelni az útvonalakat.

## 2. lépés: Nyissa meg a munkafüzetet az adatok eléréséhez

 Most, hogy a fájl elérési útja be van állítva, a következő lépés az Excel munkafüzet betöltése a`Workbook` objektum. Ez lehetővé teszi, hogy hozzáférjen a tartalmához manipuláció céljából.

```csharp
// Töltse be az Excel fájlt a munkafüzet objektumba.
Workbook wb = new Workbook(inputPath);
```

 Ezzel a sorral sikeresen betöltődött`book1.xls` a`wb` objektumot, hozzáférhetővé téve adatait.

## 3. lépés: Nyissa meg a Munkalapgyűjteményt

 A munkafüzet betöltése után hozzáférhet a benne található lapokhoz. Az Aspose.Cells biztosítja a`Worksheets`gyűjtemény, amely lehetővé teszi a munkafüzet egyes munkalapjaival való interakciót.

```csharp
// A munkalapgyűjtemény lekérése a munkafüzetből.
WorksheetCollection sheets = wb.Worksheets;
```

 A`sheets` objektum hozzáférést biztosít az összes munkalaphoz`book1.xls`, és különféle műveleteket hajthat végre rajtuk, például adatokat másolhat egyik lapról a másikra.

## 4. lépés: Másolja át az adatokat egyik lapról a másikra

 Az Aspose.Cells egy könnyen használható módszert kínál az egyik munkalapról a másikra ugyanazon a munkafüzeten belüli másolásához.`AddCopy`. Ez a módszer létrehozza a megadott munkalap másolatát, és hozzáfűzi a munkafüzethez.

```csharp
// Másolja az adatokat az „1. lapról” egy új munkalapra a munkafüzetben.
sheets.AddCopy("Sheet1");
```

 Ebben a példában adatokat másolunk az „1. lapról” egy új munkalapra. A`AddCopy` metódus megkettőzi a teljes lapot, megőrzi annak teljes tartalmát, beleértve a képleteket, formázást és értékeket.

## 5. lépés: Mentse el a módosított munkafüzetet

 Az adatok másolása után a módosított munkafüzetet új néven vagy helyre mentheti. Ez úgy történik, hogy felhívja a`Save`módszer a`Workbook` objektum.

```csharp
//Mentse el a módosított munkafüzetet új néven.
wb.Save(dataDir + "book1_copy.xls");
```

 Ezzel elmenti a munkafüzetet a másolt lappal mint`book1_copy.xls` a megadott könyvtárban. Igényei szerint módosíthatja a fájl nevét és elérési útját.

## Következtetés

Az adatok másolása Excel-munkafüzetben az Aspose.Cells for .NET használatával egyszerű feladat, és ez az útmutató a hatékony végrehajtáshoz szükséges lépéseket tartalmazza. Akár egész lapokat, akár meghatározott adattartományokat másol, az Aspose.Cells robusztus és rugalmas API-t kínál, amely egyszerűvé és hatékonysá teszi az Excel automatizálását.

## GYIK

### Másolhatok több lapot egyszerre?

Az Aspose.Cells nem támogatja több lap másolását egyetlen hívásban. A másolni kívánt lapokat azonban egyenként is átmásolhatja.

### Hogyan nevezhetem át a másolt lapot?

A lap másolása után a következőképpen nevezheti át:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Az Aspose.Cells kompatibilis a .NET Core-al?

Igen, az Aspose.Cells teljes mértékben kompatibilis mind a .NET Framework, mind a .NET Core környezetekkel.

### Hogyan kezeli az Aspose.Cells a formázást másolás közben?

 A`AddCopy`módszer megőrzi az összes tartalmat és formázást a lapok másolásakor, biztosítva, hogy a másolt adatok megegyezzenek az eredetivel.

### Másolhatok egy lapot egy másik munkafüzetbe?

 Igen, átmásolhat egy lapot egy másik munkafüzetbe a segítségével`Copy` módszer a célmunkafüzetre való hivatkozással.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```