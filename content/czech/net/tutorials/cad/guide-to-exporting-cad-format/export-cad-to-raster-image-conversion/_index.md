---
title: Export CAD na konverzi rastrových obrázků pomocí Aspose.CAD pro .NET
linktitle: Export CAD na konverzi rastrových obrázků
second_title: Aspose.CAD .NET – formát souborů CAD a BIM
description: Naučte se, jak efektivně převádět rozvržení CAD do různých formátů rastrových obrázků pomocí Aspose.CAD for .NET. Tento komplexní průvodce vás provede procesem pomocí jasného kódu.
type: docs
weight: 10
url: /cs/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Zavedení

Chcete snadno převést rozvržení CAD do formátů rastrových obrázků pomocí Aspose.CAD pro .NET? Tento podrobný průvodce je navržen tak, aby vám pomohl s navigací v procesu, doplněný stručnými úryvky kódu pro bezproblémový provoz. Ať už jste zkušený vývojář nebo teprve začínáte, tento tutoriál poskytuje cenné informace pro všechny úrovně dovedností.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

- Aspose.CAD for .NET Library: Stáhněte a nainstalujte knihovnu z[Web Aspose.CAD](https://releases.aspose.com/cad/net/).
-  Výkresový soubor CAD: Mějte svůj výkresový soubor CAD (např.`conic_pyramid.dxf`) připravené k převodu.

## Importujte požadované jmenné prostory

Ve svém projektu .NET budete muset importovat potřebné jmenné prostory, abyste mohli využívat funkce Aspose.CAD. Na začátek kódu přidejte následující:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Krok 1: Načtěte výkres CAD

Nejprve určete adresář a načtěte svůj CAD soubor do instance Image:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// Načtěte výkres CAD
using (var image = Image.Load(sourceFilePath))
{
    // Pokračujte dalšími kroky
}
```

## Krok 2: Vytvořte možnosti rastrování

Dále nastavte možnosti rastrování a definujte požadované rozměry pro výstupní obrázek:

```csharp
// Inicializujte CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Krok 3: Zadejte vrstvy pro převod

Pokud chcete převést konkrétní vrstvy, přidejte je do možností rastrování:

```csharp
// Určete vrstvu, kterou chcete převést
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Krok 4: Nastavte možnosti exportu JPEG

Nyní vytvořte možnosti pro formát obrázku, do kterého chcete exportovat (v tomto případě JPEG):

```csharp
// Vytvořte JpegOptions pro export
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Krok 5: Export do formátu JPEG

Nakonec uložte převedený obrázek:

```csharp
// Definujte cestu k výstupnímu souboru a uložte obrázek
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Další funkce: Převést všechny vrstvy

Chcete-li převést všechny vrstvy ve výkresu CAD, můžete implementovat metodu, jako je tato:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Iterujte vrstvy a každou uložte jako samostatný soubor JPEG
    // Zde je váš implementační kód
}
```

## Závěr

Gratuluji! Naučili jste se, jak efektivně převádět rozvržení CAD do formátů rastrových obrázků pomocí Aspose.CAD for .NET. Tato příručka nabízí přímý přístup vhodný pro vývojáře, kteří usilují o efektivní převody CAD.

## FAQ

### Mohu exportovat do různých formátů obrázků?

 Absolutně! Jednoduše vyměnit`JpegOptions` s dalšími možnostmi formátu, jako např`PngOptions` nebo`BmpOptions`, v závislosti na vašich potřebách.

### Je k dispozici zkušební verze?

 Ano, můžete si stáhnout zkušební verzi a prozkoumat funkce podle tohoto postupu[odkaz](https://releases.aspose.com/cad/net/).

### Kde najdu podporu pro Aspose.CAD?

 Pro podporu komunity se podívejte na Aspose.CAD[forum](https://forum.aspose.com/c/cad/19)nebo zvažte zakoupení licence pro specializovanější pomoc.

### Jsou možné dočasné licence?

 Ano, dočasné licence jsou k dispozici; můžete požádat o jeden[zde](https://purchase.conholdate.com/temporary-license/).

### Kde mohu získat podrobnou dokumentaci?

 Navštivte komplexní dokumentaci[zde](https://reference.aspose.com/cad/net/) pro více informací.