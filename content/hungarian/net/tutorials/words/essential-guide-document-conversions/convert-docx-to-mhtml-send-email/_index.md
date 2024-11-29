---
title: A DOCX konvertálása MHTML formátumba, és e-mail küldése Aspose.Words for .NET használatával
linktitle: A DOCX konvertálása MHTML formátumba, és e-mail küldése Aspose.Words for .NET használatával
second_title: Aspose.Words Document Processing API
description: Ez az átfogó útmutató lépésről lépésre ismerteti a DOCX-dokumentumok MHTML-formátumba konvertálását és e-mailben történő elküldését a .NET-ben található Aspose.Words és Aspose.Email könyvtárak használatával.
type: docs
weight: 10
url: /hu/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Bevezetés

A mai digitális környezetben a dokumentumok formátumok közötti konvertálása és e-mailben történő elküldése gyakori feladat. Ez az útmutató végigvezeti Önt a DOCX-fájlok MHTML formátumba konvertálásán és e-mailben történő elküldésén a hatékony Aspose.Words és Aspose.Email könyvtárak segítségével a .NET-hez. Minden lépést egyértelműen lebontunk, így biztosítva, hogy könnyedén követhesse. Kezdjük is!

## Előfeltételek

Mielőtt belevágna a folyamatba, győződjön meg arról, hogy a következőket beállította:

1.  Aspose.Words for .NET: Töltse le és telepítse a könyvtárat a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Töltse le és telepítse ezt a könyvtárat a[Az Aspose kiadási oldala](https://releases.aspose.com/email/net/).
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépére.
4. SMTP-szerver: E-mailek küldéséhez hozzá kell férnie egy SMTP-kiszolgálóhoz.

## A szükséges névterek importálása

Az Aspose.Words és az Aspose.Email használatához a projektben importálnia kell a szükséges névtereket. Adja hozzá a következőket a C# fájl tetején található direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## 1. lépés: Töltse be a DOCX-dokumentumot

 Kezdje a konvertálni kívánt DOCX dokumentum betöltésével. Használja a`Document` osztály Aspose-tól.Szók ennek megvalósításához.

```csharp
// Adja meg a dokumentumkönyvtár elérési útját.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 2. lépés: Mentse el a dokumentumot MHTML-ként

 Ezután konvertálja a betöltött dokumentumot MHTML formátumba. Ez a`Save` módszere a`Document` osztály.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Állítsa vissza az adatfolyam pozícióját az elejére olvasáshoz.
    stream.Position = 0;
}
```

## 3. lépés: Hozzon létre egy e-mail üzenetet

Most hozzon létre egy e-mail üzenetet az MHTML-folyamból az Aspose.Email segítségével. Használni fogja a`MailMessage` osztályt erre a célra.

```csharp
// Töltse be az MHTML adatfolyamot egy Aspose.Email MIME e-mail üzenetbe.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 4. lépés: Küldje el az e-mailt

 Végül küldje el az e-mailt egy SMTP-kliens segítségével. Konfigurálja az SMTP klienst a szerver adataival, és használja a`Send` az üzenet elküldésének módja.

```csharp
// Konfigurálja és küldje el az üzenetet az Aspose.Email használatával.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Következtetés

Gratulálok! Sikeresen konvertált egy DOCX-dokumentumot MHTML-re, és elküldte e-mailben az Aspose.Words és az Aspose.Email for .NET használatával. Ez a folyamat magában foglalja a dokumentum betöltését, MHTML formátumba konvertálását, e-mail üzenet létrehozását és SMTP-kliensen keresztüli elküldését. Ezekkel a lépésekkel zökkenőmentesen automatizálhatja a dokumentumok konvertálását és e-mailben történő elküldését alkalmazásaiban.

## GYIK

### Használhatom ezt a módszert más dokumentumformátumok konvertálására?
Teljesen! Az Aspose.Words a formátumok széles skáláját támogatja, lehetővé téve a DOC, DOCX, RTF és egyebek MHTML formátumba való konvertálását.

### Hogyan adhatok mellékleteket az e-mailhez?
 Könnyen hozzáadhat mellékleteket a`Attachments` tulajdona a`MailMessage` osztály.

### Az Aspose.Words kompatibilis a .NET Core-al?
Igen, az Aspose.Words kompatibilis a .NET Core-al, így alkalmas a .NET Core alkalmazásokban való használatra.

### Szükségem van licencre az Aspose.Words és az Aspose.Email használatához?
 Igen, mindkét könyvtárhoz engedély szükséges. Ideiglenes engedélyt értékelési célból szerezhet be a[Aspose vásárlási oldal](https://purchase.conholdate.com/temporary-license/).

### Hol találok további dokumentációt?
 A részletes dokumentációt az Aspose.Words oldalon találja[itt](https://reference.aspose.com/words/net/) és Aspose.Email[itt](https://reference.aspose.com/email/net/).