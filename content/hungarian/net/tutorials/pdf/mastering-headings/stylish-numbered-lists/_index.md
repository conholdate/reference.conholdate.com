---
title: Stílusos számozott listák Aspose.PDF használatával .NET-hez
linktitle: Stílusos számozott listák Aspose.PDF használatával .NET-hez
second_title: Aspose.PDF for .NET API Reference
description: Fedezze fel, hogyan hozhat létre gyönyörűen számozott listákat PDF-dokumentumaiban az Aspose.PDF for .NET segítségével. Ez az útmutató végigvezeti a különféle számozási stílusok – például a római számok – alkalmazásán.
type: docs
weight: 10
url: /hu/net/programming-with-headings/stylish-numbered-lists/
---
## Bevezetés

Szüksége volt valaha is jól strukturált, számozott listák létrehozására PDF-dokumentumaiban? Legyen szó jogi dokumentumokról, jelentésekről vagy prezentációkról, a hatékony számozási stílusok kulcsfontosságúak a tartalom rendszerezéséhez. Az Aspose.PDF for .NET segítségével könnyedén alkalmazhat különféle számozási stílusokat a PDF címsoraihoz, így csiszolt és professzionális dokumentumokat készíthet.

## Előfeltételek

Mielőtt belevágnánk a kódolásba, győződjön meg arról, hogy készen áll a következőkre:

1.  Aspose.PDF for .NET: Töltse le a legújabb verziót innen[itt](https://releases.aspose.com/pdf/net/).
2. Fejlesztői környezet: Szüksége lesz a Visual Studiora vagy bármely .NET-kompatibilis IDE-re.
3. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer 4.0-s vagy újabb verziója.
4.  Licenc: Ideiglenes licencet használhat[itt](https://purchase.aspose.com/temporary-license/) vagy fedezze fel a[ingyenes próbaverzió](https://releases.aspose.com/) opciók.

## A szükséges csomagok importálása

Kezdje a szükséges névterek importálásával a projektben:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## 1. lépés: A dokumentum beállítása

Kezdjük egy új PDF-dokumentum létrehozásával, és konfiguráljuk az elrendezését, beleértve az oldalméretet és a margókat.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Állítsa be az oldalméreteket és a margókat
pdfDoc.PageInfo.Width = 612.0; // 8,5 hüvelyk
pdfDoc.PageInfo.Height = 792.0; // 11 hüvelyk
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // 1 hüvelykes margók
```

Ezzel a beállítással a dokumentum szabványos betűméretet biztosít, minden oldalán egy hüvelykes margókkal.

## 2. lépés: Oldal hozzáadása a PDF-hez

Ezután adunk hozzá egy üres oldalt a PDF dokumentumhoz, ahol később alkalmazzuk a számozási stílusokat.

```csharp
// Új oldal hozzáadása a PDF dokumentumhoz
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; //Használja ugyanazokat a beállításokat, mint a dokumentum
```

## 3. lépés: Lebegő doboz létrehozása

A FloatingBox lehetővé teszi, hogy a tartalmat az oldal áramlásától függetlenül helyezze el, így jobban irányíthatja az elrendezést.

```csharp
// Hozzon létre egy FloatingBoxot a strukturált tartalomhoz
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## 4. lépés: Címsorok hozzáadása római számokkal

Most adjuk hozzá az első címsorunkat kisbetűs római számozással.

```csharp
// Hozza létre az első címsort római számokkal
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## 5. lépés: Második címsor hozzáadása egyéni kezdőszámmal

Ezután hozzáadunk egy második címsort a 13-as római számtól kezdve.

```csharp
// Hozzon létre egy második címsort, amely a 13-as római számmal kezdődik
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## 6. lépés: Címsor hozzáadása alfabetikus számozással

A változatosság kedvéért adjunk hozzá egy harmadik címsort a kisbetűs alfabetikus számozással.

```csharp
// Hozzon létre egy címsort alfabetikus számozással
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## 7. lépés: A PDF mentése

Végül mentsük a PDF fájlt a kívánt könyvtárba.

```csharp
// Mentse el a PDF dokumentumot
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Következtetés

Gratulálok! Sikeresen alkalmazta a különböző számozási stílusokat – római számokat és ábécé – a PDF-fájlok fejléceihez az Aspose.PDF for .NET használatával. Az Aspose.PDF rugalmassága lehetővé teszi az oldalelrendezés, a számozási stílusok és a tartalom elhelyezésének szabályozását, így jól szervezett és professzionális PDF dokumentumokat hozhat létre.

## GYIK

### Alkalmazhatok különböző számstílusokat ugyanarra a PDF dokumentumra?  
Igen, ugyanazon a dokumentumon belül keverhet különböző számozási stílusokat, például római számokat, arab számokat és alfabetikus számozást.

### Hogyan szabhatom testre a címsorok kezdőszámát?  
 Bármely címsor kezdőszámát beállíthatja a gombbal`StartNumber` ingatlan.

### Van mód a számozási sorrend visszaállítására?  
 Igen, visszaállíthatja a számozást a`StartNumber` tulajdonság minden címsorhoz.

### Alkalmazhatok félkövér vagy dőlt stílust a címsorokon a számozáson kívül?  
 Teljesen! Testreszabhatja a fejlécstílusokat a tulajdonságok, például a betűtípus, a méret, a félkövér és a dőlt betűk használatával történő módosításával`TextState` objektum.

### Hogyan szerezhetek ideiglenes licencet az Aspose.PDF fájlhoz?  
 Ideiglenes jogosítványt szerezhet be[itt](https://purchase.aspose.com/temporary-license/)az Aspose.PDF korlátozások nélküli teszteléséhez.