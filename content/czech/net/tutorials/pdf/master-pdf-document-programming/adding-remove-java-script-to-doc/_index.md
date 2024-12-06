---
title: Přidání Remove Javascript to PDF Document
linktitle: Přidání Remove Javascript to PDF Document
second_title: Aspose.PDF pro .NET API Reference
description: Tento komplexní průvodce vám ukáže, jak přidávat vlastní chování, dynamicky provádět výpočty nebo ověřování a jak se integrovat s jinými softwarovými aplikacemi.
type: docs
weight: 30
url: /cs/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## Zavedení

V tomto komplexním průvodci se ponoříme do světa Aspose.PDF pro .NET a odemkneme jeho plný potenciál přidávat do vašich dokumentů PDF vlastní funkce JavaScriptu. Tato výkonná funkce vám umožňuje začlenit dynamické prvky, zlepšit uživatelské prostředí a zefektivnit pracovní postupy.

## Předpoklady

Chcete-li pokračovat, budete potřebovat:

1. Aspose.PDF for .NET nainstalovaný ve vašem projektu (stáhnout z[Stránka pro stahování Aspose.PDF pro .NET](https://releases.aspose.com/pdf/net/))
2. Platná licence k používání knihovny
3. AC# IDE nebo textový editor

## Importujte balíčky

Chcete-li začít, importujte do projektu potřebné jmenné prostory:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## Krok 1: Inicializujte nový dokument PDF

Vytvořte nový dokument PDF a přidejte jej na své plátno:

```csharp
Document doc = new Document();
doc.Pages.Add();
```

Zde začnete vytvářet své PDF s vysokým obsahem JavaScriptu.

## Krok 2: Přidejte JavaScript do PDF

 Vložte funkce JavaScriptu do dokumentu pomocí`doc.JavaScript` sbírka. Zde je příklad:

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## Krok 3: Uložte PDF pomocí JavaScriptu

Uložte aktualizovaný dokument na disk:

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

Nyní můžete přistupovat a upravovat kód JavaScript v existujícím PDF.

## Krok 4: Načtěte a zobrazte JavaScript ve stávajícím PDF

 Načtěte soubor PDF, který obsahuje JavaScript, a získejte přístup k jeho klíčům pomocí`Keys` vlastnictví:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## Krok 5: Zobrazení funkcí JavaScriptu

Iterujte pomocí kláves JavaScriptu a vytiskněte jejich odpovídající kód do konzole:

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

To ukazuje, jak můžete ověřit, které funkce JavaScriptu jsou aktuálně přítomny.

## Krok 6: Odstraňte JavaScript z PDF

Najděte požadovanou funkci JavaScript pomocí jejího názvu a odstraňte ji:

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

Ověřte, zda byla funkce úspěšně odstraněna, opakovaným tiskem zbývajících funkcí.

## Závěr

V tomto komplexním průvodci jste zjistili, jak odemknout sílu přizpůsobitelné funkce JavaScriptu Aspose.PDF pro .NET. Pomocí této funkce můžete vytvářet dynamické soubory PDF, vylepšovat uživatelské prostředí a zjednodušit pracovní postupy. Zvládnutím těchto kroků a dalším prozkoumáním možností knihovny budete na dobré cestě k odemknutí nových možností ve vašich aplikacích.

## FAQ

### Mohu do jednoho PDF přidat více funkcí JavaScriptu?
 Ano! Pomocí příkazu můžete přidat tolik funkcí JavaScriptu, kolik potřebujete`doc.JavaScript` sbírka.

### Co se stane, když se pokusím odstranit neexistující funkci JavaScriptu?
 Pokud funkce neexistuje,`Remove` metoda nevyhodí chybu, ale také nic neodstraní. Chcete-li zpracovat neexistující funkce, můžete přidat další zpracování chyb nebo upravit kód tak, aby je ignoroval.

### Je možné spustit JavaScript ihned po otevření PDF?
Ano! JavaScript můžete nakonfigurovat tak, aby se spouštěl na konkrétních spouštěčích, jako je otevření dokumentu nebo kliknutí na tlačítko.

### Mohu upravit JavaScript poté, co byl přidán do PDF?
Ano, můžete načíst existující PDF, získat přístup k jeho JavaScriptu, upravit kód a dokument znovu uložit.

### Má odstranění JavaScriptu vliv na zbytek obsahu PDF?
Ne, odstranění JavaScriptu ovlivní pouze skript. Obsah PDF zůstává nezměněn.