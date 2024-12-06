---
title: Hozzon létre 1Bpp indexelt
linktitle: Hozzon létre 1Bpp indexelt
second_title: Aspose.Words Document Processing API
description: Ez az útmutató lépésenkénti utasításokat és mintakódot tartalmaz, amelyek segítségével hatékonyan hozhat létre 1 Bpp indexelt képeket archiválási, nyomtatási vagy helytakarékossági célokra.
type: docs
weight: 10
url: /hu/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Bevezetés

Szüksége volt valaha egy Word-dokumentumot fekete-fehér képpé alakítani? Legyen szó digitális archiválásról, nyomtatásról vagy egyszerűen helytakarékosságról, a dokumentumok 1 Bpp indexelt képpé konvertálása hihetetlenül hasznos lehet. Ebben az útmutatóban egy egyszerű módszert mutatunk be ennek eléréséhez az Aspose.Words for .NET használatával. Kezdjük is!

## Előfeltételek

Mielőtt belemerülne a kódba, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Words for .NET: Töltse le és telepítse a könyvtárat innen[itt](https://releases.aspose.com/words/net/).
- .NET fejlesztői környezet: Bár a Visual Studio népszerű választás, minden .NET-et támogató IDE működik.
- Alapvető C# ismeretek: A C# ismerete segít, de mi mindent egyszerűnek tartunk.
- Word-dokumentum minta: Készítsen egy dokumentumot az átalakításra.

## 1. lépés: Importálja a szükséges névtereket

Az Aspose.Words használatához importálnia kell a megfelelő névtereket. Ez elengedhetetlen a dokumentumkezeléshez szükséges osztályok és metódusok eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 2. lépés: Állítsa be a dokumentumkönyvtárat

Adja meg annak a könyvtárnak az elérési útját, ahol a Word-dokumentum található, és ahová menteni szeretné a konvertált képet.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## 3. lépés: Töltse be a Word-dokumentumot

Töltse be Word dokumentumát egy`Aspose.Words.Document` objektum. Ez az objektum lehetővé teszi a dokumentum programozott kezelését.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 4. lépés: Állítsa be a képmentési beállításokat

 Ezután állítsa be a`ImageSaveOptions` annak meghatározásához, hogy a dokumentum hogyan kerüljön mentésre képként. Úgy konfiguráljuk, hogy PNG formátumban, 1 Bpp indexelt színmóddal mentse el.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Konvertálja csak az első oldalt
    ImageColorMode = ImageColorMode.BlackAndWhite, // Fekete-fehérre állítva
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Használjon 1 Bpp indexelt formátumot
};
```

- SaveFormat.Png: Megadja, hogy a kimeneti formátum PNG lesz.
- PageSet(1): Azt jelzi, hogy csak a dokumentum első oldala lesz konvertálva.
- ImageColorMode.BlackAndWhite: Biztosítja, hogy a kép fekete-fehér legyen.
- ImagePixelFormat.Format1bppIndexed: A pixelformátumot 1 Bpp indexeltre állítja, optimalizálva a helyet.

## 5. lépés: Mentse el a dokumentumot képként

 Végül használja a`Save` módszere a`Document` objektumot a konvertált kép mentéséhez.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Következtetés

Gratulálok! Sikeresen konvertált egy Word-dokumentumot 1 Bpp indexelt képpé az Aspose.Words for .NET használatával. Ez a módszer nemcsak hatékony, hanem segít a különböző alkalmazásokhoz megfelelő, nagy kontrasztú képek létrehozásában. Nyugodtan integrálhatja ezt a funkciót projektjeibe. Boldog kódolást!

## GYIK

### Mi az 1 Bpp indexelt kép?
Az 1 Bpp (1 Bit Per Pixel) indexelt kép egy fekete-fehér képformátum, amelyben minden képpont egyetlen bittel (0 vagy 1) jelenik meg. Ez a formátum rendkívül helytakarékos, így ideális archiválásra.

### Konvertálhatok egy Word-dokumentum több oldalát egyszerre?
 Igen! Egyszerűen módosítsa a`PageSet` ingatlan a`ImageSaveOptions` több oldalt tartalmazhat, vagy beállíthatja a teljes dokumentum konvertálására.

### Szükségem van licencre az Aspose.Words for .NET használatához?
 Igen, a teljes funkcionalitáshoz licenc szükséges. Megszerezheti a[ideiglenes engedély itt](https://purchase.aspose.com/temporary-license/).

### Milyen más képformátumokba konvertálhatom a Word dokumentumomat?
 Az Aspose.Words különféle formátumokat támogat, beleértve a JPEG-et, BMP-t és TIFF-et. Csak változtasd meg a`SaveFormat`a`ImageSaveOptions` a kívánt formátumra.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Az átfogó dokumentációért látogasson el a[Aspose.Words for .NET dokumentációs oldal](https://reference.aspose.com/words/net/).