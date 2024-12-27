---
title: E-mail mellékletek kibontása C#-ban - Aspose.Email bemutató
linktitle: E-mail mellékletek kibontása C#-ban - Aspose.Email bemutató
second_title: Aspose.Email .NET Email Processing API
description: Ismerje meg, hogyan bonthat ki e-mail mellékleteket C# nyelven az Aspose.Email for .NET segítségével. Lépésről lépésre, példákkal PDF-ekhez, képekhez és egyebekhez.
type: docs
weight: 14
url: /hu/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## Bevezetés

Előfordult már, hogy egyenként manuálisan tölti le az e-mail mellékleteket? Ez nem csak időigényes, hanem hajlamos a hibákra is. Szerencsére az Aspose.Email for .NET hatékony és hatékony módszert kínál a feladat automatizálására. Függetlenül attól, hogy PDF-ekkel, képekkel vagy bármilyen más fájltípussal foglalkozik, a C# használatával könnyedén kibonthatja a mellékleteket.

Ebben az útmutatóban végigvezetjük Önt egy teljes oktatóanyagon, az előfeltételektől a teljesen működő példáig. Készen áll arra, hogy órákat takarítson meg a kézi munkával? Merüljünk el!

## Előfeltételek

A kódolás megkezdése előtt győződjön meg arról, hogy rendelkezik a következőkkel:

- A Visual Studio telepítve van a gépedre.
-  Aspose.Email a .NET könyvtárhoz. Megteheti[töltse le itt](https://releases.aspose.com/email/net/) vagy telepítse a NuGet-en keresztül.
- Érvényes e-mail fiók (IMAP/POP3 támogatott).
- A C# programozás alapvető ismerete.

 Ha még nem ismeri az Aspose.Email-t, fontolja meg a[ingyenes próbaverzió](https://releases.aspose.com/) vagy a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) a teljes funkciók feloldásához.

## Csomagok importálása

Mielőtt belemerülne a kódba, győződjön meg arról, hogy importálta a szükséges névtereket. Adja hozzá a következőket a C# fájl tetejéhez:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

Bontsuk fel a folyamatot emészthető lépésekre. Gondosan kövesse az egyes lépéseket a zökkenőmentes végrehajtás érdekében.


## 1. lépés: Állítsa be az IMAP-klienst

Az első lépés az e-mail szerverhez való csatlakozás az IMAP protokoll használatával. Az IMAP lehetővé teszi számunkra, hogy elérjük és lekérjük az e-mail üzeneteket a szerverről.

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  Cserélje ki`imap.example.com` az e-mail szolgáltató IMAP-szerver címével (pl.`imap.gmail.com` Gmailhez).
-  Használja a valódi e-mail címét`username` és`password`.
- `SelectFolder(ImapFolderInfo.InBox)`megadja, hogy a beérkező levelekkel szeretnénk dolgozni.


## 2. lépés: Töltse le az e-maileket a Beérkezett üzenetek mappából

A csatlakozás után le kell töltenie az e-maileket a beérkező levelek mappából. Az Aspose.Email egyszerű módszert kínál az összes üzenet felsorolására.

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` lekéri a beérkező levelek összes e-mailjének metaadatait.
-  A`ImapMessageInfoCollection` Az objektum olyan részleteket tartalmaz, mint a feladó, a tárgy és az egyedi azonosítók.


## 3. lépés: Minden e-mail üzenet lekérése

A tartalom és a mellékletek eléréséhez minden egyes e-mailt le kell töltenie a saját egyedi azonosítójával.


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

-  A`foreach` ciklus ismétlődik az összes üzeneten.
- `FetchMessage()` lekéri a tényleges e-mail tartalmat egy adott üzenetazonosítóhoz.


## 4. lépés: Hurok a mellékleteken keresztül

 Most, hogy megvan az e-mail tartalma, ideje kibontani a mellékleteket. Minden`MailMessage` az objektum mellékletek gyűjteményét tartalmazza.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

-  A`Attachments` tulajdonság felsorolja az összes mellékletet az e-mailben.
-  Használat`attachment.Name` hogy megkapja a fájl nevét.


## 5. lépés: Mentse el a mellékleteket a lemezre

Végül mentse a mellékleteket a helyi gépre. A fájlokat típus, méret vagy egyéb kritériumok szerint szűrheti.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  Cserélje ki`"C:\\Attachments"` kívánt mappa elérési útjával.
-  A`attachment.Save()` metódus a fájlt lemezre írja.


## 6. lépés: A mellékletek feldolgozása típus szerint

Ha a mellékleteket típusuktól függően eltérően kell kezelnie (pl. PDF vagy JPEG), az Aspose.Email ezt megkönnyíti.

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` azonosítja a fájl típusát (pl.`application/pdf` PDF-ekhez,`image/jpeg` képekhez).
- Adjon hozzá egyéni logikát a különböző fájltípusokhoz, ha szükséges.


## Következtetés

És megvan! A mellékletek kinyerése az e-mailekből már nem unalmas feladat. Az Aspose.Email for .NET segítségével néhány sornyi kóddal automatizálhatja ezt a folyamatot. Az IMAP-kliens beállításától a mellékletek helyi mentéséig ez az útmutató mindent tartalmaz, amire szüksége van az induláshoz. 

 Szóval minek várni?[Töltse le az Aspose.Emailt](https://releases.aspose.com/email/net/) és kezdje el e-mail munkafolyamatainak egyszerűsítését még ma!


## GYIK

### Használhatom ezt a kódot a Gmaillel vagy az Outlookkal?
 Igen! Cserélje ki`imap.example.com` a Gmail-lel (`imap.gmail.com`) vagy az Outlook (`outlook.office365.com`) IMAP-szerver címe.

### Ingyenesen használható az Aspose.Email?
 Az Aspose.Email licencet igényel a teljes szolgáltatáshoz. Kérheti a[ingyenes próbaverzió](https://releases.aspose.com/) vagy a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

### Hogyan kezelhetem a jelszavas biztonságot?
Fontolja meg a környezeti változók vagy a biztonságos hitelesítő adatok tárolását a merev kódolású jelszavak helyett.

### Kivonhatok mellékleteket az elküldött tételekből?
 Igen, egyszerűen használd`SelectFolder(ImapFolderInfo.Sent)` a beérkező levelek helyett.

### Az Aspose.Email támogatja a POP3-at?
Teljesen! Az IMAP mellett a POP3 és az SMTP protokollt is támogatja.