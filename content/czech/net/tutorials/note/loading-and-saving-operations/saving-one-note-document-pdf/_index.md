---
title: Ukládání dokumentů OneNotu do PDF pomocí Aspose.Note pro .NET
linktitle: Ukládání dokumentů OneNotu do PDF
second_title: Aspose.Note .NET API
description: Naučte se, jak efektivně ukládat dokumenty Microsoft OneNote jako soubory PDF pomocí Aspose.Note pro .NET. Tato příručka vás provede nezbytnými předpoklady a nabídne užitečné často kladené otázky.
type: docs
weight: 26
url: /cs/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Zavedení

V tomto tutoriálu prozkoumáme, jak ukládat dokumenty do formátu PDF pomocí Aspose.Note pro .NET. Aspose.Note je výkonná knihovna, která umožňuje vývojářům pracovat se soubory Microsoft OneNote programově. Pokryjeme předpoklady, importujeme jmenné prostory a poskytneme podrobné průvodce ukládáním dokumentů do PDF v různých rozvrženích stránek.

## Předpoklady
1. Visual Studio: Ujistěte se, že je nainstalováno.
2. Aspose.Note pro .NET: Stáhněte a nainstalujte knihovnu.
3. Znalost C#: Vyžaduje se základní znalost jazyka.

## Import nezbytných jmenných prostorů
Než budete pokračovat, importujte do kódu následující jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Krok 1: Uložte do PDF s nastavením stránky Letter
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Aktualizujte tuto cestu
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Načte dokument OneNotu a uloží jej jako PDF pomocí nastavení stránky velikosti Letter.

## Krok 2: Uložit do PDF s nastavením stránky A4 (bez omezení výšky)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Aktualizujte tuto cestu
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Podobně jako v kroku 1, ale používá nastavení stránky A4 bez omezení výšky.

## Závěr
Výukový program úspěšně ukazuje, jak převést soubory OneNote do formátu PDF pomocí Aspose.Note. Využitím různých nastavení stránky získají vývojáři flexibilitu při správě dokumentů.

## FAQ
### Dokáže Aspose.Note zpracovat složité soubory OneNotu?
Ano, efektivně zvládá různé funkce složitých souborů OneNotu.

### Je Aspose.Note vhodný pro komerční projekty?
Ano, po zakoupení licence jej můžete používat pro komerční aplikace.

### Nabízí Aspose.Note bezplatnou zkušební verzi?
Ano, k prozkoumání je k dispozici bezplatná zkušební verze.

### Kde najdu dokumentaci k Aspose.Note?
Podrobná dokumentace je k dispozici na referenční stránce Aspose.

### Potřebujete další pomoc?
Otázky a podporu najdete na fóru Aspose.Note.
