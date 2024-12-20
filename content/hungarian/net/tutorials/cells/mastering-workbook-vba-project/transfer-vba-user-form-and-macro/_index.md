---
title: VBA felhasználói űrlapok és makrók átvitele Excel-munkafüzetek között
linktitle: VBA felhasználói űrlapok és makrók átvitele Excel-munkafüzetek között
second_title: Aspose.Cells .NET Excel Processing API
description: A VBA-felhasználói űrlapok és makrók munkafüzetek közötti Aspose.Cells for .NET segítségével történő átviteléről szóló átfogó útmutató segítségével felszabadíthatja az Excel automatizálásának erejét. Kezdőknek és tapasztalt fejlesztőknek egyaránt tökéletes.
type: docs
weight: 11
url: /hu/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Bevezetés

Üdvözöljük a végső útmutatóban az Excel-élmény fokozásához VBA-makrók és felhasználói űrlapok használatával! Ebben az oktatóanyagban megvizsgáljuk, hogyan vihetünk át egy VBA Macro UserForm Designert egyik munkafüzetből a másikba a hatékony Aspose.Cells for .NET könyvtár használatával. Akár tapasztalt fejlesztő, akár csak most kezdő, ez a lépésről lépésre mutató útmutató felvértezi az Excel-fájlok programozott kezeléséhez szükséges ismeretekkel. Készen állsz a merülésre? Kezdjük is!

## Előfeltételek
Mielőtt belevágnánk a kódolásba, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van:

1. C# fejlesztői környezet: Munkakörnyezet C# fejlesztéshez, a Visual Studio erősen ajánlott.
2.  Aspose.Cells for .NET Library: Győződjön meg róla, hogy az Aspose.Cells könyvtárat integrálja a projektbe. Könnyen lehet[töltse le itt](https://releases.aspose.com/cells/net/).
3. VBA- és Excel-makrók alapismeretei: Ismerje meg a VBA-t és azt, hogy az Excel-makrók miként segítik jobban megérteni ezt az oktatóanyagot.
4. Excel-fájl felhasználói űrlappal: Hozzon létre vagy szerezzen be egy felhasználói űrlapot tartalmazó Excel-munkafüzetet (lehetőleg engedélyezve a makrókat, pl.`.xlsm` fájlok).

## A szükséges csomagok importálása
Az Aspose.Cells által biztosított funkciók használatához adja meg a következő névtereket a C# fájl tetején:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Ezek a névterek hozzáférést biztosítanak az Aspose.Cells könyvtárba ágyazott hatékony eszközökhöz.

## 1. lépés: Határozza meg a forrás- és kimeneti könyvtárait
Először határozza meg a fájlok helyét:

```csharp
// Határozza meg a forrás- és kimeneti könyvtárat
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Cserélje ki a helyőrző elérési útvonalakat a tényleges könyvtárakra, ahol a fájlokat tárolja.

## 2. lépés: Hozzon létre egy üres célmunkafüzetet
Ezután hozzon létre egy új munkafüzetet, amelybe másolja a felhasználói űrlapot és a makrókat:

```csharp
// Hozzon létre egy üres célmunkafüzetet
Workbook target = new Workbook();
```

Ez inicializál egy üres munkafüzetet, amely vászonként szolgál a közelgő adatátvitelhez.

## 3. lépés: Töltse be a sablon munkafüzetet
Töltse be a felhasználói űrlapot és a makrókat tartalmazó munkafüzetet:

```csharp
// Töltse be a VBA-Macro Designer felhasználói űrlapot tartalmazó Excel-fájlt
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Állítsa be`"sampleDesignerForm.xlsm"` a tényleges fájl nevére.

## 4. lépés: Másolja a munkalapokat a célmunkafüzetbe
Most másoljuk át a munkalapokat a sablonból a célmunkafüzetbe:

```csharp
// Másolja az összes sablonmunkalapot a célmunkafüzetbe
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Adjon hozzá egy üzenetet a célmunkalap A2 cellájába
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Ez a kód végigfut a sablon minden munkalapján, és átmásolja a célmunkafüzetbe, biztosítva az összes adat zökkenőmentes átvitelét.

## 5. lépés: Másolja ki a VBA-makrókat a sablonból
Ezután átmásoljuk a VBA makrókat, beleértve a UserForm Designer modulokat is, az új munkafüzetbe:

```csharp
// Másolja a VBA-Macro Designer felhasználói űrlapot a sablonból a célba
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Másolja ki ezt a munkafüzet modul kódját
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Másolja a többi modul kódját és adatait
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Szerezze be a felhasználói űrlap tervezői tárhelyét
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Adja hozzá a tervezői tárolót a cél Vba-projekthez
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Ez a kód biztosítja, hogy ne csak a kódot, hanem a felhasználói űrlapot is átmásolják, megőrizve a makrók funkcionalitását.

## 6. lépés: Mentse el a cél munkafüzetet
másolási folyamat befejezése után mentse el az új munkafüzetet:

```csharp
// Mentse el a célmunkafüzetet
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Módosítsa a kimeneti fájl nevét szükség szerint. Ez a lépés létrehozza a testreszabott munkafüzetet, amely tele van makróval és felhasználói űrlapokkal.

## 7. lépés: Erősítse meg a sikert
Végül nyomtasson egy sikerüzenetet a konzolra:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Ez az egyszerű vonal megnyugtatja Önt, hogy a folyamat zökkenőmentesen ment – ez a kemény munkája elengedhetetlen megerősítése!

## Következtetés
Gratulálok! Sikeresen megtanulta, hogyan másolhat át VBA makró felhasználói űrlaptervezőt egyik munkafüzetből a másikba az Aspose.Cells for .NET segítségével. Bár elsőre ijesztőnek tűnhet, a gyakorlás járatossá tesz a munkafüzet-manipulációkban. Ne feledje, a kódolás a kísérletezésről szól, ezért ne habozzon felfedezni az Excel-fájlok különböző funkcióit. Ha bármilyen kérdése van, vagy segítségre van szüksége, az Aspose fórumai és dokumentációja kiváló támogatási források.

## GYIK

### Az Excel mely verzióit támogatja az Aspose.Cells?
Az Aspose.Cells különféle Excel-formátumokat támogat, beleértve az XLSX-et, XLSM-et, CSV-t és még sok mást.

### Használhatom ingyenesen az Aspose.Cells-t?
 Igen! Kezdheti egy ingyenes próbaverzióval a könyvtár értékeléséhez:[Ingyenes próbaverzió](https://releases.aspose.com/).

### Kell-e a Visual Studio a kód futtatásához?
Míg a Visual Studio a felhasználóbarát szolgáltatásai miatt ajánlott, minden .NET fejlesztést támogató C# IDE elegendő.

### Hol találok további példákat és dokumentációt?
 Feltárhatod a[Aspose.Cells Documentation](https://reference.aspose.com/cells/net/) további példákért és mélyreható magyarázatokért.

### Hogyan oldhatom meg a problémákat az Aspose.Cells használata közben?
 Meg kell látogatnia a[Aspose támogatási fórum](https://forum.aspose.com/c/cells/9) segítségért a közösségtől és az Aspose támogató személyzetétől.