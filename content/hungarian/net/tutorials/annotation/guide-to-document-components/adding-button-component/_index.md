---
title: Gombkomponensek hozzáadása a GroupDocs.Annotation segítségével .NET-hez
linktitle: Gombkomponensek hozzáadása
second_title: GroupDocs.Annotation .NET API
description: Fedezze fel, hogyan javíthatja PDF-dokumentumait interaktív gombkomponensek hozzáadásával a GroupDocs.Annotation for .NET segítségével. Ez a lépésről lépésre bemutató oktatóanyag.
type: docs
weight: 10
url: /hu/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Bevezetés

Ebben az oktatóanyagban végigvezetjük Önt azon az egyszerű folyamaton, amellyel a .NET GroupDocs.Annotation könyvtárát használva adhatók hozzá egy gombkomponens PDF-dokumentumhoz. Az útmutató végére készen áll arra, hogy PDF-dokumentumait interaktív funkciókkal bővítse.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következők vannak a helyükön:

1.  GroupDocs.Annotation for .NET: Töltse le és telepítse a GroupDocs.Annotation for .NET könyvtárat innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: A .NET keretrendszerrel telepítsen megfelelő fejlesztői környezetet.

## 1. lépés: Importálja a szükséges névtereket

Kezdje azzal, hogy importálja a szükséges névtereket a projektbe:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## 2. lépés: Inicializálja a kimeneti útvonalat

Határozza meg a kimeneti útvonalat, ahová a módosított PDF mentésre kerül:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 3. lépés: Adjon hozzá egy gombkomponenst

Most hozzuk létre és adjuk hozzá a gombkomponenst a PDF-hez:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // A gomb helyzete és mérete
        PenColor = 65535,                       // Gombszegély színe
        Style = BorderStyle.Dashed,             // Szegély stílus
        BorderWidth = 0,                        // Szegély szélessége
        BorderColor = 0,                        // Szegély színe
        AlternateName = "Name",                 // A gomb alternatív neve
        PartialName = "Partial Name",           // A gomb részleges neve
        NormalCaption = "Caption",               // A gombon megjelenő szöveg
        ButtonColor = 16761035,                 // A gomb háttérszíne
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Adja hozzá a gombot az annotátorhoz
    annotator.Save("result.pdf"); // Mentse el a módosított PDF-et
}
```

## 4. lépés: Kimeneti útvonal megjelenítése

Végül tájékoztassa a felhasználót a kimeneti fájl mentési helyére:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Gratulálok! Sikeresen hozzáadott egy gombkomponenst egy PDF-dokumentumhoz a GroupDocs.Annotation for .NET segítségével.

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan építhet be gombösszetevőket PDF-dokumentumokba a GroupDocs.Annotation for .NET segítségével. Az alábbi lépések követésével jelentősen javíthatja PDF-dokumentumai interaktivitását.

## GYIK

### Testreszabhatom a gomb megjelenését?

Teljesen! Különféle tulajdonságokat, például méretet, színt és stílust módosíthat igényei szerint.

### A GroupDocs.Annotation for .NET kompatibilis az összes PDF-verzióval?

Igen, a GroupDocs.Annotation for .NET a PDF-verziók széles skáláját támogatja, biztosítva a kompatibilitást a legtöbb dokumentummal.

### Hozzáadhatok több gombösszetevőt egyetlen PDF dokumentumhoz?

Igen, tetszőleges számú gombelemet adhat hozzá egy PDF-dokumentumhoz.

### A GroupDocs.Annotation for .NET támogat más fájlformátumokat?

Igen, a PDF mellett számos dokumentumformátumot támogat, beleértve a DOCX, PPTX és XLSX fájlokat.

### Létezik próbaverzió tesztelési célból?

 Igen, elérheti a GroupDocs.Annotation ingyenes próbaverzióját a .NET-hez innen[itt](https://releases.groupdocs.com/).
