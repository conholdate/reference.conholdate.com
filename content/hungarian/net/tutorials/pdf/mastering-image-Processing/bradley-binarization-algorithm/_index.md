---
title: Bradley binarizációs algoritmus
linktitle: Bradley binarizációs algoritmus
second_title: Aspose.PDF for .NET API Reference
description: Ismerje meg, hogyan alakíthat át PDF-oldalakat kiváló minőségű bináris TIFF-képekké az Aspose.PDF for .NET-ben található bradley-binarizációs algoritmus segítségével. Ez a lépésenkénti útmutató kódpéldát tartalmaz.
type: docs
weight: 30
url: /hu/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Bevezetés

Ebben az oktatóanyagban végigvezetjük a PDF-oldalak TIFF-képpé alakításán a Bradley binarizációs algoritmus segítségével. Az Aspose.PDF for .NET leegyszerűsíti ezt a feladatot, lehetővé téve a dokumentumok munkafolyamatainak egyszerű automatizálását és egyszerűsítését.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.PDF for .NET: Töltse le a könyvtárat innen[itt](https://releases.aspose.com/pdf/net/).
- Visual Studio (vagy bármely C# IDE).
- C# alapismeretek.
-  Érvényes jogosítvány vagy a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) Aspose-tól.

## 1. lépés: Állítsa be projektjét

Először hozzon létre egy új C# projektet az IDE-ben, és importálja a szükséges névtereket:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## 2. lépés: Határozza meg a dokumentumkönyvtárat

Adja meg annak a könyvtárnak az elérési útját, amelyben a PDF-dokumentum található, valamint a TIFF-képek kimeneti útvonalait:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // A PDF-fájl elérési útja
```

Ez a könyvtár tárolja a forrás PDF-fájlt és a konvertált TIFF-fájlokat is.

## 3. lépés: Töltse be a PDF-dokumentumot

Nyissa meg a konvertálni kívánt PDF dokumentumot:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Cserélje ki`PageToTIFF.pdf` a PDF-fájl nevével.

## 4. lépés: Adja meg a kimeneti útvonalakat

Határozza meg a generált TIFF-fájlok kimeneti útvonalait:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## 5. lépés: Állítsa be a képfelbontást

Állítsa be a TIFF-képek felbontását. A magasabb DPI jobb képminőséget eredményez:

```csharp
Resolution resolution = new Resolution(300);
```

## 6. lépés: Konfigurálja a TIFF-beállításokat

Konfigurálja a TIFF-kép beállításait, beleértve a tömörítést és a színmélységet:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Az 1 bpp (1 bit/pixel) használata előkészíti a képet a bináris kimenetre.

## 7. lépés: Hozza létre a TIFF-eszközt

Hozzon létre egy TIFF-eszközt, amely kezeli az átalakítást:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## 8. lépés: Alakítsa át a PDF oldalt TIFF formátumba

A PDF első oldalának konvertálása TIFF-képpé:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## 9. lépés: Alkalmazza a Bradley binarizációs algoritmust

Most alkalmazza a Bradley algoritmust a szürkeárnyalatos TIFF-kép bináris képpé alakításához:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 A`BinarizeBradley` metódus két fájlfolyamot (bemeneti és kimeneti) és egy küszöbértéket vesz igénybe. Az optimális eredmény elérése érdekében szükség szerint állítsa be a küszöböt.

## 10. lépés: Erősítse meg a sikeres átalakítást

Végül ellenőrizze, hogy az átalakítás sikeres volt:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Következtetés

Gratulálok! Sikeresen konvertált egy PDF-oldalt TIFF-képpé, és alkalmazta a Bradley binarizációs algoritmust az Aspose.PDF for .NET segítségével. Ez a folyamat elengedhetetlen a dokumentum-archiváláshoz, az OCR-hez és más professzionális alkalmazásokhoz. A kiváló minőségű felbontásnak és a hatékony tömörítésnek köszönhetően a dokumentum képei tiszták és kezelhető méretűek lesznek.

## GYIK

### Mi az a Bradley algoritmus?
A Bradley algoritmus egy binarizációs technika, amely a szürkeárnyalatos képeket bináris képekké alakítja úgy, hogy minden pixelhez adaptív küszöbértéket határoz meg a környezet alapján.

### Konvertálhatok több PDF oldalt TIFF formátumba ezzel a módszerrel?
 Igen, módosíthatja a`Process` metódus a dokumentum összes oldalának végigjátszásához a konvertáláshoz.

### Mi az optimális felbontás a PDF-fájlok TIFF formátumba konvertálásához?
A jó minőségű képekhez általában 300 DPI-s felbontás javasolt, de ezt saját igényei szerint módosíthatja.

### Mit jelent az 1bpp színmélységben?
Az 1bpp (1 bit/pixel) azt jelzi, hogy a kép fekete-fehér lesz, és minden képpont teljesen fekete vagy teljesen fehér.

### Alkalmas-e a Bradley algoritmus az OCR-hez?
Igen, a Bradley algoritmust gyakran használják az OCR előfeldolgozásban, mert növeli a beolvasott dokumentumok szövegének kontrasztját, javítva a felismerés pontosságát.