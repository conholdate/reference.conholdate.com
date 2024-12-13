---
title: DGN konvertálása PDF-be az Aspose.CAD for .NET-ben
linktitle: DGN konvertálása PDF-be az Aspose.CAD for .NET-ben
second_title: Aspose.CAD .NET - CAD és BIM fájlformátum
description: Tanulja meg, hogyan konvertálhat könnyedén DGN fájlokat PDF formátumba a hatékony Aspose.CAD .NET könyvtár segítségével. Ez a lépésenkénti útmutató minden szintű fejlesztő számára készült.
type: docs
weight: 12
url: /hu/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Bevezetés

A CAD-fájlok világában való eligazodás kihívást jelenthet, de az Aspose.CAD for .NET segítségével a fejlesztők könnyen kezelhetik és konvertálhatják a különböző CAD-formátumokat. Az egyik gyakori igény a DGN-fájlok PDF-formátumba konvertálása, amelyet ebben az oktatóanyagban lépésről lépésre vizsgálunk meg.

## Előfeltételek

A követéshez győződjön meg arról, hogy rendelkezik az alábbiakkal:

- C# és .NET keretrendszer alapfokú ismerete.
-  Aspose.CAD for .NET könyvtár telepítve. Letöltheti[itt](https://releases.aspose.com/cad/net/).
- Egy minta DGN-fájl (pl. Nikon_D90_Camera.dgn). 

## 1. lépés: Importálja a szükséges névtereket

Kezdje a megfelelő névterek importálásával a C# projektben:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 2. lépés: Töltse be a DGN fájlt

Adja meg a DGN-fájl könyvtárát, és töltse be a következő kóddal:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // A további feldolgozás ide kerül...
}
```

## 3. lépés: Konfigurálja a raszterezési beállításokat

Ezután állítsa be a raszterezési beállításokat annak meghatározásához, hogy a DGN hogyan jelenjen meg a PDF-ben:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Szükség szerint állítsa be a szélességet
    PageHeight = 300, // Szükség szerint állítsa be a magasságot
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## 4. lépés: PDF-beállítások létrehozása

Határozza meg a PDF beállításokat, integrálva a korábban konfigurált raszterezési beállításokat:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 5. lépés: Mentse el a DGN-t PDF-ként

Végül mentse a DGN-fájlt PDF-ként a megadott beállításokkal:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Következtetés

Gratulálok! Sikeresen konvertált egy DGN-fájlt PDF-be az Aspose.CAD for .NET segítségével. Ez az egyszerű oktatóanyag végigvezette Önt a DGN-fájl betöltésében, a raszterezési beállítások megadásában és a kimenet PDF-formátumban történő mentésében.

## GYIK

### Szükségem van előzetes CAD ismeretekre az Aspose.CAD használatához?  
Teljesen! Az Aspose.CAD célja az összetett CAD-feladatok egyszerűsítése, így minden fejlesztő számára elérhetővé válik, függetlenül a CAD-ismeretétől.

### Hol találok további forrásokat és dokumentációt az Aspose.CAD-hez?  
 Átfogó útmutatókat és példákat fedezhet fel a[Aspose.CAD dokumentáció](https://reference.aspose.com/cad/net/).

### Létezik ingyenes próbaverzió az Aspose.CAD számára?  
 Igen, ingyenes próbaverzió elérhető[itt](https://releases.aspose.com/).

### Hogyan szerezhetek ideiglenes licencet az Aspose.CAD-hez?  
 Ideiglenes licenceket kérhet[itt](https://purchase.conholdate.com/temporary-license/).

### Segítségre van szüksége vagy kérdése van?  
 Csatlakozzon a beszélgetéshez a[Aspose.CAD fórum](https://forum.aspose.com/c/cad/19) közösségi támogatásért és megkeresésekért.