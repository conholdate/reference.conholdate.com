---
title: Szöveges aláírások hozzáadása a dokumentumokhoz a GroupDocs.Signature segítségével
linktitle: Szöveges aláírások hozzáadása a dokumentumokhoz
second_title: GroupDocs.Signature .NET API
description: Ismerje meg, hogyan írhat alá dokumentumokat szöveggel a GroupDocs.Signature for .NET használatával. Lépésről lépésre szóló útmutató szöveges aláírások programozott hozzáadásához.
type: docs
weight: 17
url: /hu/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Bevezetés

A mai digitális környezetben az elektronikus dokumentum-aláírás elengedhetetlenné vált a munkafolyamatok egyszerűsítéséhez és az erőforrások megtakarításához. A GroupDocs.Signature for .NET hatékony megoldást kínál szöveges aláírások programozott hozzáadásához különböző dokumentumformátumokhoz. Ez az oktatóanyag végigvezeti Önt egy szöveges dokumentum aláírásának lépésein a GroupDocs.Signature for .NET használatával.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  GroupDocs.Signature for .NET: Töltse le és telepítse a könyvtárat innen[itt](https://releases.groupdocs.com/signature/net/).
2. Fejlesztési környezet: Állítsa be a .NET fejlesztői környezetet.
3. Dokumentum: Készítse elő az aláírni kívánt dokumentumot (pl. PDF, Word).

## A szükséges névterek importálása

Kezdje azzal, hogy importálja a szükséges névtereket a .NET-projektbe:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 1. lépés: Töltse be a dokumentumot

Kezdje az aláírni kívánt dokumentum betöltésével:

```csharp
string filePath = "sample.pdf"; // A dokumentum elérési útja
string fileName = Path.GetFileName(filePath);
```

## 2. lépés: Határozza meg a kimeneti fájl elérési útját

Ezután állítsa be a kimeneti fájl elérési útját, ahová az aláírt dokumentum mentésre kerül:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## 3. lépés: Aláírási beállítások létrehozása

Konfigurálja a szöveges aláírás beállításait, beleértve a tartalmat, pozíciót, méretet, színt és betűstílust:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X pozíció
    Top = 200, // Y pozíció
    Width = 100, // Az aláírás szélessége
    Height = 30, // Az aláírás magassága
    ForeColor = Color.Red, // Szöveg színe
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Betűtípus beállítások
};
```

## 4. lépés: Aláírja a dokumentumot

Végül a GroupDocs.Signature segítségével alkalmazza a szöveges aláírást, és mentse az aláírt dokumentumot:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Írja alá a dokumentumot
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan adhatunk programozottan szöveges aláírást egy dokumentumhoz a GroupDocs.Signature for .NET használatával. Az alábbi lépések követésével hatékonyan növelheti dokumentumai biztonságát és hitelességét.

## GYIK

### Testreszabhatom a szöveges aláírás megjelenését?
Igen, testreszabhatja a különféle attribútumokat, például a színt, a betűtípust, a méretet és a szövegaláírás pozícióját, hogy megfeleljen az Ön igényeinek.

### A GroupDocs.Signature kompatibilis több dokumentumformátummal?
Teljesen! A GroupDocs.Signature formátumok széles skáláját támogatja, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.

### Hozzáadhatok több szöveges aláírást egyetlen dokumentumhoz?
Igen, több szöveges aláírást is hozzáadhat, mindegyik saját testreszabási lehetőséggel.

### A GroupDocs.Signature biztosítja a dokumentum integritását az aláírás után?
Igen, a könyvtár robusztus kriptográfiai algoritmusokat használ a dokumentum integritásának biztosítására és az aláírás utáni manipuláció megelőzésére.

### Vásárlás előtt kipróbálható-e próbaverzió?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/) hogy vásárlás előtt fedezze fel a funkciókat.