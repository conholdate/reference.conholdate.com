---
title: Implementujte záhlaví a zápatí pomocí Aspose.Cells pro .NET
linktitle: Implementujte záhlaví a zápatí pomocí Aspose.Cells pro .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Zjistěte, jak vylepšit své dokumenty aplikace Excel pomocí programového přizpůsobení záhlaví a zápatí pomocí Aspose.Cells pro .NET. Tento komplexní průvodce vás provede každým krokem – od nastavení sešitu až po dynamické vkládání názvu listu.
type: docs
weight: 22
url: /cs/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Zavedení

Záhlaví a zápatí jsou základní prvky v tabulkách Excelu, které poskytují důležité kontextové informace, jako jsou názvy souborů, data a čísla stránek. Ať už automatizujete sestavy nebo generujete dynamické soubory, Aspose.Cells for .NET zjednodušuje proces programového přizpůsobení záhlaví a zápatí. Tato příručka nabízí postupný přístup k vylepšení souborů aplikace Excel o dokonalá a profesionální záhlaví a zápatí.

## Předpoklady

Před potápěním se ujistěte, že máte následující:

1.  Aspose.Cells for .NET: Stáhněte a nainstalujte jej z[zde](https://releases.aspose.com/cells/net/).
2. Nastavení IDE: Použijte Visual Studio nebo preferované IDE s rozhraním .NET.
3.  Licence: Začněte s bezplatnou zkušební verzí, ale zvažte získání plné nebo dočasné licence pro kompletní funkčnost. Můžete[získat dočasnou licenci](https://purchase.aspose.com/temporary-license/).

## Import požadovaných balíčků

Začněte importováním potřebných jmenných prostorů do vašeho projektu:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

To vám umožní přístup ke třídám a metodám potřebným pro práci se záhlavími, zápatími a dalšími funkcemi aplikace Excel v Aspose.Cells.

## Krok 1: Vytvořte sešit a otevřete nastavení stránky

Začněte vytvořením nového sešitu a přístupem k nastavení stránky listu. Zde upravíte nastavení záhlaví a zápatí.

```csharp
// Definujte cestu k uložení dokumentu
string dataDir = "Your Document Directory";

// Vytvořte instanci objektu sešitu
Workbook excel = new Workbook();
```

 Zde, a`Workbook` objekt představuje váš soubor Excel. The`PageSetup` vlastnost listu vám umožní přizpůsobit záhlaví a zápatí.

## Krok 2: Otevřete vlastnosti listu a PageSetup

 Každý pracovní list v Aspose.Cells má a`PageSetup` vlastnost, která řídí funkce rozvržení, včetně záhlaví a zápatí. Získejte`PageSetup` objekt pro váš pracovní list:

```csharp
// Získejte odkaz na PageSetup prvního listu
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Teď,`pageSetup` obsahuje nastavení potřebná k přizpůsobení záhlaví a zápatí.

## Krok 3: Nastavte levou část záhlaví

Záhlaví se skládají ze tří částí: levá, středová a pravá. Začněme nastavením levé části pro zobrazení názvu listu.

```csharp
// V levé části záhlaví nastavte název listu
pageSetup.SetHeader(0, "&A");
```

 Použití`&A`dynamicky zobrazuje název listu, což je užitečné zejména pro sešity s více listy.

## Krok 4: Přidejte datum a čas do středu záhlaví

Dále přidejte aktuální datum a čas do střední části záhlaví a použijte vlastní písmo pro styl.

```csharp
// Nastavte datum a čas ve střední části záhlaví s tučným písmem
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

V tomto řádku:
- `&D` vloží aktuální datum.
- `&T` vloží aktuální čas.
- `"Times New Roman,Bold"` použije tučné písmo Times New Roman.

## Krok 5: Zobrazte název souboru v pravé části záhlaví

Pro dokončení záhlaví zobrazte název souboru na pravé straně se zadanou velikostí písma.

```csharp
// Zobrazovat název souboru v pravé části záhlaví s vlastní velikostí písma
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Zde,`&F` představuje název souboru a`&12` nastaví velikost písma na 12.

## Krok 6: Přidejte vlastní text do sekce levé zápatí

Nyní nastavíme levé zápatí vlastní text a konkrétní styl písma.

```csharp
// Přidejte vlastní text se stylem písma do levé části zápatí
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

 tomto příkladu text`123` je nastylován písmem „Courier New“ o velikosti 14, zatímco zbytek zůstává ve výchozím písmu zápatí.

## Krok 7: Vložte číslo stránky do středu zápatí

Zahrnutí čísel stránek do zápatí pomáhá čtenářům sledovat vícestránkové dokumenty.

```csharp
// Vložte číslo stránky do střední části zápatí
pageSetup.SetFooter(1, "&P");
```

 The`&P` kód přidá číslo aktuální stránky do středové části zápatí.

## Krok 8: Zobrazit celkový počet stránek v pravé zápatí

Dokončete zápatí zobrazením celkového počtu stránek v pravé části.

```csharp
// Zobrazit celkový počet stránek v pravé části zápatí
pageSetup.SetFooter(2, "&N");
```

 The`&N` kód poskytuje celkový počet stránek a informuje čtenáře o délce dokumentu.

## Krok 9: Uložte sešit

Nakonec sešit uložte a vygenerujte soubor Excel s přizpůsobenými záhlavími a zápatími.

```csharp
// Uložte sešit
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Tento řádek uloží soubor s vašimi vlastními nastaveními.

## Závěr

Přizpůsobení záhlaví a zápatí v listech aplikace Excel zvyšuje profesionalitu vašich dokumentů. Pomocí Aspose.Cells for .NET můžete tyto prvky snadno ovládat, od zobrazování názvů listů po vkládání vlastního textu, dat, časů a dynamických čísel stránek. Nyní, když jste se naučili kroky, můžete své projekty automatizace Excel pozvednout.

## FAQ

### Mohu použít různá písma pro různé části záhlaví a zápatí?
Ano, Aspose.Cells vám umožňuje určit jedinečná písma pro každou část záhlaví a zápatí.

### Jak odstraním záhlaví a zápatí?
 Vymažte záhlaví a zápatí nastavením jejich textu na prázdný řetězec pomocí`SetHeader` nebo`SetFooter`.

### Mohu vkládat obrázky do záhlaví nebo zápatí pomocí Aspose.Cells pro .NET?
V současné době Aspose.Cells podporuje především text v záhlaví a zápatí. Obrázky mohou vyžadovat alternativní metody, jako je vložení přímo do listu.

### Podporuje Aspose.Cells dynamická data v záhlaví a zápatí?  
 Ano, můžete použít různé dynamické kódy (např`&D`na datum popř`&P` pro číslo stránky) pro přidání dynamického obsahu.

### Jak mohu upravit výšku záhlaví nebo zápatí?  
 Aspose.Cells poskytuje možnosti v rámci`PageSetup` třídy pro úpravu okrajů záhlaví a zápatí, což vám dává kontrolu nad mezerami.