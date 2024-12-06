---
title: Új aláírási sor létrehozása és aláírása
linktitle: Új aláírási sor létrehozása és aláírása
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat zökkenőmentesen digitális aláírást Word-dokumentumaihoz az Aspose.Words for .NET használatával. Ez az átfogó oktatóanyag mindent lefed, a környezet beállításától az aláírási sor beszúrásán át az aláírt dokumentumok mentéséig és ellenőrzéséig.
type: docs
weight: 10
url: /hu/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Bevezetés

Digitális aláírást szeretne hozzáadni egy Word dokumentumhoz? Az Aspose.Words for .NET segítségével egyszerűbb, mint gondolnád! Ez az oktatóanyag végigvezeti Önt a környezet beállításának, az aláírási sor hozzáadásának és a dokumentum digitális aláírásának lépésein. Kezdjük is!

## Előfeltételek

Mielőtt belemerülne a kódba, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  Aspose.Words for .NET -[Töltse le itt](https://releases.aspose.com/words/net/).
2. A .NET fejlesztői környezet – a Visual Studio ideális erre a feladatra.
3. Aláírandó dokumentum – Létrehozhat új Word-dokumentumot, vagy használhat egy meglévőt.
4.  Tanúsítványfájl - A`.pfx` fájl szükséges a digitális aláíráshoz.
5. Aláírási vonal képe (opcionális) – Az aláíráshoz csatolhat egy képfájlt.

## Importálja a szükséges névtereket

Az Aspose.Words funkcióinak használatához importálnia kell a következő névtereket:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 1. lépés: A dokumentumkönyvtár beállítása

Kezdje a dokumentumkönyvtár elérési útjának meghatározásával. Itt mentheti és kérheti le a dokumentumokat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Adja meg a dokumentumkönyvtár elérési útját
```

## 2. lépés: Új dokumentum létrehozása

Ezután hozzunk létre egy új Word-dokumentumot. Ez a dokumentum vászonként szolgál az aláírási sorhoz.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Az aláírási sor beszúrása

 Most használja a`DocumentBuilder` osztály aláírási sor beillesztéséhez a dokumentumba:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 4. lépés: A dokumentum mentése

Miután beszúrta az aláírási sort, mentse a dokumentumot. Ez egy döntő lépés az aláírás előtt.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 5. lépés: Az aláírási beállítások konfigurálása

Állítsa be az aláírási folyamat beállításait. Ez magában foglalja az aláírási sor azonosítójának és az aláírással együtt megjelenítendő opcionális kép megadását.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Út a képedhez
};
```

## 6. lépés: A tanúsítvány betöltése

Töltse be a dokumentum aláírásához szükséges tanúsítványfájlt:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Állítsa be a fájl nevét és jelszavát
```

## 7. lépés: A dokumentum aláírása

 Végül írja alá a dokumentumot a`DigitalSignatureUtil` osztály. Mentse el az aláírt dokumentumot új névvel későbbi használatra.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Következtetés

Gratulálok! Sikeresen létrehozott egy Word-dokumentumot, hozzáadott egy aláírási sort, és digitálisan aláírta az Aspose.Words for .NET segítségével. Ez a hatékony eszköz leegyszerűsíti a dokumentumok automatizálását, és biztosítja a szerződések és hivatalos dokumentumok biztonságos aláírását és hitelesítését.

## GYIK

### Használhatok más képformátumokat az aláírási sorhoz?

Igen, különféle képformátumokat használhat, beleértve a PNG-t, JPG-t és BMP-t.

###  Szükséges-e használni a`.pfx` file for the certificate?

 Igen, a`.pfx` fájl egy szabványos formátum a tanúsítványok és a digitális aláírásokhoz szükséges magánkulcsok tárolására.

### Hozzáadhatok több aláírási sort egyetlen dokumentumhoz?

Teljesen! A beszúrási lépés szükség szerinti megismétlésével több aláírási sort is beszúrhat.

### Mi a teendő, ha nincs digitális tanúsítványom?

Be kell szereznie egy digitális tanúsítványt egy megbízható tanúsító hatóságtól, vagy létre kell hoznia egyet olyan eszközökkel, mint az OpenSSL.

### Hogyan ellenőrizhetem a digitális aláírást a dokumentumban?

A digitális aláírás ellenőrzéséhez nyissa meg az aláírt dokumentumot a Wordben, és ellenőrizze az aláírás részleteit, hogy megerősítse annak hitelességét és integritását.