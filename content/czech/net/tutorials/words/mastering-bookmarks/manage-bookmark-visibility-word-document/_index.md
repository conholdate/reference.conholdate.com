---
title: Správa viditelnosti záložek v dokumentech aplikace Word
linktitle: Správa viditelnosti záložek v dokumentech aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Objevte, jak odborně ovládat viditelnost obsahu v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento průvodce krok za krokem.
type: docs
weight: 10
url: /cs/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Zavedení

Jste připraveni zlepšit své dovednosti v manipulaci s dokumenty pomocí Aspose.Words pro .NET? Ať už jste zkušený vývojář, který automatizuje úlohy s dokumenty, nebo zvědavý jedinec zkoumající programovou kontrolu nad soubory Wordu, tato příručka je šitá na míru vám. Dnes se ponoříme do toho, jak zobrazit a skrýt obsah založený na záložkách v dokumentu aplikace Word. Začněme!

## Předpoklady

Než se ponoříme, ujistěte se, že máte následující:

1. Visual Studio: Jakákoli verze kompatibilní s .NET.
2.  Aspose.Words pro .NET: Stáhněte si ji[zde](https://releases.aspose.com/words/net/).
3. Základní znalost C#: Postačí znalost psaní jednoduchých C# programů.
4. Ukázkový dokument aplikace Word: Připravte dokument aplikace Word (např. "Bookmarks.docx") obsahující záložky pro tento výukový program.

### Vytvořit nový projekt

1. Otevřete Visual Studio a vytvořte nový projekt Console App (.NET Core). Pojmenujte to něco jako "BookmarkVisibilityManager".

### Nainstalujte Aspose.Words for .NET

Přidejte Aspose.Words do svého projektu pomocí NuGet Package Manager:

1. Přejděte na Nástroje > Správce balíčků NuGet > Spravovat balíčky NuGet pro řešení.
2. Vyhledejte "Aspose.Words".
3. Nainstalujte balíček.

Po nastavení vašeho projektu přistoupíme k načtení dokumentu.

## Import jmenných prostorů

Začněte importem základních jmenných prostorů. Tyto poskytují třídy a metody nezbytné pro manipulaci s dokumenty aplikace Word pomocí Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Krok 1: Vložení dokumentu

Abychom mohli s dokumentem Word manipulovat, musíme jej nejprve načíst. Postup:

```csharp
// Definujte cestu k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Tento úryvek nastaví cestu k vašemu adresáři dokumentů a načte dokument do a`Document` objekt.

## Krok 2: Zobrazit/skrýt obsah označený záložkou

 Nyní vytvoříme metodu pro přepínání viditelnosti obsahu na základě záložek. Tuto metodu budeme nazývat`ShowHideBookmarkedContent`.

Zde je implementace metody:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Načítání záložek:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` načte zadanou záložku.
- Procházení uzlů: Iterujeme přes uzly v záložce.
-  Přepínač viditelnosti: Pro každý`Run` uzel (představující segment textu), nastavíme jeho`Hidden` majetek založený na`isHidden` parametr.

## Krok 3: Použití metody

Nyní, když máme naši metodu připravenou, pojďme ji použít k zobrazení nebo skrytí obsahu v konkrétní záložce:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Skryje obsah v "MyBookmark1"
```

Tento řádek skryje obsah spojený se záložkou s názvem „MyBookmark1“.

## Krok 4: Uložení dokumentu

Po provedení změn nezapomeňte upravený dokument uložit:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Tím se dokument uloží s aktualizovaným nastavením viditelnosti.

## Závěr

Gratuluji! Úspěšně jste se naučili, jak zobrazit a skrýt obsah označený záložkou v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna zjednodušuje manipulaci s dokumenty, takže je ideální pro automatizaci sestav, vytváření šablon nebo experimentování se soubory aplikace Word. Šťastné kódování!

## FAQ

### Mohu přepínat více záložek najednou?
 Ano, stačí zavolat`ShowHideBookmarkedContent` pro každou záložku, kterou chcete přepnout.

### Ovlivňuje skrytí obsahu strukturu dokumentu?
Ne, skrytí obsahu ovlivní pouze jeho viditelnost; obsah zůstane v dokumentu nedotčen.

### Mohu tuto metodu použít pro jiné typy obsahu?
Tato metoda je speciálně navržena pro textové běhy. U ostatních typů obsahu budete muset odpovídajícím způsobem upravit logiku procházení uzlu.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words nabízí bezplatnou zkušební verzi[zde](https://releases.aspose.com/) , ale pro produkční použití je vyžadována plná licence. Můžete si jej zakoupit[zde](https://purchase.aspose.com/buy).

### Jak mohu získat podporu, pokud narazím na problémy?
 Podporu získáte na fóru komunity Aspose[zde](https://forum.aspose.com/c/words/8).