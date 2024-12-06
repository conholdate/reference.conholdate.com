---
title: Vytvářejte primitivní 3D modelování
linktitle: Vytvářejte primitivní 3D modelování
second_title: Aspose.3D .NET API
description: Naučte se vytvářet a přizpůsobovat primitivní 3D modely, včetně krabic a válců, a bez námahy je ukládat ve formátu FBX.
type: docs
weight: 10
url: /cs/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Zavedení

Vítejte v pohlcujícím světě 3D modelování pomocí Aspose.3D pro .NET! V tomto obsáhlém tutoriálu vás krok za krokem provedeme procesem vytváření primitivních 3D modelů. Ať už jste zkušený vývojář nebo začátečník, který se chce učit, tato příručka vám umožní vytvářet vizuálně úžasné 3D prvky pro vaše projekty.

## Předpoklady

Než se ponoříte do 3D modelování, ujistěte se, že máte splněny následující předpoklady:

-  Aspose.3D for .NET: Stáhněte si a nainstalujte knihovnu Aspose.3D for .NET z[stránka ke stažení](https://releases.aspose.com/3d/net/).
  
- Vývojové prostředí .NET: Nastavte prostředí kompatibilní s Aspose.3D, jako je Visual Studio.

Když je vše připraveno, vydejme se na naše dobrodružství 3D modelování!

## Import požadovaných jmenných prostorů

Začněte importem potřebných jmenných prostorů pro přístup k funkcím Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Tyto jmenné prostory vám poskytnou nástroje nezbytné pro manipulaci s 3D modely a ukládání vašich výtvorů.

## Krok 1: Inicializujte objekt scény

Vytvořte nový objekt scény, který funguje jako plátno pro vaše 3D modely:

```csharp
// Inicializujte objekt Scene
Scene scene = new Scene();
```

Tato scéna bude obsahovat primitivní tvary, které se chystáte vytvořit.

## Krok 2: Vytvořte krabicový model

Dále do vaší scény přidáme model krabice:

```csharp
// Vytvořte model krabice
scene.RootNode.CreateChildNode("box", new Box());
```

Rozměry a vlastnosti krabice si můžete přizpůsobit tak, aby vyhovovala vaší kreativní vizi.

## Krok 3: Vytvořte model válce

Nyní vylepšete svou scénu přidáním válce:

```csharp
// Vytvořte model válce
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Stejně jako u krabice si můžete upravit parametry válce tak, abyste dosáhli požadovaného vzhledu.

## Krok 4: Uložte scénu ve formátu FBX

Chcete-li zachovat svůj 3D model, uložte jej ve formátu FBX:

```csharp
// Uložte výkres ve formátu FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Ujistěte se, že jste zvolili vhodný výstupní adresář a název souboru pro váš model.

## Krok 5: Zobrazte zprávu o úspěchu

Nakonec oslavte svůj úspěch zobrazením zprávy:

```csharp
// Zobrazit zprávu o úspěchu
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Vaše 3D scéna složená z primitivních modelů je nyní kompletní a uložená!

## Závěr

 Gratulujeme k vytvoření úžasných 3D modelů pomocí Aspose.3D for .NET! Tento tutoriál pokryl základy primitivního modelování, ale možnosti jsou nekonečné. Prozkoumejte více o pokročilých funkcích a technikách v[dokumentace](https://reference.aspose.com/3d/net/).

## FAQ

### Mohu používat Aspose.3D pro .NET s jinými programovacími jazyky než .NET?

Aspose.3D podporuje hlavně .NET, ale jsou dostupné verze pro Javu a další platformy.

### Je k dispozici bezplatná zkušební verze?

 Ano, můžete vyzkoušet možnosti Aspose.3D pomocí a[zkušební verze zdarma](https://releases.aspose.com/).

### Kde najdu podporu pro Aspose.3D pro .NET?

Pro podporu komunity navštivte[Aspose.3D fórum](https://forum.aspose.com/c/3d/18).

### Jak mohu získat dočasnou licenci?

 Můžete požádat o dočasnou licenci[zde](https://purchase.conholdate.com/temporary-license/).

### Jsou k dispozici další výukové programy?

 Ano! Prozkoumejte další návody a příklady v[dokumentace](https://reference.aspose.com/3d/net/).