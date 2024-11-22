---
title: OneNote-dokumentumok mentése PDF formátumban az Aspose.Note for .NET használatával
linktitle: OneNote-dokumentumok mentése PDF formátumban
second_title: Aspose.Note .NET API
description: Ismerje meg, hogyan mentheti hatékonyan a Microsoft OneNote dokumentumokat PDF-fájlként az Aspose.Note for .NET segítségével. Ez az útmutató végigvezeti a szükséges előfeltételeken, és hasznos GYIK-et kínál.
type: docs
weight: 26
url: /hu/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Bevezetés

Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet dokumentumokat PDF formátumba menteni az Aspose.Note for .NET segítségével. Az Aspose.Note egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan dolgozzanak Microsoft OneNote fájlokkal. Leírjuk az előfeltételeket, importálunk névtereket, és lépésről lépésre útmutatást adunk a dokumentumok PDF formátumba mentéséhez különböző oldalelrendezésekben.

## Előfeltételek
1. Visual Studio: Győződjön meg arról, hogy telepítve van.
2. Aspose.Note for .NET: Töltse le és telepítse a könyvtárat.
3. C# ismeretek: A nyelv alapszintű ismerete szükséges.

## A szükséges névterek importálása
A folytatás előtt importálja a következő névtereket a kódjába:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## 1. lépés: Mentse PDF-be a Letter Page Settings segítségével
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Frissítse ezt az útvonalat
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Betölti a OneNote-dokumentumot, és PDF formátumban menti a Letter méretű oldalbeállításokkal.

## 2. lépés: Mentés PDF-be A4-es oldalbeállításokkal (nincs magasságkorlátozás)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Frissítse ezt az útvonalat
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Hasonló az 1. lépéshez, de A4-es oldalbeállításokat használ magassági korlátozások nélkül.

## Következtetés
Az oktatóanyag sikeresen bemutatja, hogyan konvertálhat OneNote fájlokat PDF formátumba az Aspose.Note segítségével. A különböző oldalbeállítások használatával a fejlesztők rugalmasságot szerezhetnek a dokumentumkezelésben.

## GYIK
### Az Aspose.Note képes kezelni az összetett OneNote-fájlokat?
Igen, hatékonyan kezeli az összetett OneNote-fájlok különféle funkcióit.

### Az Aspose.Note alkalmas kereskedelmi projektekhez?
Igen, a licenc megvásárlása után használhatja kereskedelmi célokra.

### Az Aspose.Note ingyenes próbaverziót kínál?
Igen, ingyenes próbaverzió áll rendelkezésre a felfedezéshez.

### Hol találom az Aspose.Note dokumentációját?
A részletes dokumentáció az Aspose referenciaoldalán érhető el.

### További segítségre van szüksége?
Kérdéseivel és támogatásával kapcsolatban keresse fel az Aspose.Note fórumot.
