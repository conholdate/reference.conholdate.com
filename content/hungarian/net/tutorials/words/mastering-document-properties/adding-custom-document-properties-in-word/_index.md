---
title: Egyéni dokumentumtulajdonságok hozzáadása a Wordben
linktitle: Egyéni dokumentumtulajdonságok hozzáadása a Wordben
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan javíthatja Word-dokumentumait egyéni dokumentumtulajdonságokkal az Aspose.Words for .NET használatával. Ez az átfogó útmutató végigvezeti Önt a folyamaton.
type: docs
weight: 10
url: /hu/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Bevezetés

Üdvözöljük! Ha az Aspose.Words for .NET-et fedezi fel, és szeretné megtanulni, hogyan adhat egyéni dokumentumtulajdonságokat Word-fájljaihoz, akkor jó helyen jár. Az egyéni tulajdonságok felbecsülhetetlen értékűek további metaadatok tárolására, amelyeket a beépített tulajdonságok nem fednek le. Függetlenül attól, hogy nyomon kell követnie a dokumentumok engedélyezését, a revíziószámokat vagy bizonyos dátumokat, az egyéni tulajdonságok segíthetnek. Ebben az oktatóanyagban végigvezetjük a tulajdonságok zökkenőmentes hozzáadásának lépésein az Aspose.Words for .NET használatával. Kezdjük is!

## Előfeltételek

Mielőtt belemerülne a kódba, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  Aspose.Words for .NET Library: Töltse le[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: IDE, például a Visual Studio.
3. Alapvető C# ismerete: Hasznos lesz a C# és a .NET ismerete.
4.  Mintadokumentum: Készítsen elnevezésű Word-dokumentum mintát`Properties.docx` módosításra.

## Névterek importálása

Az Aspose.Words funkcióinak eléréséhez importálnia kell a szükséges névtereket a kód elejére:

```csharp
using System;
using Aspose.Words;
```

## 1. lépés: A dokumentum elérési útjának beállítása

 Ezután határozzuk meg a Word-dokumentum elérési útját. Ez a lépés elengedhetetlen az Ön helyének megtalálásához és kinyitásához`Properties.docx` fájlt.

```csharp
// Adja meg a dokumentumkönyvtár elérési útját.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Ügyeljen arra, hogy cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentum tényleges elérési útjával.

## 2. lépés: Az egyéni dokumentum tulajdonságainak elérése

Most pedig érjük el a Word-dokumentum egyéni dokumentumtulajdonságait, ahol az egyéni metaadatok lesznek.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Ez a sor hozzáférést biztosít az egyéni tulajdonságok gyűjteményéhez, amelyekkel dolgozni fog.

## 3. lépés: Meglévő tulajdonságok ellenőrzése

Új tulajdonságok hozzáadása előtt célszerű ellenőrizni, hogy létezik-e már egy tulajdonság, hogy elkerülje a párhuzamosságot.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Ez a kód ellenőrzi, hogy létezik-e már az „Authorized” tulajdonság. Ha ez megtörténik, a módszer korán kilép, megelőzve a duplikációkat.

## 4. lépés: Logikai tulajdonság hozzáadása

Adjunk hozzá egy egyéni logikai tulajdonságot, amely jelzi, hogy a dokumentum engedélyezett-e.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Ez a sor hozzáad egy "Authorized" nevű tulajdonságot, és beállítja az értékét`true`.

## 5. lépés: Karakterlánc tulajdonság hozzáadása

Ezután egy karakterlánc tulajdonság hozzáadásával meghatározzuk, hogy ki engedélyezte a dokumentumot.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Nyugodtan cserélje le a "John Smith" kifejezést tetszőleges névre.

## 6. lépés: Dátum tulajdonság hozzáadása

A dokumentum engedélyezésének nyomon követéséhez adjunk hozzá egy dátum tulajdonságot.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Ez a sor hozzáad egy "Engedélyezett dátum" nevű tulajdonságot, és a mai dátumhoz rendeli hozzá`DateTime.Today`.

## 7. lépés: Revíziószám hozzáadása

A verzióvezérléshez hozzáadhatunk egy tulajdonságot a dokumentum revíziószámának nyomon követéséhez.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Itt hozzáadunk egy "Engedélyezett revízió" tulajdonságot, amely tartalmazza a dokumentum aktuális verziószámát.

## 8. lépés: Numerikus tulajdonság hozzáadása

Végül adjunk hozzá egy numerikus tulajdonságot egy engedélyezett összeg, például egy költségvetési szám tárolásához.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Ez a sor hozzáad egy "Engedélyezett összeg" nevű tulajdonságot a következő értékkel`123.45`. Ezt a számot szükség szerint módosíthatja.

## Következtetés

Gratulálok! Sikeresen hozzáadott egyéni dokumentumtulajdonságokat egy Word-dokumentumhoz az Aspose.Words for .NET használatával. Ezek a tulajdonságok hatékony módszert jelentenek az Ön igényeihez szabott metaadatok tárolására, legyen szó a jogosultsági adatok nyomon követéséről, a verziószámokról vagy bizonyos összegekről.

## GYIK

### Mik azok az egyéni dokumentumtulajdonságok?
Az egyéni dokumentumtulajdonságok olyan metaadatok, amelyeket hozzáadhat egy Word-dokumentumhoz, hogy további információkat tároljon, amelyekre nem vonatkoznak a beépített tulajdonságok.

### Hozzáadhatok karakterláncokon és számokon kívül más tulajdonságokat is?
Igen, különféle típusú tulajdonságokat adhat hozzá, beleértve a logikai értékeket, dátumokat és akár egyéni objektumokat is.

### Hogyan érhetem el ezeket a tulajdonságokat egy Word dokumentumban?
Az egyéni tulajdonságokat programozottan érheti el az Aspose.Words használatával, vagy közvetlenül megtekintheti őket a Wordben a dokumentum tulajdonságain keresztül.

### Lehetséges egyéni tulajdonságok szerkesztése vagy törlése?
Teljesen! Az Aspose.Words által biztosított módszerekkel egyszerűen szerkesztheti vagy törölheti az egyéni tulajdonságokat.

### Használhatók egyéni tulajdonságok dokumentumok szűrésére?
Igen! Az egyéni tulajdonságok kiválóan alkalmasak dokumentumok meghatározott metaadatok alapján történő kategorizálására és szűrésére.