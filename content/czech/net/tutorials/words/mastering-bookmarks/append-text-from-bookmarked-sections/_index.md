---
title: Připojit text ze sekcí se záložkami v dokumentech aplikace Word
linktitle: Připojit text ze sekcí se záložkami v dokumentech aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak plynule přidávat text ze záložek částí dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento návod krok za krokem.
type: docs
weight: 10
url: /cs/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Zavedení

Už se vám někdy zdálo, že je obtížné připojit text ze sekce se záložkou v dokumentu aplikace Word? Jste na správném místě! Tento tutoriál vás provede procesem krok za krokem pomocí Aspose.Words for .NET. Na konci budete moci přidat text se záložkou jako profesionál. Začněme!

## Předpoklady

Než se ponoříme, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Pokud jste jej ještě nenainstalovali, můžete[stáhněte si jej zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Vývojové prostředí .NET jako Visual Studio.
- Základní znalost C#: Výhodou bude znalost základních konceptů programování v C#.
- Dokument aplikace Word se záložkami: Dokument aplikace Word obsahující záložky, ze kterých budeme přidávat text.

## Importujte potřebné jmenné prostory

Nejprve musíme importovat požadované jmenné prostory pro přístup k funkcím Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Krok 1: Načtěte dokument a inicializujte proměnné

Začněme načtením našich zdrojových a cílových dokumentů Wordu a inicializací potřebných proměnných.

```csharp
//Načtěte zdrojové a cílové dokumenty.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializujte importér dokumentů.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Najděte záložku ve zdrojovém dokumentu.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Krok 2: Identifikujte počáteční a koncový odstavec

Dále musíme najít odstavce, kde začíná a končí záložka. To je nezbytné pro extrakci správného textu.

```csharp
// Identifikujte odstavce na začátku a na konci záložky.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Ověřte odstavce.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Krok 3: Ověřte rodiče odstavce

Musíme zajistit, aby počáteční i koncový odstavec sdílely stejný nadřazený uzel. Jedná se o zjednodušený přístup, aby se předešlo komplikacím.

```csharp
// Zkontrolujte, zda mají počáteční a koncové odstavce stejného rodiče.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Krok 4: Identifikujte uzel, který chcete zastavit

Nyní musíme určit, kde zastavit kopírování textu, což bude uzel bezprostředně za koncovým odstavcem.

```csharp
// Identifikujte uzel hned za koncovým odstavcem.
Node endNode = endPara.NextSibling;
```

## Krok 5: Přidejte k cílovému dokumentu text označený záložkou

Nakonec projdeme uzly od počátečního odstavce k uzlu za koncovým odstavcem a připojíme je k cílovému dokumentu.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Importujte aktuální uzel do cílového dokumentu.
    Node newNode = importer.ImportNode(curNode, true);

    // Připojte importovaný uzel k cílovému dokumentu.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Uložte aktualizovaný cílový dokument.
dstDoc.Save("appended_document.docx");
```

## Závěr

Gratuluji! Úspěšně jste přidali text ze sekce se záložkou v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna usnadňuje manipulaci s dokumenty a nyní máte ve své sadě nástrojů další šikovnou dovednost. Šťastné kódování!

## FAQ

### Mohu připojit text z více záložek najednou?
Ano, postup můžete opakovat pro každou záložku a přidat text podle potřeby.

### Co když mají počáteční a koncové odstavce různé rodiče?
Aktuální příklad předpokládá, že mají stejného rodiče. Pokud ne, budete muset implementovat složitější manipulaci.

### Bude zachováno původní formátování připojeného textu?
 Absolutně! Použití`ImportFormatMode.KeepSourceFormatting`zajišťuje zachování původního formátování.

### Je možné připojit text na konkrétní pozici v cílovém dokumentu?
Ano, můžete přidat text na libovolné požadované místo tak, že přejdete na příslušný uzel v cílovém dokumentu.

### Mohu přidat text ze záložky do nové sekce?
Ano, můžete vytvořit novou sekci v cílovém dokumentu a přidat tam text.