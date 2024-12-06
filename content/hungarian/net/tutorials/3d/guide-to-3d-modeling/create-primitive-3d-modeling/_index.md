---
title: Primitív 3D modellezés létrehozása
linktitle: Primitív 3D modellezés létrehozása
second_title: Aspose.3D .NET API
description: Tanulja meg, hogyan hozhat létre és szabhat testre primitív 3D-s modelleket, beleértve a dobozokat és hengereket, és könnyedén mentheti FBX formátumba.
type: docs
weight: 10
url: /hu/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Bevezetés

Üdvözöljük a 3D modellezés magával ragadó világában az Aspose.3D for .NET használatával! Ebben az átfogó oktatóanyagban lépésről lépésre végigvezetjük a primitív 3D modellek létrehozásának folyamatán. Legyen szó tapasztalt fejlesztőről vagy kezdő, tanulni vágyó, ez az útmutató lehetővé teszi, hogy vizuálisan lenyűgöző 3D-s elemeket készítsen projektjeihez.

## Előfeltételek

Mielőtt belemerülne a 3D modellezésbe, győződjön meg arról, hogy a következő előfeltételekkel rendelkezik:

-  Aspose.3D for .NET: Töltse le és telepítse az Aspose.3D for .NET könyvtárat a[letöltési oldal](https://releases.aspose.com/3d/net/).
  
- .NET fejlesztői környezet: Az Aspose.3D-vel kompatibilis környezet beállítása, például a Visual Studio.

Mindennel felkészülve induljunk 3D-s modellezési kalandunknak!

## Kötelező névterek importálása

Kezdje a szükséges névterek importálásával az Aspose.3D funkciók eléréséhez:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Ezek a névterek biztosítják a 3D-s modellek kezeléséhez és az alkotások mentéséhez szükséges eszközöket.

## 1. lépés: Inicializáljon egy jelenetobjektumot

Hozzon létre egy új jelenetobjektumot, amely vászonként működik 3D modelljeihez:

```csharp
// Inicializáljon egy jelenet objektumot
Scene scene = new Scene();
```

Ez a jelenet tartalmazza azokat a primitív alakzatokat, amelyeket éppen létrehozni készül.

## 2. lépés: Hozzon létre egy doboz modellt

Ezután adjunk hozzá egy dobozmodellt a jelenethez:

```csharp
// Hozzon létre egy Box modellt
scene.RootNode.CreateChildNode("box", new Box());
```

Testreszabhatja a doboz méreteit és tulajdonságait kreatív elképzeléseinek megfelelően.

## 3. lépés: Hozzon létre egy hengermodellt

Most fokozza a jelenetet egy henger hozzáadásával:

```csharp
// Hozzon létre egy hengermodellt
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Csakúgy, mint a doboznál, nyugodtan állítsa be a henger paramétereit, hogy elérje a kívánt megjelenést.

## 4. lépés: Mentse el a jelenetet FBX formátumban

3D modell megőrzéséhez mentse el FBX formátumban:

```csharp
// Mentse el a rajzot FBX formátumban
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Ügyeljen arra, hogy a modellnek megfelelő kimeneti könyvtárat és fájlnevet válassza.

## 5. lépés: Jelenítsen meg egy sikerüzenetet

Végül ünnepelje meg sikerét egy üzenet megjelenítésével:

```csharp
// Sikeres üzenet megjelenítése
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

A primitív modellekből összeállított 3D-s jelenet most elkészült és elmentve!

## Következtetés

 Gratulálunk a lenyűgöző 3D modellek létrehozásához az Aspose.3D for .NET használatával! Ez az oktatóanyag a primitív modellezés alapjait ismertette, de a lehetőségek végtelenek. Fedezzen fel többet a speciális funkciókról és technikákról a[dokumentáció](https://reference.aspose.com/3d/net/).

## GYIK

### Használhatom az Aspose.3D for .NET programot a .NET-től eltérő programozási nyelvekkel?

Az Aspose.3D főként a .NET-et támogatja, de vannak Java- és más platformok verziói is.

### Ingyenes próbaverzió elérhető?

 Igen, kipróbálhatja az Aspose.3D képességeit a[ingyenes próbaverzió](https://releases.aspose.com/).

### Hol találok támogatást az Aspose.3D for .NET számára?

Közösségi támogatásért látogassa meg a[Aspose.3D fórum](https://forum.aspose.com/c/3d/18).

### Hogyan szerezhetek ideiglenes engedélyt?

 Ideiglenes engedélyt kérhet[itt](https://purchase.conholdate.com/temporary-license/).

### Vannak további oktatóanyagok?

 Igen! Fedezzen fel további oktatóanyagokat és példákat a[dokumentáció](https://reference.aspose.com/3d/net/).