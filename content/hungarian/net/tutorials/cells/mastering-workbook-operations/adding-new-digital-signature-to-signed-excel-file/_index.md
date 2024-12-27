---
title: Új digitális aláírás hozzáadása aláírt Excel-fájlhoz
linktitle: Új digitális aláírás hozzáadása aláírt Excel-fájlhoz
second_title: Aspose.Cells .NET Excel Processing API
description: Ismerje meg, hogyan adhat hozzá új digitális aláírást egy meglévő aláírt Excel-fájlhoz az Aspose.Cells for .NET használatával. Ez az átfogó útmutató lefedi az összes előfeltételt, lépésenkénti utasításokat és kódpéldákat.
type: docs
weight: 12
url: /hu/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Bevezetés

A mai digitális környezetben a dokumentumok hitelességének és sértetlenségének biztosítása fontosabb, mint valaha. A digitális aláírások megbízható módot biztosítanak annak ellenőrzésére, hogy a dokumentumot nem módosították, és hogy az legitim forrásból származik-e. Ha Excel-fájlokkal dolgozik .NET-ben, és új digitális aláírást kell hozzáadnia egy már aláírt fájlhoz, ez az útmutató az Ön számára készült! Az Aspose.Cells for .NET segítségével végigvezetjük a digitális aláírás hozzáadásának folyamatát egy meglévő aláírt Excel-fájlhoz.

## Előfeltételek

Mielőtt belemerülnénk a megvalósításba, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Cells for .NET: Töltse le és telepítse az Aspose.Cells programot a[kiadási oldal](https://releases.aspose.com/cells/net/).
2. .NET-keretrendszer: Győződjön meg arról, hogy a gépén be van állítva a .NET-keretrendszer, és ismeri az alapvető .NET-programozási fogalmakat.
3. Digitális tanúsítvány: Szerezzen be egy érvényes digitális tanúsítványt .pfx formátumban. Tesztelés céljából létrehozhat egy önaláírt tanúsítványt.
4. Fejlesztési környezet: Használjon IDE-t, például a Visual Studio-t a C# kód írásához és végrehajtásához.
5. Minta Excel-fájl: rendelkezzen egy meglévő Excel-fájllal, amely már digitálisan alá van írva, és ez lesz az új aláírás hozzáadásának célpontja.

Ha megvannak ezek az előfeltételek, ugorjunk bele a kódba!

## Importálja a szükséges csomagokat

A C# fájl tetején adja meg a következő névtereket a szükséges osztályok és metódusok eléréséhez:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 1. lépés: Határozza meg könyvtárait

Adja meg a forrásfájlok könyvtárait és a kimeneti fájl mentési helyét:

```csharp
// Forrás könyvtár
string sourceDir = "Your Document Directory"; // Cserélje le a tényleges könyvtárával
// Kimeneti könyvtár
string outputDir = "Your Document Directory"; // Cserélje le a tényleges könyvtárával
```

## 2. lépés: Töltse be a meglévő aláírt munkafüzetet

Töltse be a már aláírt Excel-munkafüzetet:

```csharp
// Töltse be a már digitálisan aláírt munkafüzetet
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## 3. lépés: Hozzon létre egy digitális aláírásgyűjteményt

Hozzon létre egy gyűjteményt a digitális aláírások kezeléséhez:

```csharp
//Hozza létre a digitális aláírásgyűjteményt
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## 4. lépés: Töltse be a tanúsítványt

Töltse be digitális tanúsítványát, amelyet az új aláírás létrehozásához fog használni:

```csharp
// Tanúsítványfájl és jelszava
string certFileName = sourceDir + "AsposeDemo.pfx"; // Az Ön tanúsítványfájlja
string password = "aspose"; // A tanúsítvány jelszava

// Hozzon létre új tanúsítványt
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## 5. lépés: Hozzon létre egy új digitális aláírást

Most hozzon létre egy új digitális aláírást, és adja hozzá a gyűjteményéhez:

```csharp
// Hozzon létre új digitális aláírást, és adja hozzá a gyűjteményhez
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## 6. lépés: Adja hozzá az aláírásgyűjteményt a munkafüzethez

Adja hozzá a digitális aláírásgyűjteményt a munkafüzethez:

```csharp
// Digitális aláírásgyűjtemény hozzáadása a munkafüzethez
workbook.AddDigitalSignature(dsCollection);
```

## 7. lépés: Mentse el a munkafüzetet

Mentse el a munkafüzetet az új digitális aláírással:

```csharp
// Mentse el a munkafüzetet
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## 8. lépés: Erősítse meg a sikert

Visszajelzés a sikeres végrehajtásról:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Következtetés

Gratulálok! Sikeresen hozzáadott egy új digitális aláírást egy már aláírt Excel-fájlhoz az Aspose.Cells for .NET segítségével. Ez a folyamat növeli a dokumentumok biztonságát, valamint biztosítja azok hitelességét és integritását.

## GYIK

### Mi az a digitális aláírás?

A digitális aláírás egy matematikai séma, amely ellenőrzi a digitális üzenetek vagy dokumentumok hitelességét és sértetlenségét, biztosítva, hogy azokat nem módosították, és megerősíti az aláíró személyazonosságát.

### Szükségem van speciális tanúsítványra a digitális aláírás létrehozásához?

Igen, egy megbízható tanúsító hatóság (CA) által kiadott digitális tanúsítvány szükséges az érvényes digitális aláírás létrehozásához.

### Használhatok önaláírt tanúsítványt a teszteléshez?

Teljesen! Fejlesztési és tesztelési célokra használhat önaláírt tanúsítványt, de a termeléshez célszerű egy megbízható CA-tól származó tanúsítványt használni.

### Mi történik, ha megpróbálok aláírást adni egy nem aláírt dokumentumhoz?

Ha olyan dokumentumhoz próbál digitális aláírást hozzáadni, amely még nincs aláírva, az probléma nélkül fog működni, de az eredeti aláírás nem lesz jelen.

### Hol találhatok több információt az Aspose.Cells-ről?

 Részletes útmutatókért és API-referenciákért tekintse meg a[Aspose.Cells dokumentáció](https://reference.aspose.com/cells/net/).