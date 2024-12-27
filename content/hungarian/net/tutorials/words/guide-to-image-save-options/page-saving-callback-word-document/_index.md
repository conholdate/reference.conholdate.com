---
title: Oldal mentése visszahívás Word dokumentumokban
linktitle: Oldal mentése visszahívás Word dokumentumokban
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan konvertálhat egyszerűen egy Word-dokumentum egyes oldalait egyedi PNG-képekké az Aspose.Words for .NET segítségével. Ez az útmutató lépésről lépésre tartalmaz utasításokat, beleértve a kódpéldákat.
type: docs
weight: 10
url: /hu/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Bevezetés

Szüksége volt már arra, hogy egy Word-dokumentum minden oldalát egyedi képekké alakítsa? Akár bélyegképeket szeretne készíteni az előnézethez, akár egy hosszú jelentést emészthető látványelemekre szeretne lebontani, az Aspose.Words for .NET egyszerűvé és hatékonysá teszi ezt a feladatot. Ebben az útmutatóban végigvezetjük az oldalmentő visszahívás beállításának folyamatán, amellyel a dokumentum minden oldalát PNG-képként mentheti el. Kezdjük is!

## Előfeltételek

Búvárkodás előtt győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET: Töltse le és telepítse a webhelyről[itt](https://releases.aspose.com/words/net/).
2. Visual Studio: Bármelyik verzió működik, de ehhez az útmutatóhoz a Visual Studio 2019-et fogjuk használni.
3. Alapvető C# ismeretek: A C# ismerete segít a zökkenőmentes követésben.

## 1. lépés: Importálja a szükséges névtereket

Először is importálnunk kell a szükséges névtereket. Ez lehetővé teszi a szükséges osztályok és metódusok elérését anélkül, hogy minden alkalommal beírnánk a teljes névteret.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 2. lépés: Határozza meg a dokumentumkönyvtárat

Ezután állítsa be a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a bevitt Word-dokumentum található, és ahol a kimeneti képek mentésre kerülnek.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 3. lépés: Töltse be a dokumentumot

Most töltsük be a feldolgozni kívánt dokumentumot. Győződjön meg arról, hogy a „Rendering.docx” nevű dokumentum a megadott könyvtárban van.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 4. lépés: Állítsa be a képmentési beállításokat

Beállítjuk a képek mentési lehetőségeit, megadva, hogy az oldalakat PNG-fájlként szeretnénk menteni.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Itt,`PageSet` meghatározza a menteni kívánt oldalak tartományát, és`PageSavingCallback` rámutat az egyéni visszahívási osztályunkra.

## 5. lépés: Végezze el az Oldalmentés visszahívását

Most végre kell hajtanunk a visszahívási osztályt, amely kezeli az egyes oldalak mentését.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Ez az osztály valósítja meg a`IPageSavingCallback` felület. A`PageSaving` módszerrel minden mentett oldalhoz megadjuk az elnevezési mintát.

## 6. lépés: Mentse el a dokumentumot képekként

Végül elmentjük a dokumentumot a beállított opciókkal.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Következtetés

Gratulálok! Sikeresen beállított egy oldalmentő visszahívást, amellyel egy Word-dokumentum minden oldalát külön PNG-képként mentheti az Aspose.Words for .NET segítségével. Ez a technika hihetetlenül hasznos a különböző alkalmazásokhoz, az oldal-előnézetek létrehozásától a jelentésekhez készített egyedi oldalképekig.

## GYIK

### Menthetek oldalakat a PNG-től eltérő formátumban?
 Igen! Az oldalakat JPEG, BMP és TIFF formátumban mentheti, ha módosítja a`SaveFormat` be`ImageSaveOptions`.

### Hogyan menthetek csak bizonyos oldalakat?
 Adott oldalak mentéséhez állítsa be a`PageSet` paraméter be`ImageSaveOptions` hogy csak a kívánt oldalakat tartalmazza.

### Testreszabható a képminőség?
 Teljesen! A kimeneti képminőséget olyan tulajdonságok beállításával szabályozhatja, mint pl`ImageSaveOptions.JpegQuality`.

### Hogyan kezelhetek hatékonyan nagy dokumentumokat?
Nagyméretű dokumentumok esetén fontolja meg az oldalak kötegelt feldolgozását a memóriahasználat hatékony kezelése érdekében.

### Hol találhatok további információt az Aspose.Words for .NET-ről?
 Átfogó útmutatókért és példákért tekintse meg a[Aspose.Words dokumentáció](https://reference.aspose.com/words/net/).