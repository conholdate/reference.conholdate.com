---
title: A könyvjelzők láthatóságának kezelése a Word-dokumentumokban
linktitle: A könyvjelzők láthatóságának kezelése a Word-dokumentumokban
second_title: Aspose.Words Document Processing API
description: Fedezze fel, hogyan szabályozhatja szakszerűen a Word-dokumentumok tartalmának láthatóságát az Aspose.Words for .NET segítségével. Ez a lépésenkénti útmutató.
type: docs
weight: 10
url: /hu/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Bevezetés

Készen áll arra, hogy javítsa dokumentumkezelési készségeit az Aspose.Words for .NET segítségével? Legyen szó tapasztalt, dokumentumfeladatokat automatizáló fejlesztőről, vagy kíváncsi egyénről, aki a Word-fájlok programozott vezérlését vizsgálja, ez az útmutató az Ön számára készült. Ma azt vizsgáljuk meg, hogyan jeleníthetünk meg és rejthetünk el tartalmat a Word-dokumentumban lévő könyvjelzők alapján. Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1. Visual Studio: Bármilyen verzió, amely kompatibilis a .NET-tel.
2.  Aspose.Words for .NET: Töltse le[itt](https://releases.aspose.com/words/net/).
3. Alapvető C# ismeretek: Az egyszerű C# programok írásának ismerete elegendő.
4. Word-dokumentum minta: Készítsen egy Word-dokumentumot (pl. "Bookmarks.docx"), amely könyvjelzőket tartalmaz ehhez az oktatóanyaghoz.

### Hozzon létre egy új projektet

1. Nyissa meg a Visual Studio-t, és hozzon létre egy új Console App (.NET Core) projektet. Nevezd el valami ilyesmivel: "BookmarkVisibilityManager".

### Telepítse az Aspose.Words for .NET programot

Adja hozzá az Aspose.Wordst projektjéhez a NuGet Package Manager segítségével:

1. Lépjen az Eszközök > NuGet csomagkezelő > NuGet csomagok kezelése a megoldáshoz menüpontra.
2. Keresse meg az "Aspose.Words" kifejezést.
3. Telepítse a csomagot.

projekt beállítása után kezdjük el a dokumentum betöltését.

## Névterek importálása

Kezdje az alapvető névterek importálásával. Ezek biztosítják az Aspose.Words Word-dokumentumok kezeléséhez szükséges osztályokat és módszereket.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## 1. lépés: A dokumentum betöltése

A Word dokumentum kezeléséhez először be kell töltenünk. Ezt a következőképpen teheti meg:

```csharp
// Határozza meg a dokumentumkönyvtár elérési útját.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Ez a kódrészlet beállítja a dokumentumkönyvtár elérési útját, és betölti a dokumentumot a`Document` objektum.

## 2. lépés: A könyvjelzővel ellátott tartalom megjelenítése/elrejtése

 Most hozzunk létre egy módszert a tartalom láthatóságának váltásra könyvjelzők alapján. Ezt a módszert nevezzük`ShowHideBookmarkedContent`.

Íme a módszer megvalósítása:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Könyvjelzők lekérése:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` lekéri a megadott könyvjelzőt.
- Csomópont bejárás: Iterálunk a könyvjelzőn belüli csomópontokon.
-  Láthatóság kapcsoló: Mindegyikhez`Run` node (szöveg egy szegmense), beállítjuk`Hidden` ingatlan alapján a`isHidden` paraméter.

## 3. lépés: A módszer alkalmazása

Most, hogy a módszerünk készen van, használjuk a tartalom megjelenítésére vagy elrejtésére egy adott könyvjelzőn belül:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Elrejti a tartalmat a "MyBookmark1" mappában
```

Ez a sor elrejti a "MyBookmark1" nevű könyvjelzőhöz társított tartalmat.

## 4. lépés: A dokumentum mentése

Miután elvégezte a módosításokat, ne felejtse el menteni a módosított dokumentumot:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Ezzel menti a dokumentumot a frissített láthatósági beállításokkal.

## Következtetés

Gratulálok! Sikeresen megtanulta, hogyan jeleníthet meg és rejthet el könyvjelzővel ellátott tartalmat egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a nagy teljesítményű könyvtár leegyszerűsíti a dokumentumok kezelését, így ideális a jelentések automatizálásához, sablonok létrehozásához vagy Word fájlokkal való kísérletezéshez. Boldog kódolást!

## GYIK

### Válthatok több könyvjelzőt egyszerre?
 Igen, egyszerűen hívja a`ShowHideBookmarkedContent` módszert minden egyes átkapcsolni kívánt könyvjelzőhöz.

### A tartalom elrejtése befolyásolja a dokumentum szerkezetét?
Nem, a tartalom elrejtése csak annak láthatóságát befolyásolja; a tartalom érintetlen marad a dokumentumon belül.

### Használhatom ezt a módszert más típusú tartalomhoz?
Ezt a módszert kifejezetten szövegfuttatásokhoz tervezték. Más tartalomtípusok esetén ennek megfelelően módosítania kell a csomópont bejárási logikáját.

### Az Aspose.Words for .NET ingyenes?
 Az Aspose.Words ingyenes próbaverziót kínál[itt](https://releases.aspose.com/) , de a termelési felhasználáshoz teljes licenc szükséges. Megvásárolhatod[itt](https://purchase.aspose.com/buy).

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatásért keresse fel az Aspose közösségi fórumot[itt](https://forum.aspose.com/c/words/8).