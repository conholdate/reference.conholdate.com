---
title: Szöveg hozzáfűzése a Word-dokumentumok könyvjelzővel ellátott szakaszaiból
linktitle: Szöveg hozzáfűzése a Word-dokumentumok könyvjelzővel ellátott szakaszaiból
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan fűzhet zökkenőmentesen szöveget egy Word-dokumentum könyvjelzővel ellátott részeiből az Aspose.Words for .NET segítségével. Ez a lépésről lépésre bemutató oktatóanyag.
type: docs
weight: 10
url: /hu/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Bevezetés

Előfordult már, hogy kihívást jelentett egy Word-dokumentum könyvjelzővel ellátott szakaszából szöveget hozzáfűzni? Jó helyen jársz! Ez az oktatóanyag lépésről lépésre végigvezeti a folyamaton az Aspose.Words for .NET használatával. A végére profi módon hozzáfűzheti a könyvjelzővel ellátott szöveget. Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Words for .NET: Ha még nem telepítette, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: .NET fejlesztői környezet, például a Visual Studio.
- Alapvető C# ismerete: Az alapvető C# programozási fogalmak ismerete előnyt jelent.
- Word-dokumentum könyvjelzőkkel: Word-dokumentum, amely könyvjelzőket tartalmaz, amelyekből szöveget fogunk hozzáfűzni.

## Importálja a szükséges névtereket

Először is importálnunk kell a szükséges névtereket az Aspose.Words funkciók eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## 1. lépés: Töltse be a dokumentumot és inicializálja a változókat

Kezdjük azzal, hogy betöltjük a forrás és cél Word dokumentumainkat, és inicializáljuk a szükséges változókat.

```csharp
//Töltse be a forrás- és céldokumentumot.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializálja a dokumentumimportőrt.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Keresse meg a könyvjelzőt a forrásdokumentumban.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 2. lépés: Határozza meg a kezdő és záró bekezdéseket

Ezután meg kell találnunk azokat a bekezdéseket, ahol a könyvjelző kezdődik és végződik. Ez elengedhetetlen a megfelelő szöveg kinyeréséhez.

```csharp
// Határozza meg a bekezdéseket a könyvjelző elején és végén.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Érvényesítse a bekezdéseket.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## 3. lépés: A bekezdésszülők érvényesítése

Biztosítanunk kell, hogy a kezdő és a záró bekezdés ugyanazon a szülőcsomóponton osztozzon. Ez egy egyszerűsített megközelítés a komplikációk elkerülése érdekében.

```csharp
// Ellenőrizze, hogy a kezdő és a záró bekezdésnek ugyanaz a szülője.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## 4. lépés: Határozza meg a leállítandó csomópontot

Most meg kell határoznunk, hogy hol állítsuk le a szöveg másolását, amely a csomópont közvetlenül a záró bekezdés után lesz.

```csharp
// Azonosítsa a csomópontot közvetlenül a bekezdés befejezése után.
Node endNode = endPara.NextSibling;
```

## 5. lépés: Adja hozzá a könyvjelzővel ellátott szöveget a céldokumentumhoz

Végül a csomópontokat a kezdő bekezdéstől a záró bekezdés utáni csomópontig hurcoljuk, és hozzáfűzzük őket a céldokumentumhoz.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Importálja az aktuális csomópontot a céldokumentumba.
    Node newNode = importer.ImportNode(curNode, true);

    // Az importált csomópont hozzáfűzése a céldokumentumhoz.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Mentse el a frissített céldokumentumot.
dstDoc.Save("appended_document.docx");
```

## Következtetés

Gratulálok! Sikeresen hozzáfűzte egy Word-dokumentum könyvjelzővel ellátott szakaszának szövegét az Aspose.Words for .NET segítségével. Ez a nagy teljesítményű könyvtár egyszerűvé teszi a dokumentumok kezelését, és most egy másik praktikus készség is van az eszköztárban. Boldog kódolást!

## GYIK

### Hozzáfűzhetek szöveget több könyvjelzőből egyszerre?
Igen, megismételheti a folyamatot minden könyvjelzőnél, és szükség szerint hozzáfűzheti a szöveget.

### Mi van akkor, ha a kezdő és a záró bekezdésnek különböző szülője van?
A jelenlegi példa azt feltételezi, hogy ugyanaz a szülő. Ha nem, akkor összetettebb kezelést kell végrehajtania.

### Megmarad a hozzáfűzött szöveg eredeti formázása?
 Teljesen! Használata`ImportFormatMode.KeepSourceFormatting`biztosítja az eredeti formázás megőrzését.

### Lehetséges-e szöveget hozzáfűzni a céldokumentum egy adott helyéhez?
Igen, bármilyen kívánt pozícióhoz hozzáfűzhet szöveget, ha a céldokumentum megfelelő csomópontjához navigál.

### Hozzáfűzhetek szöveget egy könyvjelzőből egy új szakaszhoz?
Igen, létrehozhat egy új szakaszt a céldokumentumban, és hozzáfűzheti a szöveget.