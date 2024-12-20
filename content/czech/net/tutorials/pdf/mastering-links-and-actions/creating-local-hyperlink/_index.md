---
title: Vytvoření místního hypertextového odkazu v souboru PDF
linktitle: Vytvoření místního hypertextového odkazu v souboru PDF
second_title: Aspose.PDF pro .NET API Reference
description: Objevte, jak zlepšit navigaci v dokumentech PDF vytvořením místních hypertextových odkazů pomocí Aspose.PDF for .NET. Tento návod krok za krokem vás provede celým procesem.
type: docs
weight: 40
url: /cs/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Zavedení

V této příručce vás provedeme procesem vytváření místních hypertextových odkazů v souboru PDF pomocí Aspose.PDF for .NET. Každý krok jasně rozebereme a zajistíme, že i když jste v práci s PDF nováčky, budete je moci bez námahy sledovat.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

1.  Visual Studio: Stáhněte si jej z[Webové stránky Visual Studia](https://visualstudio.microsoft.com/).
2.  Aspose.PDF pro .NET: Stáhněte si knihovnu přes[Aspose webové stránky](https://releases.aspose.com/pdf/net/). Tato knihovna poskytuje bohatou sadu funkcí pro manipulaci s PDF.
3. Základní znalost C#: Znalost programování v C# pomůže, ale nebojte se; vysvětlíme si kód řádek po řádku.
4. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework. Zkontrolujte požadavky na Aspose.PDF[dokumentace](https://reference.aspose.com/pdf/net/).

S těmito předpoklady jste připraveni naučit se vytvářet místní hypertextové odkazy v dokumentech PDF!

## Import požadovaných balíčků

Nyní, když jste vše nastavili, je čas naimportovat potřebné balíčky do vašeho projektu C#.

### Otevřete svůj projekt

Otevřete svůj stávající projekt .NET nebo vytvořte nový v aplikaci Visual Studio. Pokud začínáte znovu, vyberte na úvodní obrazovce možnost „Vytvořit nový projekt“.

### Přidejte odkaz do Aspose.PDF

 Klikněte pravým tlačítkem myši na "Dependencies" ve složce projektu v Průzkumníku řešení. Vyberte „Spravovat balíčky NuGet“ a vyhledejte`Aspose.PDF`a nainstalujte nejnovější dostupnou verzi. To přinese všechny nástroje, které potřebujete pro vytváření a manipulaci s PDF.

### Importovat jmenné prostory

V horní části souboru .cs přidejte následující pomocí direktiv:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Tyto direktivy vám umožňují bezproblémový přístup k funkcím knihovny.

Pojďme si proces vytváření lokálních hypertextových odkazů rozdělit do jednoduchých kroků.

## Krok 1: Nastavte instanci dokumentu

 Vytvořte novou instanci souboru`Document` třídy představující soubor PDF, se kterým budete pracovat.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Nastavte adresář dokumentů
Document doc = new Document(); //Vytvořit instanci dokumentu
```

 Nahradit`"YOUR_DOCUMENT_DIRECTORY"` se skutečnou cestou ve vašem systému, kam bude PDF uložen.

## Krok 2: Přidejte stránku do dokumentu

Poté do dokumentu PDF přidejte stránku.

```csharp
Page page = doc.Pages.Add(); // Přidat novou stránku
```

Tento řádek přidá do dokumentu novou stránku, na kterou bude umístěn veškerý váš obsah.

## Krok 3: Vytvořte textový fragment

Nyní vytvoříme text, který bude fungovat jako odkaz, na který lze kliknout.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Vytvořte fragment textu
```

 Tento`TextFragment` zobrazí text, na který mohou uživatelé kliknout.

## Krok 4: Vytvořte místní hypertextový odkaz

Nyní vytvořte místní hypertextový odkaz, který odkazuje na stránku 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Vytvořte místní hypertextový odkaz
link.TargetPageNumber = 7; // Nastavte cílovou stránku odkazu
text.Hyperlink = link; // Nastavte hypertextový odkaz pro fragment textu
```

 The`LocalHyperlink` class umožňuje zadat číslo cílové stránky pro hypertextový odkaz.

## Krok 5: Přidejte textový fragment na stránku

Přidejte klikací text na stránku, kterou jste vytvořili.

```csharp
page.Paragraphs.Add(text); // Přidejte fragment textu na stránku
```

Tento řádek přidá váš text do kolekce odstavců na stránce.

## Krok 6: Vytvořte další textový fragment (volitelné)

Pojďme přidat další hypertextový odkaz pro přechod zpět na stránku 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Vytvořte nový textový fragment
textBack.IsInNewPage = true; // Uveďte, že by měl být na nové stránce
```

## Krok 7: Nastavte druhý místní hypertextový odkaz

Vytvořte další místní hypertextový odkaz pro stránku 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Vytvořte další místní hypertextový odkaz
linkBack.TargetPageNumber = 1; // Nastavte cílovou stránku pro druhý hypertextový odkaz
textBack.Hyperlink = linkBack; // Nastavte hypertextový odkaz pro druhý textový fragment
```

## Krok 8: Přidejte druhý textový fragment na novou stránku

Přidejte druhý fragment textu na jeho stránku.

```csharp
Page newPage = doc.Pages.Add(); // Přidejte novou stránku pro druhý odkaz
newPage.Paragraphs.Add(textBack); // Přidejte fragment textu na novou stránku
```

## Krok 9: Uložte dokument

Nakonec dokument uložte.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Zadejte název výstupního souboru
doc.Save(dataDir); // Uložte aktualizovaný dokument
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Tento řádek kombinuje cestu k vašemu adresáři s názvem souboru a`Save()` metoda uloží váš dokument.

## Závěr

Vytváření lokálních hypertextových odkazů v souborech PDF pomocí Aspose.PDF for .NET je praktická funkce, která zlepšuje navigaci a uživatelskou zkušenost. Nyní máte znalosti, jak navést své čtenáře přímo k informacím, které potřebují, díky čemuž budou vaše soubory PDF interaktivnější a uživatelsky přívětivější.

## FAQ

### Co je Aspose.PDF pro .NET?
Aspose.PDF for .NET je knihovna, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty PDF programově pomocí rozhraní .NET.

### Mohu vytvořit hypertextové odkazy na externí webové stránky?
Ano, Aspose.PDF také podporuje vytváření hypertextových odkazů na externí URL kromě lokálních hypertextových odkazů v rámci PDF.

### Existuje bezplatná zkušební verze pro Aspose.PDF?
 Absolutně! K bezplatné zkušební verzi můžete přistupovat z[Aspose webové stránky](https://releases.aspose.com/).

### Jaké programovací jazyky Aspose podporuje?
Aspose nabízí knihovny pro různé programovací jazyky, včetně Javy, C++, a Python, mimo jiné.

### Jak získám podporu pro produkty Aspose?
 Podporu můžete hledat prostřednictvím[Fórum Aspose](https://forum.aspose.com/c/pdf/10).