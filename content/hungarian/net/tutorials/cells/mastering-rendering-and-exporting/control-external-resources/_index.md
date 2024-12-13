---
title: A külső erőforrások vezérlése az Aspose.Cells segítségével .NET-hez
linktitle: A külső erőforrások vezérlése az Aspose.Cells segítségével .NET-hez
second_title: Aspose.Cells .NET Excel Processing API
description: Az Aspose.Cells for .NET segítségével tárja fel az Excelből PDF-be konvertálásának teljes potenciálját. Ebből az átfogó útmutatóból megtudhatja, hogyan kezelheti a külső erőforrásokat, például a képeket, biztosítva, hogy a PDF-fájlok pontosan tükrözzék a formázási követelményeket.
type: docs
weight: 12
url: /hu/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Bevezetés

mai digitális környezetben az Excel-táblázatok PDF-dokumentummá konvertálása gyakori és elengedhetetlen feladat. Legyen szó jelentésekről, pénzügyi adatokról vagy prezentációs anyagokról, döntő fontosságú annak biztosítása, hogy a PDF-ek megfeleljenek a tervezett formátumnak. Az Aspose.Cells for .NET olyan hatékony könyvtárat biztosít, amely lehetővé teszi az átalakítási folyamat részletes vezérlését, különösen akkor, ha külső erőforrásokkal, például képekkel foglalkozik. Ebben az útmutatóban megvizsgáljuk, hogyan lehet hatékonyan kezelni a külső erőforrásokat az Aspose.Cells segítségével az Excelből PDF-be átalakítási folyamat során. Merüljünk el!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy készen áll a következőkre:

1. Visual Studio vagy bármely .NET-kompatibilis IDE: Ez lesz a fejlesztői környezet.
2.  Aspose.Cells for .NET: Ha még nem telepítette, keresse fel a[Aspose letöltések](https://releases.aspose.com/cells/net/) oldalt a legújabb verzió beszerzéséhez.
3. Alapszintű C# ismerete: A C# ismerete előnyt jelent. Ha bármilyen fogalmat tisztázni szeretne, bátran nézzen utána.
4. Minta Excel-fájl: Készítsen egy Excel-fájlt, például „samplePdfSaveOptions_StreamProvider.xlsx”, amely tartalmazza a konvertálni kívánt külső erőforrásokat.
5. Képfájl teszteléshez: Az átalakítás során külső forrásként használjon egy képfájlt, például a „newPdfSaveOptions_StreamProvider.png”-t.

## Importálja a szükséges csomagokat

A kezdéshez importálnia kell a szükséges névtereket az Aspose.Cells könyvtárból. Adja hozzá a következőket a C# fájl tetején található direktívák használatával:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Ezek a névterek biztosítják a feladatok alapvető osztályait és metódusait.

## 1. lépés: Hozzon létre egy Stream Provider osztályt

 Először hozzon létre egy adatfolyam-szolgáltató osztályt, amely megvalósítja a`IStreamProvider` felület. Ez az osztály lehetővé teszi a külső erőforrások betöltésének szabályozását.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Töltse be a képet egy memóriafolyamba
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Ez a metódus akkor hívódik meg, amikor az adatfolyam zárva van, és jelenleg hibakeresési üzenetet naplóz.
- InitStream: Ez a módszer a külső képfájlt bájttömbként olvassa be, memóriafolyammá alakítja, és hozzárendeli a`options.Stream` ingatlan.

## 2. lépés: Állítsa be a forrás- és kimeneti könyvtárakat

Ezután határozza meg az Excel-fájl és a kimeneti PDF könyvtárait.

```csharp
// Forrás könyvtár
string sourceDir = "Your Document Directory";
// Kimeneti könyvtár
string outputDir = "Your Document Directory";
```

 Cserélje ki`"Your Document Directory"` a rendszer tényleges elérési útjával, ahol a fájlok találhatók.

## 3. lépés: Töltse be az Excel fájlt

Most töltse be azt az Excel fájlt, amelyből a PDF-et szeretné létrehozni.

```csharp
// Töltse be a külső képeket tartalmazó Excel forrásfájlt
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 A`Workbook` Az Aspose.Cells osztály az Excel-fájlt képviseli, amely különféle külső forrásokat, például képeket tartalmazhat.

## 4. lépés: Állítsa be a PDF mentési beállításokat

A munkafüzet PDF formátumban történő mentése előtt adja meg a kívánt mentési beállításokat.

```csharp
// Adja meg a PDF mentési beállításokat – Stream Provider
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Mentse el az egyes lapot egy új oldalra
};
```

 Ezzel létrejön egy példány`PdfSaveOptions` , amely lehetővé teszi a PDF formátum testreszabását. A`OnePagePerSheet` opció biztosítja, hogy minden Excel munkalap külön oldalon jelenjen meg a végleges PDF-ben.

## 5. lépés: Jelölje ki az adatfolyam-szolgáltatót

 Csatlakoztassa a`Workbook` példa a`MyStreamProvider` korábban létrehozott osztályt.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Ez a vonal biztosítja, hogy amikor az átalakítás során külső erőforrásokkal találkozik, az egyéni szolgáltató megfelelően kezeli azokat.

## 6. lépés: Mentse el a munkafüzetet PDF formátumban

Most mentse az Excel-munkafüzetet PDF-ként.

```csharp
// Mentse el a munkafüzetet PDF-be
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Felhívva a`Save` metódussal a munkafüzet objektumon, és átadja a kimeneti könyvtárat a PDF-beállításokkal együtt, akkor az Excel-fájlt jól formázott PDF-fájllá konvertálja.

## 7. lépés: Erősítse meg a sikeres végrehajtást

Végül érdemes megerősíteni, hogy a folyamat sikeresen befejeződött.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Ez az üzenet tájékoztatja Önt a művelet állapotáról, és hasznos visszajelzést ad.

## Következtetés

Elsajátította a külső erőforrások vezérlésének folyamatát az Aspose.Cells segítségével az Excelből PDF-be konvertálva! Ezen lépések követésével biztosíthatja, hogy dokumentumai pontosan tartalmazzák a képeket és egyéb külső elemeket, ami minden alkalommal csiszolt végterméket eredményez.

## GYIK

### Mi az Aspose.Cells?
Az Aspose.Cells egy hatékony könyvtár .NET-fejlesztők számára, amely lehetővé teszi Excel-fájlok létrehozását, kezelését, konvertálását és megjelenítését különféle formátumokban.

### Hogyan tölthetem le az Aspose.Cells-t?
 A legújabb verziót letöltheti a[Letöltési link](https://releases.aspose.com/cells/net/).

### Kipróbálhatom az Aspose.Cells-t ingyen?
 Igen! Ingyenes próbaverzióhoz férhet hozzá, ha ellátogat a[Ingyenes próbaoldal](https://releases.aspose.com/).

### Hol találok támogatást az Aspose.Cells számára?
 A támogatással kapcsolatos kérdésekkel kapcsolatban keresse fel a[Aspose támogatási fórum](https://forum.aspose.com/c/cells/9).

### Hogyan szerezhetek ideiglenes licencet az Aspose.Cells számára?
 Ideiglenes jogosítványt igényelhet[itt](https://purchase.aspose.com/temporary-license/).
