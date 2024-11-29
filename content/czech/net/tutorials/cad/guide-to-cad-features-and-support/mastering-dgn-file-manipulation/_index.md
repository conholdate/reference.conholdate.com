---
title: Zvládnutí manipulace se soubory DGN pomocí Aspose.CAD v .NET
linktitle: Zvládnutí manipulace se soubory DGN
second_title: Aspose.CAD .NET – formát souborů CAD a BIM
description: Naučte se načítat soubory DGN, iterovat jejich prvky, spravovat 2D i 3D entity a exportovat je jako rastrové obrázky – to vše při využití výkonných funkcí knihovny Aspose.CAD.
type: docs
weight: 18
url: /cs/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Zavedení

Jste vývojář .NET, který touží integrovat soubory DGN do svých aplikací? Aspose.CAD for .NET nabízí výkonnou knihovnu navrženou speciálně pro práci s formáty souborů DGN. V tomto tutoriálu prozkoumáme, jak efektivně zacházet se soubory DGN, včetně podporovaných prvků, a jak s nimi manipulovat ve vašich projektech .NET.

## Předpoklady

Než začnete, ujistěte se, že máte následující nastavení:

- Základní znalost programování .NET: Výhodou bude znalost C# nebo VB.NET.
- Visual Studio: Nainstalované na vašem počítači pro vývoj projektu.
-  Knihovna Aspose.CAD for .NET: Stáhněte si ji z[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Krok 1: Importujte potřebné jmenné prostory

Chcete-li využít funkce Aspose.CAD, začněte importováním požadovaných jmenných prostorů do vašeho projektu.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Krok 2: Načtěte soubor DGN

 Začněte načtením existujícího souboru DGN do vaší aplikace. To se provádí vytvořením instance a`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Zde pokračujte ve své logice
}
```

## Krok 3: Iterujte prvky DGN

Jakmile je soubor DGN načten, můžete iterovat jeho prvky. Aspose.CAD poskytuje různé typy prvků DGN pro vaši manipulaci.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Zpracujte každý prvek
}
```

## Krok 4: Zacházení s 2D a 3D entitami

Můžete rozlišovat mezi 2D a 3D prvky DGN. Níže uvádíme, jak s nimi efektivně zacházet:

### Ovládejte 2D entity

Dříve podporované 2D entity můžete spravovat pomocí bloku přepínačů.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Zde přidejte svou logiku zpracování
        break;
}
```

### Ovládejte 3D entity

Podobně zacházejte s 3D entitami následovně:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Zde přidejte svou logiku zpracování
        break;
}
```

## Krok 5: Exportujte soubor DGN

Po manipulaci s prvky DGN můžete exportovat soubor jako rastrový obrázek. To lze snadno provést pomocí Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Definujte svou výstupní cestu
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Závěr

V tomto tutoriálu jsme se naučili, jak používat Aspose.CAD pro .NET k efektivní správě souborů DGN. Podle nastíněných kroků můžete bez námahy pracovat s 2D i 3D prvky DGN a exportovat je jako rastrové obrázky. Tato výkonná knihovna umožňuje bezproblémovou integraci zpracování DGN do vašich aplikací .NET a rozšiřuje možnosti vašeho projektu.

## FAQ

### Kde najdu dokumentaci k Aspose.CAD pro .NET?

 K dispozici je obsáhlá dokumentace[zde](https://reference.aspose.com/cad/net/).

### Jak si stáhnu Aspose.CAD pro .NET?

 Můžete si stáhnout nejnovější verzi knihovny[zde](https://releases.aspose.com/cad/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.CAD pro .NET?

 Ano, je k dispozici bezplatná zkušební verze[zde](https://releases.aspose.com/).

### Jak mohu získat dočasné licence pro Aspose.CAD pro .NET?

 Můžete požádat o dočasné licence[zde](https://purchase.conholdate.com/temporary-license/).

### Potřebujete pomoc nebo máte otázky?

Pro podporu nebo pro dotazy navštivte komunitu Aspose.CAD[fórum podpory](https://forum.aspose.com/c/cad/19).