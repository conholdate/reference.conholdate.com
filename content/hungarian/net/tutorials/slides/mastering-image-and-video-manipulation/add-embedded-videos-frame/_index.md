---
title: Adjon hozzá beágyazott videókeretet a .NET-bemutatókhoz
linktitle: Adjon hozzá beágyazott videókeretet a .NET-bemutatókhoz
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Használja ki prezentációiban rejlő lehetőségeket, ha megtanulja, hogyan ágyazhat be videókat az Aspose.Slides for .NET segítségével. Ez az átfogó oktatóanyag lépésről lépésre végigvezeti a multimédiás elemek integrálásának folyamatán.
type: docs
weight: 19
url: /hu/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## Bevezetés

A mai rohanó prezentációs környezetben a multimédiás elemek integrálása jelentősen növelheti az elköteleződést és a közönségmegtartást. Az Aspose.Slides for .NET robusztus megoldást kínál videokockák diákjaiba való beágyazására. Ez az oktatóanyag lépésről lépésre végigvezeti a folyamaton, biztosítva a zökkenőmentes élményt az elejétől a végéig.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Slides for .NET Library: Töltse le és telepítse a könyvtárat a[kiadási oldal](https://releases.aspose.com/slides/net/).
- Médiatartalom: Videófájl (pl. "Wildlife.mp4"), amelyet be szeretne ágyazni a prezentációjába.

## Importálja a szükséges névtereket

Kezdje a szükséges névterek importálásával a .NET-projektben:

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## 1. lépés: Állítsa be a címtárakat

Győződjön meg arról, hogy projektje tartalmazza a dokumentum- és médiafájlokhoz szükséges könyvtárakat:

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// Hozzon létre könyvtárat, ha nem létezik
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## 2. lépés: Példányosítsa a bemutató osztályt

 Hozzon létre egy példányt a`Presentation` osztály a PPTX fájl megjelenítéséhez:

```csharp
using (Presentation pres = new Presentation())
{
    // Szerezd meg az első diát
    ISlide sld = pres.Slides[0];
```

## 3. lépés: A videó beágyazása

Illessze be a videót a prezentációjába a következő kóddal:

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## 4. lépés: Videókeret hozzáadása

Ezután adjon hozzá egy videokockát a diához:

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## 5. lépés: Állítsa be a videó tulajdonságait

Állítsa be a videó tulajdonságait, beleértve a lejátszási módot és a hangerőt:

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // A videó automatikus lejátszása
vf.Volume = AudioVolumeMode.Loud; // Állítsa be a hangerőt
```

## 6. lépés: Mentse el prezentációját

Végül mentse a módosított PPTX fájlt lemezre:

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

Ezeket a lépéseket megismételheti minden olyan videónál, amelyet be szeretne ágyazni a bemutatójába.

## Következtetés

Gratulálok! Sikeresen beágyazott egy videokeretet a prezentációjába az Aspose.Slides for .NET segítségével. Ezzel a dinamikus funkcióval a prezentációit a következő szintre emelheti, és zökkenőmentesen integrált multimédiával ragadhatja meg közönségét.

## GYIK

### Beágyazhatok videókat a prezentáció bármely diájába?

 Igen, bármelyik diát kiválaszthatja az index beállításával`pres.Slides[index]`.

### Mely videóformátumok támogatottak?

Az Aspose.Slides különféle videoformátumokat támogat, beleértve az MP4-et, az AVI-t és a WMV-t.

### Testreszabhatom a videókockák méretét és helyzetét?

 Teljesen! Módosíthatja a paramétereket`AddVideoFrame(x, y, width, height, video)` hogy megfeleljen az Ön igényeinek.

### Van korlátozás a beágyazható videók számának?

A beágyazott videók korlátja általában a prezentációs szoftver kapacitásától függ.

### Hol kérhetek további segítséget, vagy megoszthatom tapasztalataimat?

 Nyugodtan látogassa meg a[Aspose.Slides fórum](https://forum.aspose.com/c/slides/11) közösségi támogatásra és beszélgetésekre.