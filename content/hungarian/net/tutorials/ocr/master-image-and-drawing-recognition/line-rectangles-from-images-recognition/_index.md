---
title: Vonaltéglalapok kinyerése a képfelismerésből
linktitle: Vonaltéglalapok kinyerése a képfelismerésből
second_title: Aspose.OCR .NET API
description: Ismerje meg, hogyan valósíthatja meg az optikai karakterfelismerést (OCR) .NET-alkalmazásaiban az Aspose.OCR használatával. Ez az átfogó útmutató végigvezeti a felismert vonalak téglalapjainak kinyerésének folyamatán.
type: docs
weight: 10
url: /hu/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Bevezetés

Üdvözöljük az Aspose.OCR for .NET világában, egy lenyűgöző eszköz, amely az optikai karakterfelismerést (OCR) integrálja .NET-alkalmazásaiba. Akár tapasztalt fejlesztő, akár kíváncsi újonc, ez az útmutató végigvezeti Önt azon lépéseken, amelyek segítségével a képek felismert szövegéből vonalakat ábrázoló téglalapokat kaphat.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következők vannak a helyükön:

- C# és .NET fejlesztési alapismeretek.
- Integrált fejlesztői környezet (IDE), például a Visual Studio.
-  Az Aspose.OCR for .NET könyvtár telepítve van. Letöltheti[itt](https://releases.aspose.com/ocr/net/).
- Egy mintakép, amely szöveget tartalmaz a felismeréshez.

## Kötelező névterek

A kezdéshez hozzá kell adnia a szükséges névtereket a projekthez. Illessze a következő sorokat a C# fájl tetejére:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Kövesse ezeket a lépéseket az OCR-kép vonalainak téglalapjainak lekéréséhez.

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Adja meg a könyvtárat, ahol a képfájl található:

```csharp
// Határozza meg a dokumentumkönyvtár elérési útját
string dataDir = "Your Document Directory";
```

 Mindenképpen cserélje ki`"Your Document Directory"` a tényleges úttal.

## 2. lépés: Inicializálja az Aspose.OCR-t

 Hozzon létre egy példányt a`AsposeOcr` osztály funkcióihoz való hozzáféréshez:

```csharp
// Inicializálja az Aspose.OCR API-t
AsposeOcr api = new AsposeOcr();
```

## 3. lépés: Adja meg a kép elérési útját

Határozza meg a feldolgozni kívánt képfájl teljes elérési útját:

```csharp
// Adja meg a kép teljes elérési útját
string fullPath = dataDir + "sample.png";
```

## 4. lépés: A kép felismerése és a vonalak téglalapjainak lekérése

 Most már használhatja a`GetRectangles` módszer felismert szövegsorok téglalapjainak kinyerésére:

```csharp
// Téglalapok lekérése a megadott kép vonalaihoz
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## 5. lépés: Írja ki az eredményeket

Végül nyomtassa ki az egyes észlelt vonaltéglalapok koordinátáit a konzolra:

```csharp
// Jelenítse meg az észlelt téglalapok koordinátáit
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Következtetés

Gratulálok! Sikeresen lekérte a téglalapokat egy OCR-kép vonalaihoz az Aspose.OCR for .NET használatával. Ez a technológia számos lehetőséget nyit meg a szövegek kinyerésére és feldolgozására az alkalmazásokban.

## GYIK

### Használhatom az Aspose.OCR-t .NET-hez bármilyen típusú képpel?

Igen, az Aspose.OCR különféle képformátumokat támogat, rugalmasságot biztosítva az OCR-alkalmazásokhoz.

### Mekkora az OCR felismerés pontossága?

Az Aspose.OCR fejlett algoritmusokat használ a szövegfelismerés nagy pontosságának eléréséhez, amely különféle forgatókönyvekhez alkalmas.

### Próbaverzió elérhető?

 Igen, felfedezheti az Aspose.OCR for .NET szolgáltatásait, ha letölti a[ingyenes próbaverzió](https://releases.aspose.com/).

### Hol találok részletes dokumentációt?

 Átfogó dokumentáció megtalálható[itt](https://reference.aspose.com/ocr/net/), amely részletes információkat és iránymutatásokat kínál.

### További segítségre van szüksége, vagy kérdései vannak?

 Csatlakozzon a vitához a[Aspose.OCR fórum](https://forum.aspose.com/c/ocr/16) közösségi támogatásért.