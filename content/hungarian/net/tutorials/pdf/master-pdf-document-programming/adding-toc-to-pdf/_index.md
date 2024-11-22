---
title: Tartalomjegyzék hozzáadása PDF-dokumentumhoz
linktitle: Tartalomjegyzék hozzáadása PDF-dokumentumhoz
second_title: Aspose.PDF for .NET API Reference
description: Ez az oktatóanyag bemutatja, hogyan adhat hozzá tartalomjegyzéket (TOC) egy PDF-dokumentumhoz az Aspose.Pdf for .NET használatával.
type: docs
weight: 40
url: /hu/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Bevezetés

Tartalomjegyzék (TOC) létrehozása egy PDF-dokumentumban nagymértékben javíthatja a navigációt és a hozzáférhetőséget. Ebben az útmutatóban bemutatjuk, hogyan adhat hozzá TOC-t egy PDF-fájlhoz az Aspose.Pdf for .NET használatával.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.   Aspose.PDF for .NET: Töltse le és telepítse a legújabb verziót innen[itt](https://releases.aspose.com/pdf/net/).
2.  Fejlesztői környezet: Hozzon létre egy .NET fejlesztői környezetet, például a Visual Studio-t.
3.   Licenc: Ha szükséges, kérjen ideiglenes engedélyt; kérjük látogassa meg[Aspose.Pdf licencelési oldal](https://asposepdf.com/developers) további információkért.

Szükséges könyvtárak importálása

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## 1. lépés: Töltse be a PDF-dokumentumot

Töltse be a meglévő PDF-fájlt, ahová a tartalomjegyzéket hozzá szeretné adni. Adja meg a dokumentumkönyvtár elérési útját.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## 2. lépés: Szúrjon be egy új oldalt a TOC-hoz

Szúrjon be egy új oldalt a PDF dokumentum elejére. Ez az oldal tartalomjegyzékként (TOC) fog szolgálni.

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## 3. lépés: Hozzon létre egy TOC információs objektumot

Hozzon létre egy objektumot, amely képviseli a TOC információkat. Adjon hozzá címet és linket a jobb navigáció érdekében.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## 4. lépés: Határozza meg a TOC elemeket

Határozza meg azokat az elemeket (vagy címsorokat), amelyek megjelennek a tartalomjegyzékben. Ezek az elemek segíthetnek az olvasóknak eligazodni a dokumentum bizonyos részeihez.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## 5. lépés: Hozzon létre TOC címsorokat

Hozzon létre fejlécet a tartalomjegyzék első két eleméhez. Ezek a címsorok a megfelelő oldalakra hivatkoznak.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## 6. lépés: Mentse el a PDF-fájlt a tartalomjegyzékkel

Végül mentse a frissített PDF-fájlt.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Megerősítő üzenet

Jelenítsen meg egy megerősítő üzenetet, amely tudatja a felhasználóval, hogy a folyamat befejeződött.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Következtetés

Az Aspose.PDF for .NET segítségével tartalomjegyzék hozzáadása a PDF-hez nem csak egyszerű, hanem testreszabható is. Akár egyszerű navigációs hivatkozásokat, akár összetett struktúrákat kell létrehoznia, ez az eszköz mindent megtalál. Tehát, ha legközelebb egy hosszadalmas PDF-en dolgozik, ne felejtse el hozzáadni a TOC-t ehhez a professzionális érintéshez.

## GYIK

### Testreszabhatom a TOC megjelenését az Aspose.PDF-ben?

Igen, teljes mértékben testreszabhatja a tartalomjegyzék megjelenését, beleértve a betűstílust, -méretet és az igazítást.

### Hogyan adhatok alcímeket a tartalomjegyzékhez?

 Alcímeket adhat hozzá a`Heading` szinten (pl.`Heading(2)`).

### Lehetséges a TOC automatikus frissítése, ha a dokumentum megváltozik?

Nem, a tartalomjegyzék nem frissül automatikusan. Újra kell létrehoznia, ha a dokumentum szerkezete megváltozik.

### Összekapcsolhatom a TOC bejegyzéseket külső dokumentumokkal?

Igen, hiperhivatkozások segítségével tartalomjegyzék-bejegyzéseket külső PDF-ekhez vagy URL-ekhez kapcsolhat.

### Az Aspose.PDF támogatja a többszintű tartalomjegyzékeket?

Igen, az Aspose.PDF támogatja a többszintű tartalomjegyzéket az alszakaszokkal rendelkező összetett dokumentumokhoz.
