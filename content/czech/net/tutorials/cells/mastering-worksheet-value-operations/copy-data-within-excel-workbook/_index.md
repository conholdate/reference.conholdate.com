---
title: Kopírování dat v sešitu aplikace Excel pomocí Aspose.Cells pro .NET
linktitle: Kopírování dat v sešitu aplikace Excel pomocí Aspose.Cells pro .NET
second_title: Aspose.Cells .NET Excel Processing API
description: Naučte se efektivně kopírovat data v excelovém sešitu pomocí Aspose.Cells for .NET. Podle tohoto podrobného průvodce snadno duplikujete listy, přenesete data a snadno spravujete soubory Excel.
type: docs
weight: 12
url: /cs/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Zavedení

V tomto podrobném průvodci si ukážeme, jak kopírovat data ve stejném sešitu pomocí Aspose.Cells for .NET. Podle níže uvedených podrobných pokynů se naučíte, jak programově duplikovat listy, zachovat jejich obsah a formátování.

## Předpoklady pro kopírování dat v Excelu pomocí Aspose.Cells

Než se pustíte do procesu kódování, ujistěte se, že máte vše na svém místě:

1. Knihovna Aspose.Cells for .NET: Musíte mít nainstalovanou knihovnu Aspose.Cells for .NET. Nejnovější verzi si můžete stáhnout z[Stránka ke stažení Aspose.Cells for .NET](https://releases.aspose.com/cells/net/).
2. Vývojové prostředí: Pro psaní a běh vašeho kódu je nezbytné IDE kompatibilní s .NET, jako je Visual Studio.
3.  Aspose License: Můžete použít buď bezplatnou zkušební verzi, nebo zakoupenou licenci. Pro více informací navštivte[zde](https://purchase.aspose.com/temporary-license/).

Jakmile jsou předpoklady nastaveny, jste připraveni začít s knihovnou pracovat.

## Import požadovaných balíčků

Chcete-li začít, budete muset importovat příslušné jmenné prostory z Aspose.Cells. To vám umožní pracovat se soubory aplikace Excel pomocí tříd a metod poskytovaných Aspose.Cells.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Tyto jmenné prostory vám umožní přístup k`Workbook` třídy (pro práci se soubory Excel) a`WorksheetCollection` (pro přístup k více listům v sešitu).

## Krok 1: Inicializujte cesty souborů pro sešit

Aby byl váš kód uspořádaný, je nezbytné definovat cesty k souborům, kde je váš sešit umístěn a kam chcete upravený soubor uložit. Cesty můžete určit takto:

```csharp
// Definujte cestu k adresáři, kde je umístěn soubor Excel.
string dataDir = "Your Directory Path";

// Definujte úplnou cestu ke vstupnímu sešitu.
string inputPath = dataDir + "book1.xls";
```

 Nahradit`"Your Directory Path"` se skutečnou cestou k vašemu adresáři obsahujícímu sešit. To pomáhá zajistit, že kód je flexibilní a že můžete efektivně spravovat cesty.

## Krok 2: Otevřete sešit pro přístup k datům

 Nyní, když jsou cesty k souborům nastaveny, je dalším krokem načtení sešitu Excel do a`Workbook` objekt. To vám umožní přístup k jeho obsahu pro manipulaci.

```csharp
// Načtěte soubor aplikace Excel do objektu Workbook.
Workbook wb = new Workbook(inputPath);
```

 S tímto řádkem jste úspěšně načetli`book1.xls` do`wb` objekt, zpřístupňující jeho data.

## Krok 3: Vstupte do kolekce Worksheets

 Po načtení sešitu získáte přístup k listům, které jsou v něm obsaženy. Aspose.Cells poskytuje`Worksheets`kolekce, která umožňuje interakci s každým listem v sešitu.

```csharp
// Načtěte kolekci listů ze sešitu.
WorksheetCollection sheets = wb.Worksheets;
```

 The`sheets` objekt vám nyní poskytuje přístup ke všem pracovním listům v rámci`book1.xls`a můžete s nimi provádět různé operace, včetně kopírování dat z jednoho listu na druhý.

## Krok 4: Zkopírujte data z jednoho listu do druhého

 Pro kopírování dat z jednoho listu do druhého v rámci stejného sešitu nabízí Aspose.Cells snadno použitelnou metodu tzv.`AddCopy`. Tato metoda vytvoří duplikát zadaného listu a připojí jej k sešitu.

```csharp
// Zkopírujte data z "List1" do nového listu v sešitu.
sheets.AddCopy("Sheet1");
```

 V tomto příkladu kopírujeme data z "List1" do nového listu. The`AddCopy` metoda zduplikuje celý list a zachová veškerý jeho obsah, včetně vzorců, formátování a hodnot.

## Krok 5: Uložte upravený sešit

 Po zkopírování dat můžete upravený sešit uložit s novým názvem nebo umístěním. To se provádí zavoláním na`Save`metoda na`Workbook` objekt.

```csharp
//Uložte upravený sešit pod novým názvem.
wb.Save(dataDir + "book1_copy.xls");
```

 Tím se sešit se zkopírovaným listem uloží jako`book1_copy.xls` v zadaném adresáři. Název souboru a cestu můžete změnit podle svých potřeb.

## Závěr

Kopírování dat v sešitu aplikace Excel pomocí Aspose.Cells for .NET je snadný úkol a tato příručka obsahuje kroky potřebné k tomu, aby to bylo efektivní. Ať už duplikujete celé listy nebo konkrétní rozsahy dat, Aspose.Cells nabízí robustní a flexibilní API, díky kterému je automatizace Excelu jednoduchá a efektivní.

## FAQ

### Mohu kopírovat více listů najednou?

Aspose.Cells nepodporuje kopírování více listů v jednom volání. Můžete však procházet listy, které chcete kopírovat, a kopírovat je jednotlivě.

### Jak mohu přejmenovat zkopírovaný list?

Po zkopírování listu jej můžete přejmenovat následovně:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Je Aspose.Cells kompatibilní s .NET Core?

Ano, Aspose.Cells je plně kompatibilní s prostředím .NET Framework i .NET Core.

### Jak Aspose.Cells zpracovává formátování během kopírování?

 The`AddCopy`metoda zachová veškerý obsah a formátování při kopírování listů, čímž zajistí, že zkopírovaná data budou vypadat stejně jako originál.

### Mohu zkopírovat list do jiného sešitu?

 Ano, list můžete zkopírovat do jiného sešitu pomocí`Copy` metoda s odkazem na cílový sešit.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```