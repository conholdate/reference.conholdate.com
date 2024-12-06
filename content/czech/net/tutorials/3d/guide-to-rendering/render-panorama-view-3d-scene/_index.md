---
title: Vykreslení panoramatického pohledu na 3D scénu pomocí Aspose.3D pro .NET
linktitle: Vykreslení panoramatického pohledu na 3D scénu
second_title: Aspose.3D .NET API
description: Naučte se, jak vykreslit úžasný panoramatický pohled na 3D scénu ve vašich aplikacích .NET pomocí Aspose.3D. Postupujte podle našeho podrobného průvodce pro pohlcující vykreslování scény.
type: docs
weight: 13
url: /cs/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Zavedení

Vytváření pohlcujících, panoramatických 3D scén je změnou hry pro vývojáře, kteří chtějí vylepšit své aplikace o úžasné vizuální efekty. Ať už pracujete na herním enginu, architektonické vizualizaci nebo pohlcující webové zážitky, vykreslování 3D scén jako panoramat umožňuje uživatelům zažít dynamický pohled ze všech úhlů. Aspose.3D for .NET je perfektní nástroj pro bezproblémovou integraci této funkce do vašich projektů .NET. Tento komplexní průvodce vás provede procesem vykreslení panoramatu z 3D scény pomocí Aspose.3D for .NET.

## Předpoklady

Než se ponoříte do procesu vykreslování, ujistěte se, že máte na místě následující:

- Aspose.3D for .NET: Chcete-li začít, musíte nainstalovat Aspose.3D, který poskytuje všechny potřebné nástroje pro manipulaci s 3D prostředky a vykreslování.[Stáhněte si Aspose.3D pro .NET](https://releases.aspose.com/3d/net/) začít.
- Vývojové prostředí .NET: Je vyžadováno plně nakonfigurované vývojové prostředí .NET. Ujistěte se, že máte Visual Studio nebo jakékoli jiné kompatibilní IDE.
-  Ukázkový soubor 3D scény: Můžete použít jakoukoli 3D scénu ve formátech jako např`.glb`, `.fbx` nebo`.obj`. Pro tento tutoriál použijeme jednoduchý soubor „VirtualCity.glb“.

Jakmile splníte tyto předpoklady, můžeme přejít k nastavení scény.

## Importujte potřebné jmenné prostory

Pro práci s Aspose.3D budeme muset do našeho projektu importovat několik jmenných prostorů. Tyto jmenné prostory vám umožňují efektivně manipulovat s 3D objekty, nastavením kamery a možnostmi vykreslování.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Tyto jmenné prostory jsou nezbytné pro načtení 3D scény, konfiguraci kamery, osvětlení a nastavení vykreslovacích textur, které tvoří panoramatický pohled.

## Krok 1: Načtěte 3D scénu do aplikace

 Prvním krokem je načtení 3D scény do vaší aplikace. Toho lze dosáhnout pomocí`Scene` třídy poskytuje Aspose.3D. Nahradit`"VirtualCity.glb"` s cestou k souboru 3D scény.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 The`Scene` objekt načte 3D scénu do paměti, což vám umožní s ní pracovat a aplikovat techniky vykreslování.

## Krok 2: Nastavte fotoaparát a světla

Abyste zajistili správné zachycení vaší 3D scény, budete muset nastavit kameru a vhodné osvětlení. Kamera umožňuje ovládat perspektivu scény, zatímco světla pomáhají osvětlovat objekty.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Nastavení kamery: Blízká a vzdálená rovina kamery je nastavena tak, aby definovala viditelný rozsah ve 3D scéně.
- Nastavení světla: Jsou přidána dvě světla – jedno bodové světlo a druhé se specifickou barvou pro přidání hloubky a realismu do scény.

## Krok 3: Nastavte vykreslovací modul a definujte cíle vykreslování

Nyní, když máte nastavenou scénu, kameru a světla, je dalším krokem vytvoření vykreslovacího modulu a definování cílů vykreslování. Vykreslovací modul je zodpovědný za generování 3D obrázků a cíle vykreslování definují, kam bude uložen konečný výstup.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Textura vykreslení krychle: Používá se k vykreslení mapy krychle pro panoramatický pohled. Zde definujeme texturu 512x512.
- Final Render Texture: Toto je textura, která bude držet finální ekvidaktulární panoramatický pohled.

## Krok 4: Konfigurace výřezu a vykreslení scény

Po vytvoření textur renderu musíme nakonfigurovat výřez, který definuje oblast 3D scény, kterou kamera zachytí.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Tento kód nastaví výřez pro mapu krychle a vykreslí scénu do`rt` vykreslení textury.

## Krok 5: Aplikujte post-processing pro Equirectangular Projection

tomto okamžiku musíme použít následné zpracování, abychom převedli mapu krychle do ekvidaktulárního panoramatického pohledu. Tato transformace zajistí, že výsledný snímek bude správné panorama.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Equirectangular Projection: Tento efekt následného zpracování vezme mapu krychle a přemění ji na ekvidaktouhlou panoramatickou projekci, která poskytuje plynulý 360stupňový pohled.

## Krok 6: Uložte vykreslené panorama

Po dokončení vykreslování a následného zpracování je posledním krokem uložení konečného panoramatu do souboru obrázku, jako je například PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Tím se panoramatický snímek uloží do určeného adresáře, což vám umožní integrovat jej do vaší aplikace nebo zobrazit na webové stránce.

## Závěr

Vykreslování panoramatických pohledů na 3D scény nebylo nikdy snazší s Aspose.3D pro .NET. Podle výše uvedených kroků můžete snadno načíst 3D scénu, nakonfigurovat kameru a světla, vykreslit scénu a použít efekty následného zpracování pro vytvoření pohlcujících panoramatických snímků. Aspose.3D for .NET poskytuje výkon a flexibilitu pro oživení vašich 3D vizualizací a jejich bezproblémovou integraci do vašich aplikací.

## FAQ

### Mohu pro vykreslování panoramat použít vlastní 3D scénu?
Absolutně. Jednoduše nahraďte cestu souboru ukázkové scény umístěním vaší vlastní 3D scény.

### Jsou k dispozici nějaké další efekty následného zpracování?
Ano, Aspose.3D nabízí řadu efektů následného zpracování, jako je hloubka ostrosti, květ a další, které lze použít pro vylepšení vašich vykreslených obrázků.

### Jak mohu optimalizovat výkon vykreslování?
Výkon vykreslování lze optimalizovat úpravou parametrů, jako je velikost textury vykreslování a rozlišení, a také vyladěním blízkých a vzdálených rovin kamery.

### Mohu to integrovat do webové aplikace?
Ano, Aspose.3D for .NET lze integrovat do vašich webových aplikací .NET a dynamicky vykreslovat 3D panoramata.

### Existuje komunitní fórum pro podporu Aspose.3D?
 Ano, můžete navštívit[Aspose.3D fórum](https://forum.aspose.com/c/3d/18) za podporu a komunitní diskuse.