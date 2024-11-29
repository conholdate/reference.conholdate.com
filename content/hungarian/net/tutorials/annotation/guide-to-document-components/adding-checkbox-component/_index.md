---
title: Jelölőnégyzet komponens hozzáadása a PDF-dokumentumhoz
linktitle: Jelölőnégyzet komponens hozzáadása a PDF-dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Fedezze fel, hogyan gazdagíthatja PDF-dokumentumait interaktív jelölőnégyzet-összetevők hozzáadásával a GroupDocs.Annotation for .NET SDK használatával. Ez az átfogó oktatóanyag világos, lépésenkénti útmutatót ad.
type: docs
weight: 11
url: /hu/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## Bevezetés

Ebben az oktatóanyagban végigvezetjük a jelölőnégyzet-összetevő PDF-dokumentumhoz való hozzáadásának folyamatán a GroupDocs.Annotation for .NET SDK használatával. Ez a funkció lehetővé teszi, hogy PDF-dokumentumait interaktív elemekkel bővítse, így azok még vonzóbbá válnak a felhasználók számára.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  GroupDocs.Annotation for .NET SDK: Töltse le innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Állítson be egy .NET fejlesztői környezetet a gépén.

## 1. lépés: Importálja a szükséges névtereket

Először foglalja bele a szükséges névtereket a projektbe:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## 2. lépés: Határozza meg a kimeneti útvonalat

Adja meg, hogy a módosított PDF-dokumentum hova kerüljön mentésre:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 3. lépés: Inicializálja az annotátort

 Hozzon létre egy példányt a`Annotator` osztály a bemeneti PDF-dokumentum elérési útjával:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## 4. lépés: A jelölőnégyzet összetevő létrehozása

Most hozzuk létre és szabjuk testre a Checkbox komponenst:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // Határozza meg a pozíciót és a méretet
    PenColor = 65535, // Állítsa be a színt (ebben az esetben sárga)
    Style = BoxStyle.Star, // Válasszon stílust a jelölőnégyzethez
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## 5. lépés: Adja hozzá a jelölőnégyzetet a dokumentumhoz

Adja hozzá a létrehozott jelölőnégyzet összetevőt a PDF-hez:

```csharp
annotator.Add(checkBox);
```

## 6. lépés: Mentse el a módosított dokumentumot

Mentse el a frissített PDF-dokumentumot a jelölőnégyzettel:

```csharp
annotator.Save("result.pdf");
```

## 7. lépés: Jelenítse meg a kimeneti útvonalat

Végül tájékoztassa a felhasználót, hogy hova menti a módosított dokumentumot:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés

Ebben az oktatóanyagban sikeresen hozzáadtunk egy jelölőnégyzet-összetevőt egy PDF-dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ezzel a funkcióval interaktív PDF-fájlokat hozhat létre, amelyek javíthatják a felhasználói élményt és elköteleződést.

## GYIK

### Testreszabhatom a jelölőnégyzet megjelenését?

Teljesen! Különféle tulajdonságokat, például színt, stílust és méretet módosíthat sajátos igényei szerint.

### A GroupDocs.Annotation for .NET alkalmas kereskedelmi használatra?

Igen, a GroupDocs.Annotation for .NET kereskedelmi licenceket biztosít a vállalkozások számára.

### Kipróbálhatom a GroupDocs.Annotation for .NET szolgáltatást a vásárlás előtt?

 Igen, ingyenes próbaverzió áll rendelkezésre. Hozzáférhetsz[itt](https://releases.groupdocs.com/).

### Hol találok támogatást a GroupDocs.Annotation for .NET számára?

 Támogatás és további források állnak rendelkezésre a webhelyen[GroupDocs fórum](https://forum.groupdocs.com/c/annotation/10).

### Szükségem van ideiglenes licencre tesztelés céljából?

 Ideiglenes engedélyt a teszteléshez szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).