---
title: Cílová strojová písma pomocí Aspose.Words pro .NET
linktitle: Fonty cílového stroje
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak zajistit konzistentní vzhled vašich dokumentů aplikace Word na různých platformách využitím písem pro cílové stroje pomocí Aspose.Words for .NET.
type: docs
weight: 10
url: /cs/net/tutorials/words/html-fixed-save-options/target-machine-font/
---
## Zavedení

Vítejte ve fascinujícím světě Aspose.Words pro .NET! Dnes se vydáme na cestu, abychom prozkoumali, jak používat písma z cílového počítače při práci s dokumenty aplikace Word. Tato funkce zajišťuje, že si vaše dokumenty zachovají svůj zamýšlený vzhled bez ohledu na to, kde si je prohlížíte. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu. Pokud jste tak neučinili, můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí .NET, jako je Visual Studio, je nezbytné.
3. Dokument, se kterým můžete pracovat: Připravte si dokument aplikace Word k testování, například „Odrážky s alternativním fontem.docx“.

S těmito předpoklady se vrhneme na kód!

## Import nezbytných jmenných prostorů

Abychom mohli začít, musíme importovat požadované jmenné prostory. Tento krok propojuje všechny součásti našeho projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Načtěte dokument aplikace Word

 Prvním krokem je načtení dokumentu aplikace Word pomocí`Document` třídy z knihovny Aspose.Words.

### Krok 1.1: Definujte cestu dokumentu

Začněte definováním cesty k adresáři dokumentů:

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### Krok 1.2: Vložte dokument

Nyní načtěte dokument:

```csharp
// Načtěte dokument aplikace Word
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## Krok 2: Nakonfigurujte možnosti uložení

 Dále musíme nastavit možnosti ukládání, abychom zajistili, že písma použitá ve vašem dokumentu pocházejí z cílového počítače. Vytvoříme instanci`HtmlFixedSaveOptions` a nastavte`UseTargetMachineFonts` majetek do`true`.

```csharp
// Nakonfigurujte možnosti uložení pro použití písem z cílového počítače
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## Krok 3: Uložte dokument

Nyní uložme dokument jako pevný soubor HTML. Tady se děje kouzlo!

```csharp
//Převést dokument do pevného HTML
doc.Save(dataDir + "UsingTargetMachineFonts.html", saveOptions);
```

## Krok 4: Ověřte výstup

Nakonec je důležité ověřit výstup. Otevřete uložený soubor HTML ve webovém prohlížeči a zkontrolujte, zda jsou písma správně použita z cílového počítače.

```csharp
// Otevřete soubor HTML a ověřte výstup
System.Diagnostics.Process.Start(dataDir + "UsingTargetMachineFonts.html");
```

A tady to máte! Úspěšně jste použili písma z cílového počítače v dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Závěr

Využití písem z cílového počítače zajistí, že vaše dokumenty Word budou vypadat konzistentně a profesionálně, bez ohledu na to, kde jsou zobrazeny. Aspose.Words for .NET tento proces zjednodušuje a umožňuje vám snadno načítat dokumenty, konfigurovat možnosti ukládání a ukládat je s požadovaným nastavením písma.

## FAQ

### Mohu tuto metodu použít s jinými formáty dokumentů?
Ano, Aspose.Words for .NET podporuje různé formáty dokumentů a pro různé formáty můžete použít podobné možnosti ukládání.

### Co když cílový počítač nemá požadovaná písma?
Pokud na cílovém počítači chybí potřebná písma, dokument se nemusí vykreslit správně. V případě potřeby je vhodné vložit písma.

### Jak vložím písma do dokumentu?
 Písma můžete vkládat pomocí`FontSettings` třídy v Aspose.Words pro .NET. Viz[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Existuje způsob, jak zobrazit náhled dokumentu před uložením?
 Ano,`DocumentRenderer` class umožňuje zobrazit náhled dokumentu před uložením. Zkontrolujte Aspose.Words pro .NET[dokumentace](https://reference.aspose.com/words/net/) pro více informací.

### Mohu dále upravit výstup HTML?
 Absolutně! The`HtmlFixedSaveOptions` class poskytuje různé vlastnosti pro přizpůsobení výstupu HTML. Prozkoumat[dokumentace](https://reference.aspose.com/words/net/) pro všechny dostupné možnosti.