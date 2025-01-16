---
title: Egyedi információk sorrendje MHTML-ben az Aspose.Email-lel
linktitle: Egyedi információk sorrendje MHTML-ben az Aspose.Email-lel
second_title: Aspose.Email .NET Email Processing API
description: Ebben a lépésenkénti oktatóanyagban megtudhatja, hogyan határozhat meg egyéni információsorrendet MHTML-ben az Aspose.Email for .NET használatával.
type: docs
weight: 14
url: /hu/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## Bevezetés

gazdag e-mail formátumok létrehozása nagyban javíthatja a kommunikációt, különösen akkor, ha az e-maileket különböző fájlformátumokba, például MHTML-be exportálja. Az Aspose.Email for .NET hatékony eszközkészletet biztosít a fejlesztőknek az e-mailek kezeléséhez, amely magában foglalja az adatok megjelenítési sorrendjének meghatározását az MHTML-be exportáláskor. Ebben az útmutatóban lebontjuk az ehhez szükséges lépéseket, így könnyen nyomon követhető, akár tapasztalt fejlesztő, akár csak most kezdő. Szóval, vágjunk is bele!

## Előfeltételek

Mielőtt belemerülne az információk egyéni sorrendjének meghatározásába az MHTML-ben, van néhány előfeltétel, amelyet meg kell vizsgálnia a listán:

1. .NET fejlesztői környezet: Győződjön meg arról, hogy be van állítva egy .NET fejlesztői környezet. Használhatja a Visual Studio-t, a Visual Studio Code-ot vagy bármely más kompatibilis IDE-t.

2.  Aspose.Email Library: telepítenie kell az Aspose.Email for .NET könyvtárat. A legújabb verziót letöltheti a[Az Aspose kiadási oldala](https://releases.aspose.com/email/net/).

3. C# alapvető ismerete: A C# programozás ismerete segít a kód jobb megértésében.

4.  Minta e-mail fájl: Szüksége lesz egy mintára`.eml` fájl (pl.`Attachments.eml`) tesztelési célból.

Ha megvannak ezek az előfeltételek, készen állsz az oktatóanyag követésére!

## Csomagok importálása

A kód használatának megkezdéséhez importálnia kell a szükséges névtereket az Aspose.Email könyvtárból. Ez elengedhetetlen az e-mail fájlok kezeléséhez szükséges összes osztály és módszer eléréséhez.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

Helyezze ezeket a C# fájl tetejére. Most már készen állsz a kódolásba!

Most, hogy mindent beállított, bontsuk fel az oktatóanyagot kezelhető lépésekre.

## 1. lépés: Állítsa be az adattárat

Az első dolog, hogy hozzon létre egy könyvtárat, ahol az e-mail fájljait tárolni fogja. Ez lehet bármilyen elérési út a helyi gépen.

```csharp
string dataDir = "Your Data Directory";
```

 Cserélje ki`"Your Data Directory"` a tényleges útvonallal, ahol az Ön`.eml` fájl található. Például, ha a fájl be van`C:\Emails`, ezt írnád:

```csharp
string dataDir = @"C:\Emails\";
```

## 2. lépés: Töltse be az e-mail üzenetet

Ezután be kell töltenie a`.eml` fájlba a`MailMessage` objektum. Ez lehetővé teszi az e-mail tartalmának és metaadatainak kezelését.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

Győződjön meg arról, hogy a fájlnév megegyezik a megadott könyvtárban található fájlnévvel. Ha a fájl neve más, frissítse a fájlnevet ennek megfelelően.

## 3. lépés: Állítsa be az MHTML mentési opciókat

Amikor az e-mail betöltődött, itt az ideje meghatározni, hogyan szeretné MHTML-ként menteni. Kezdheti az alapértelmezett beállításokkal.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

Ez a sor inicializálja az MHTML mentési beállításait, megadva a terepet a fejlécek későbbi testreszabásához.

## 4. lépés: Mentse el az MHTML-t alapértelmezett sorrendben

Mentsük az e-mailt MHTML-ként az alapértelmezett sorrendben. Ez megadja az alapvonalat, amellyel összehasonlíthatja a testreszabás után.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

 Futtassa ezt a sort, és ellenőrizze a megadott könyvtárat. Most egy új MHTML fájlnak kell megjelennie`CustomOrderOfInformationInMHTML_1.mhtml`. Nyissa meg, hogy megnézze, hogyan jelennek meg az információk alapértelmezés szerint.

## 5. lépés: A fejlécek sorrendjének testreszabása

Most jön a szórakoztató rész! Megadhatja, hogy mely fejlécek szerepeljenek az MHTML kimenetben, és milyen sorrendben. Kezdjük néhány általános fejléccel.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

A fejlécek hozzáadásával elmondja az Aspose-nak, hogyan szeretné megjeleníteni az e-mailt.

## 6. lépés: MHTML mentése egyéni sorrendben

A fejlécek testreszabása után ismét el kell mentenie az e-mailt MHTML formátumban, hogy megnézze, hogyan befolyásolja az új rendelés a kimenetet.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

 Futtassa ezt a kódot, majd nyissa meg`CustomOrderOfInformationInMHTML_2.mhtml`. Hasonlítsa össze az elsővel, hogy megtudja, hogyan változott az információ a fejlécsorrend alapján.

## 7. lépés: Törölje és adjon hozzá új fejlécsorrendet

Mi van, ha teljesen más sorrendet szeretne? Újra kezdheti a meglévő fejlécbeállítások törlésével.

```csharp
opt.RenderingHeaders.Clear();
```

Itt az ideje a fejlécek új sorrendjének meghatározására. Például, ha prioritást szeretne adni a mellékleteknek, és másolni szeretné a címzetteket:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## 8. lépés: Mentse el az MHTML-t új egyéni sorrenddel

Végül utoljára mentse el az e-mailt az új fejlécbeállításokkal.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

 A sor futtatása után nyissa meg`CustomOrderOfInformationInMHTML_3.mhtml`és ellenőrizze, hogyan jeleníti meg az információkat az új testreszabása alapján.

## Következtetés

És itt van – egy egyszerű útmutató az információk egyéni sorrendjének meghatározásához MHTML-ben az Aspose.Email for .NET használatával. Ezeket a lépéseket követve szabályozhatja, hogy e-mailjei hogyan jelenjenek meg MHTML formátumban, így biztosítva, hogy a legfontosabb információk az Ön igényeinek megfelelő módon jelenjenek meg. 

## GYIK

### Mi az az MHTML?
Az MHTML a „MIME HTML” rövidítése, amely egy weboldal archív formátuma, amely egyesíti a HTML-t és más forrásokat, például képeket.

### Használhatom ingyenesen az Aspose.Email-t?
 Igen, az Aspose ingyenes próbaverziót biztosít a fejlesztők számára. Megtalálhatod[itt](https://releases.aspose.com/).

### Mi a teendő, ha problémákat tapasztalok az Aspose.Email használatával?
 Támogatást kaphat a közösségtől a[Aspose fórum](https://forum.aspose.com/c/email/12/).

### Elérhető ideiglenes licenc az Aspose.Email számára?
 Igen, kérhet ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).

### Hol vásárolhatok Aspose.Email-t?
 A könyvtárat itt tudod megvásárolni[link](https://purchase.aspose.com/buy).