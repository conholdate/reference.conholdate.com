---
title: Vytvoření vyplněného obdélníku
linktitle: Vytvoření vyplněného obdélníku
second_title: Aspose.PDF pro .NET API Reference
description: Odemkněte sílu manipulace s PDF pomocí Aspose.PDF pro .NET v tomto podrobném tutoriálu. Naučte se, jak programově vytvářet vizuálně přitažlivé dokumenty PDF kreslením vyplněných obdélníků.
type: docs
weight: 50
url: /cs/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Zavedení

Chtěli jste někdy programově vytvářet vizuálně ohromující soubory PDF? Pokud ano, jste na správném místě! V tomto tutoriálu prozkoumáme Aspose.PDF for .NET, výkonnou knihovnu, která zjednodušuje manipulaci s dokumenty PDF. Dnes se zaměříme na vytvoření vyplněného obdélníku v souboru PDF. Ať už jste zkušený vývojář nebo teprve začínáte, tento průvodce vás přátelsky a poutavě provede každým krokem. Takže popadněte svůj kódovací klobouk a můžeme začít!

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte následující:

1. Visual Studio: Nainstalujte si Visual Studio na svůj počítač, protože je to vynikající IDE pro vývoj .NET.
2. Aspose.PDF pro .NET: Stáhněte si a nainstalujte knihovnu Aspose.PDF z[zde](https://releases.aspose.com/pdf/net/).
3. Základní znalost C#: Znalost programování v C# vám pomůže lépe porozumět úryvkům kódu.

## Krok 1: Vytvořte nový projekt

1. Otevřete Visual Studio a vytvořte nový projekt aplikace konzoly.
2. Pojmenujte svůj projekt vhodně.

## Krok 2: Přidejte odkaz Aspose.PDF

1. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
2. Vyberte Spravovat balíčky NuGet.
3. Vyhledejte Aspose.PDF a nainstalujte nejnovější verzi.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Nyní, když máme vše nastaveno, pojďme se ponořit do kódu!

## Krok 3: Nastavte adresář dokumentů

Zadejte cestu, kam bude váš PDF uložen:

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou na vašem počítači, kam chcete PDF uložit.

## Krok 4: Vytvořte instanci dokumentu

Inicializujte nový dokument PDF:

```csharp
//Vytvořit instanci dokumentu
Document doc = new Document();
```

## Krok 5: Přidejte stránku do dokumentu

Každý PDF potřebuje alespoň jednu stránku. Přidejme jeden:

```csharp
// Přidat stránku do kolekce stránek souboru PDF
Page page = doc.Pages.Add();
```

## Krok 6: Vytvořte instanci grafu

 A`Graph` instance funguje jako plátno pro kreslení tvarů:

```csharp
// Vytvořte instanci Graph
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Krok 7: Přidejte graf na stránku

Připojte graf ke stránce:

```csharp
// Přidejte objekt grafu do kolekce odstavců instance stránky
page.Paragraphs.Add(graph);
```

## Krok 8: Vytvořte instanci obdélníku

Definujte polohu a velikost obdélníku:

```csharp
// Vytvořte instanci obdélníku
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Krok 9: Zadejte barvu výplně

Vyberte barvu pro svůj obdélník. Pro tento příklad použijeme červenou:

```csharp
// Určete barvu výplně pro objekt Graph
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Krok 10: Přidejte obdélník do grafu

Přidejte obdélník do grafu:

```csharp
// Přidejte obdélníkový objekt do kolekce tvarů objektu Graph
graph.Shapes.Add(rect);
```

## Krok 11: Uložte dokument PDF

Nakonec uložte dokument do určeného adresáře:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Uložit soubor PDF
doc.Save(dataDir);
```

## Krok 12: Potvrzující zpráva

Vytiskněte potvrzovací zprávu pro potvrzení úspěchu:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Závěr

Gratuluji! Úspěšně jste vytvořili vyplněný obdélník v dokumentu PDF pomocí Aspose.PDF for .NET. Tato výkonná knihovna otevírá svět možností pro manipulaci s PDF a umožňuje vám programově generovat úžasné dokumenty. Ať už vytváříte zprávy, faktury nebo jakýkoli jiný typ PDF, Aspose.PDF vám pomůže.

## FAQ

### Co je Aspose.PDF pro .NET?
Aspose.PDF for .NET je knihovna, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty PDF programově.

### Mohu používat Aspose.PDF zdarma?
 Ano, Aspose nabízí bezplatnou zkušební verzi, kterou můžete použít k prozkoumání funkcí knihovny. Můžete si jej stáhnout[zde](https://releases.aspose.com/).

### Existuje způsob, jak získat podporu pro Aspose.PDF?
 Absolutně! Podporu můžete získat prostřednictvím fóra Aspose[zde](https://forum.aspose.com/c/pdf/10).

### Jak mohu zakoupit Aspose.PDF?
 Aspose.PDF si můžete zakoupit na stránce nákupu[zde](https://purchase.aspose.com/buy).

### Jaké typy tvarů mohu vytvořit pomocí Aspose.PDF?
Pomocí knihovny Aspose.PDF můžete vytvářet různé tvary, včetně obdélníků, kruhů, čar a dalších.