---
title: Fájlok csatolása és ikonok beállítása az Aspose.Note for .NET programban
linktitle: Csatoljon fájlt és állítsa be az ikont az Aspose.Note-ban
second_title: Aspose.Note .NET API
description: Ismerje meg lépésről lépésre, hogyan csatolhat fájlokat és állíthat be egyéni ikonokat a Microsoft OneNote dokumentumokban az Aspose.Note for .NET használatával. Bővítse .NET-alkalmazását zökkenőmentes dokumentumkezelési és testreszabási funkciókkal.
type: docs
weight: 10
url: /hu/net/tutorials/note/manage-attachments/attaching-files-setting-icons/
---
## Bevezetés

Az Aspose.Note for .NET egy fejlett könyvtár, amelyet a fejlesztők számára terveztek Microsoft OneNote-fájlok programozott létrehozására, kezelésére és konvertálására. A könyvtár kiemelkedő funkciója, hogy képes fájlokat csatolni a OneNote-dokumentumokhoz, és személyre szabni az ikonjaikat. Ebben az útmutatóban megvizsgáljuk, hogyan használhatja ki az Aspose.Note for .NET alkalmazást a fájlok zökkenőmentes csatolásához és egyéni ikonok beállításához, gazdagítva ezzel a OneNote dokumentumfunkcióit.

## Előfeltételek

A megoldás bevezetése előtt győződjön meg arról, hogy rendelkezik az alábbiakkal:

- Fejlesztői környezet: Visual Studio vagy egy hasonló IDE .NET-fejlesztéshez konfigurálva.
-  Könyvtár telepítése: Telepítse a[Aspose.Note for .NET](https://releases.aspose.com/words/net/) könyvtár.
- Programozási ismeretek: A C# alapvető ismerete.

## Kötelező névterek importálása

Adja hozzá ezeket a névtereket a projekthez az alapvető funkciók érdekében:

```csharp
using System.IO;
using Aspose.Note;
using System;
using System.Collections.Generic;
using System.Drawing.Imaging;
```

Az alábbiakban bemutatjuk a részletes, lépésről lépésre történő megvalósítást.

## 1. lépés: Hozzon létre egy új OneNote-dokumentumot

 Inicializáljon egy új OneNote-dokumentumot a`Document`osztály.

```csharp
Document doc = new Document();
```

## 2. lépés: Új oldal hozzáadása

Adjon hozzá egy oldalt a dokumentumhoz a jegyzetek és mellékletek rendszerezéséhez.

```csharp
Aspose.Note.Page page = new Aspose.Note.Page(doc);
```

## 3. lépés: Állítson be egy körvonalat

 Hozzon létre egy`Outline` objektum, amely a OneNote oldalon lévő elemek tárolójaként szolgál.

```csharp
Outline outline = new Outline(doc);
```

## 4. lépés: Inicializáljon egy Vázlat elemet

 An`OutlineElement` tartalmazza a mellékletet és a hozzá tartozó ikont.

```csharp
OutlineElement outlineElem = new OutlineElement(doc);
```

## 5. lépés: Csatoljon egy fájlt, és adja meg az ikonját

Adja meg a csatolni kívánt fájlt, és adjon hozzá egy ikont.

```csharp
string dataDir = "Your Document Directory";

using (var stream = File.OpenRead(dataDir + "icon.jpg"))
{
    AttachedFile attachedFile = new AttachedFile(doc, dataDir + "attachment.txt", stream, ImageFormat.Jpeg);
    outlineElem.AppendChildLast(attachedFile);
}
```

## 6. lépés: Állítsa össze a dokumentumszerkezetet

 Add hozzá a`OutlineElement` a`Outline` , és a`Outline` a`Page`.

```csharp
outline.AppendChildLast(outlineElem);
page.AppendChildLast(outline);
```

## 7. lépés: Adja hozzá az oldalt a dokumentumhoz

Végül foglalja bele az oldalt a OneNote-dokumentumba.

```csharp
doc.AppendChildLast(page);
```

## 8. lépés: Mentse el a dokumentumot

Exportálja a frissített dokumentumot a fájlmelléklettel és ikonnal.

```csharp
dataDir = dataDir + "AttachFileAndSetIcon_out.one";
doc.Save(dataDir);
```

## Következtetés

Az ebben az útmutatóban ismertetett lépések követésével könnyedén csatolhat fájlokat és állíthat be egyéni ikonokat a OneNote-dokumentumokban az Aspose.Note for .NET segítségével. Ez a funkció nagymértékben javíthatja a dokumentumok rendszerezését és a felhasználói élményt, így alkalmazásai robusztusabbak és funkciókban gazdagabbak.

## GYIK

### Egy jegyzethez több fájl is csatolható?
Igen, több fájlt is csatolhat, ha minden fájlhoz megismétli a csatolási folyamatot.

### Milyen képformátumok támogatottak az ikonokhoz?
Az Aspose.Note támogatja a JPEG, PNG, BMP és GIF formátumokat a melléklet ikonokhoz.

### Lehetséges-e dinamikusan csatolni fájlokat külső URL-ekről?
 Fájlokat tölthet le .NET-könyvtárak használatával, például`HttpClient` majd csatolja őket az Aspose.Note segítségével.

### Vannak korlátozások a mellékletek fájlméretére vonatkozóan?
Az Aspose.Note nem ír elő kifejezett méretkorlátot, de ügyeljen arra, hogy a rendszererőforrások képesek legyenek kezelni a nagy fájlokat.

### Átméretezhetők az ikonok beállítása előtt?
 Igen, manipulálhatja az ikonképet a .NET segítségével`System.Drawing` csatolása előtt.

 További segítségért keresse fel a[dokumentáció](https://reference.aspose.com/words/net/) vagy nyúlj hozzá[Aspose támogatást](https://forum.aspose.com/c/words/8).