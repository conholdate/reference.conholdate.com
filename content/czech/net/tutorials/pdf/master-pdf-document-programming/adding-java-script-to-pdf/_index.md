---
title: Přidání Java Scriptu do souboru PDF
linktitle: Přidat soubor PDF Java Script
second_title: Aspose.PDF pro .NET API Reference
description: Tento dokument poskytuje komplexní průvodce přidáváním interaktivních prvků, jako jsou vyskakovací upozornění nebo funkce automatického tisku, do dokumentů PDF pomocí Aspose.PDF for .NET.
type: docs
weight: 10
url: /cs/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Zavedení
Tento dokument poskytuje komplexní průvodce přidáváním interaktivních prvků, jako jsou vyskakovací upozornění nebo funkce automatického tisku, do dokumentů PDF pomocí Aspose.PDF for .NET. Využitím možností této knihovny můžete vytvářet dynamické a poutavé soubory PDF, které uspokojí různé potřeby uživatelů.

## Předpoklady
 Než budete pokračovat, ujistěte se, že jste si stáhli nejnovější verzi Aspose.PDF pro .NET z[Aspose Releases](https://releases.aspose.com/pdf/net/) nebo získat bezplatnou zkušební verzi prostřednictvím svých webových stránek:[releases.aspose.com](http://releases.aspose.com).

Měli byste mít také základní znalosti C# a znát vývojové prostředí, které používáte. Navíc, pokud se během vašeho vývojového procesu potřebujete vyhnout omezením, zvažte získání dočasné licence od Aspose.

## Import nezbytných balíčků
Chcete-li začít psát kód, importujte požadované jmenné prostory z knihovny Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Krok 1: Načtení existujícího PDF
Načtěte existující dokument PDF, do kterého chcete přidat interaktivní prvky:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu souboru PDF.

## Krok 2: Přidání JavaScriptu na úrovni dokumentu

 Chcete-li použít skript, který se spustí při otevření dokumentu, vytvořte instanci a`JavascriptAction` objekt:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Krok 3: Přidání JavaScriptu na úrovni stránky

 Chcete-li spustit konkrétní akce na základě otevření nebo zavření stránky, vytvořte instanci a`JavascriptAction` objekt pro každou stránku:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Krok 4: Uložení dokumentu PDF

Chcete-li uložit upravený dokument PDF, zadejte cestu k výstupnímu souboru:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Závěr
Dodržováním tohoto průvodce a používáním Aspose.PDF for .NET můžete efektivně vylepšit své PDF interaktivními prvky. Tato knihovna nabízí komplexní řešení pro vytváření dynamických a poutavých dokumentů, které uspokojí různé potřeby uživatelů.

## FAQ

### Mohu přidat více akcí JavaScriptu na různé stránky v PDF?
Ano, jednotlivým stránkám nebo celému dokumentu můžete přiřadit různé akce JavaScriptu.

### Je možné odstranit JavaScript z PDF po jeho přidání?
 Ano, existující akce JavaScriptu můžete odstranit nebo upravit vymazáním`Actions` vlastnosti dokumentu nebo stránky.

### Jaké funkce JavaScriptu mohu použít v PDF?
Můžete použít jakýkoli JavaScript podporovaný jádrem JavaScriptu Adobe Acrobat, jako je tisk, upozornění a manipulace s formuláři.

### Funguje JavaScript ve všech prohlížečích PDF?
Většina akcí JavaScriptu bude fungovat v prohlížečích PDF, které podporují interaktivní soubory PDF, jako je Adobe Acrobat. Některé základní čtečky PDF však nemusí podporovat JavaScript.