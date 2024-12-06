---
title: Převeďte DGN do PDF v Aspose.CAD pro .NET
linktitle: Převeďte DGN do PDF v Aspose.CAD pro .NET
second_title: Aspose.CAD .NET – formát souborů CAD a BIM
description: Naučte se, jak bez námahy převádět soubory DGN do PDF pomocí výkonné knihovny Aspose.CAD pro .NET. Tento průvodce krok za krokem je určen pro vývojáře všech úrovní.
type: docs
weight: 12
url: /cs/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Zavedení

Navigace ve světě CAD souborů může být náročná, ale s Aspose.CAD for .NET mohou vývojáři snadno manipulovat a převádět různé CAD formáty. Jednou z běžných potřeb je převod souborů DGN do PDF, což krok za krokem prozkoumáme v tomto tutoriálu.

## Předpoklady

Chcete-li pokračovat, ujistěte se, že máte následující:

- Základní znalost C# a .NET frameworku.
-  Nainstalovaná knihovna Aspose.CAD for .NET. Můžete si jej stáhnout[zde](https://releases.aspose.com/cad/net/).
- Ukázkový soubor DGN (např. Nikon_D90_Camera.dgn). 

## Krok 1: Importujte požadované jmenné prostory

Začněte importováním příslušných jmenných prostorů do vašeho projektu C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Krok 2: Načtěte soubor DGN

Zadejte adresář pro váš soubor DGN a načtěte jej pomocí následujícího kódu:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Zde proběhne další zpracování...
}
```

## Krok 3: Nakonfigurujte možnosti rastrování

Dále nastavte možnosti rasterizace, abyste definovali, jak bude vaše DGN vykresleno v PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Upravte šířku podle potřeby
    PageHeight = 300, // Nastavte výšku podle potřeby
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Krok 4: Vytvořte možnosti PDF

Definujte možnosti PDF integrováním nastavení rastrování nakonfigurovaných dříve:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Krok 5: Uložte DGN jako PDF

Nakonec uložte soubor DGN jako PDF pomocí možností, které jste nakonfigurovali:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Závěr

Gratuluji! Úspěšně jste převedli soubor DGN do PDF pomocí Aspose.CAD for .NET. Tento jednoduchý tutoriál vás provede načtením souboru DGN, nastavením možností rastrování a uložením výstupu jako PDF.

## FAQ

### Potřebuji předchozí znalosti CAD, abych mohl používat Aspose.CAD?  
Absolutně! Aspose.CAD je navržen tak, aby zjednodušil složité úlohy CAD a zpřístupnil jej všem vývojářům bez ohledu na jejich znalosti CAD.

### Kde najdu další zdroje a dokumentaci k Aspose.CAD?  
 Můžete prozkoumat komplexní průvodce a příklady v[Dokumentace Aspose.CAD](https://reference.aspose.com/cad/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.CAD?  
 Ano, lze získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Jak mohu získat dočasnou licenci pro Aspose.CAD?  
 Můžete požádat o dočasné licence[zde](https://purchase.conholdate.com/temporary-license/).

### Potřebujete pomoc nebo máte otázky?  
 Zapojte se do konverzace v[Fórum Aspose.CAD](https://forum.aspose.com/c/cad/19) za podporu komunity a dotazy.