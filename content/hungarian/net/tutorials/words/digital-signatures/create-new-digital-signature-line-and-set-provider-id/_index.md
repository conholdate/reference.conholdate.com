---
title: Új digitális aláírási vonal létrehozása és szolgáltatói azonosító beállítása
linktitle: Új digitális aláírási vonal létrehozása és szolgáltatói azonosító beállítása
second_title: Aspose.Words Document Processing API
description: Fedezze fel, hogyan adhat programozottan aláírási sorokat Word-dokumentumaihoz az Aspose.Words for .NET használatával. Ez az átfogó útmutató mindent lefed, a fejlesztői környezet beállításától az aláírási sorok beszúrásáig és a dokumentumok biztonságos aláírásáig.
type: docs
weight: 10
url: /hu/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Bevezetés

Sziasztok a technika szerelmesei! Szerette volna valaha is automatizálni az aláírási sorok beillesztését Word-dokumentumaiba? Ma az Aspose.Words for .NET használatával valósítható meg. Ez a lépésenkénti útmutató végigvezeti Önt egy aláírási sor létrehozásán és a szolgáltatói azonosító beállításán, így a dokumentumfeldolgozási feladatai hatékonyabbá és egyszerűbbé válnak.

## Előfeltételek

Mielőtt belevágnánk, győződjön meg arról, hogy mindent beállított:

1.  Aspose.Words for .NET: Ha még nem telepítette, töltse le[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Használja a Visual Studio vagy bármely C# fejlesztői beállítást.
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépére.
4. PFX-tanúsítvány: A dokumentumok aláírásához PFX-tanúsítványra lesz szüksége, amelyet egy megbízható tanúsító hatóságtól szerezhet be.

## A szükséges névterek importálása

A kezdéshez importálja a szükséges névtereket a C# projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Most pedig nézzük meg az új aláírási sor létrehozásának és a szolgáltatói azonosító beállításának részleteit.

## 1. lépés: Hozzon létre egy új dokumentumot

Először is létre kell hoznunk egy új Word-dokumentumot, amely vászonként szolgál az aláírási sorunkhoz:

```csharp
// Adja meg a dokumentumkönyvtár elérési útját.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt inicializálunk egy újat`Document` és a`DocumentBuilder`, amely lehetővé teszi az elemek egyszerű hozzáadását.

## 2. lépés: Adja meg az aláírási sor beállításait

Ezután meghatározzuk az aláírási sor beállításait, beleértve az aláíró nevét, beosztását, e-mail-címét és egyéb releváns adatokat:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Ezek a lehetőségek segítenek személyre szabni az aláírási vonalat, egyértelművé és professzionálissá téve azt.

## 3. lépés: Illessze be az aláírási sort

Ha készen állnak a lehetőségek, beilleszthetjük az aláírási sort a dokumentumba:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 A`InsertSignatureLine`metódus hozzáadja az aláírási sort, és egyedi szolgáltatói azonosítót rendelünk hozzá.

## 4. lépés: Mentse el a dokumentumot

Az aláírási sor beszúrása után mentsük el a dokumentumot:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Ezzel elmenti a dokumentumot az újonnan hozzáadott aláírási sorral.

## 5. lépés: Az aláírási beállítások beállítása

Most konfiguráljuk az aláírási beállításokat, beleértve az aláírási sor azonosítóját, a szolgáltató azonosítóját, a megjegyzéseket és az aláírási időt:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Ezek a beállítások biztosítják, hogy a dokumentumot a megfelelő adatokkal írják alá.

## 6. lépés: Hozzon létre tanúsítványtulajdonost

A dokumentum aláírásához létre kell hoznunk egy tanúsítvány tulajdonost a PFX tanúsítvánnyal:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Cserélje ki`"morzal.pfx"` a tényleges tanúsítványfájl nevével és`"aw"` a tanúsítvány jelszavával.

## 7. lépés: Aláírja a dokumentumot

Végül aláírjuk a dokumentumot a digitális aláírás segédprogrammal:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Ez a folyamat aláírja a dokumentumot, és új fájlként menti.

## Következtetés

Gratulálok! Sikeresen létrehozott egy aláírási sort, és beállította a szolgáltatói azonosítót egy Word-dokumentumban az Aspose.Words for .NET használatával. Ez a hatékony könyvtár leegyszerűsíti a dokumentumfeldolgozási feladatokat, és hatékonyabbá teszi a munkafolyamatot. Próbálja ki, és nézze meg, hogyan javíthatja projektjeit!

## GYIK

### Testreszabhatom az aláírássor megjelenését?
 Teljesen! Különféle beállításokat állíthat be a`SignatureLineOptions` hogy megfeleljen az Ön stílusának és követelményeinek.

### Mi a teendő, ha nincs PFX tanúsítványom?
Be kell szereznie egyet egy megbízható tanúsító hatóságtól, mivel ez elengedhetetlen a dokumentumok digitális aláírásához.

### Hozzáadhatok több aláírási sort egy dokumentumhoz?
Igen, több aláírási sort is hozzáadhat a beillesztési folyamat különböző opciókkal történő megismétlésével.

### Az Aspose.Words for .NET kompatibilis a .NET Core-al?
Igen, az Aspose.Words for .NET támogatja a .NET Core-t, így sokoldalúan használható különféle fejlesztői környezetekben.

### Mennyire biztonságosak a digitális aláírások?
Az Aspose.Words segítségével létrehozott digitális aláírások rendkívül biztonságosak, feltéve, hogy érvényes és megbízható tanúsítványt használ.