---
title: Přenos uživatelských formulářů a maker VBA mezi sešity aplikace Excel
linktitle: Přenos uživatelských formulářů a maker VBA mezi sešity aplikace Excel
second_title: Aspose.Cells .NET Excel Processing API
description: Odemkněte sílu automatizace Excelu s tímto komplexním průvodcem o přenosu uživatelských formulářů a maker VBA mezi sešity pomocí Aspose.Cells for .NET. Ideální pro začátečníky i zkušené vývojáře.
type: docs
weight: 11
url: /cs/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Zavedení

Vítejte ve vašem dokonalém průvodci pro vylepšení vaší zkušenosti s Excelem pomocí maker VBA a uživatelských formulářů! V tomto tutoriálu prozkoumáme, jak přenést VBA Macro UserForm Designer z jednoho sešitu do druhého pomocí výkonné knihovny Aspose.Cells for .NET. Ať už jste zkušený vývojář nebo teprve začínáte, tento podrobný průvodce vás vybaví znalostmi, jak programově pracovat se soubory Excel. Jste připraveni se ponořit? Začněme!

## Předpoklady
Než se pustíme do kódování, ujistěte se, že máte vše, co potřebujete:

1. Vývojové prostředí C#: Pracovní prostředí pro vývoj v C#, vysoce doporučeno Visual Studio.
2.  Aspose.Cells for .NET Library: Ujistěte se, že jste do svého projektu integrovali knihovnu Aspose.Cells. Můžete snadno[stáhněte si jej zde](https://releases.aspose.com/cells/net/).
3. Základní znalost VBA a Excel maker: Znalost jazyka VBA a fungování maker Excelu zlepší vaše porozumění tomuto kurzu.
4. Excelový soubor s uživatelským formulářem: Vytvořte nebo získejte excelový sešit obsahující uživatelský formulář (nejlépe s povolenými makry, např.`.xlsm` soubory).

## Import požadovaných balíčků
Chcete-li využívat funkce poskytované Aspose.Cells, zahrňte do horní části souboru C# následující jmenné prostory:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Tyto jmenné prostory vám umožní přístup k výkonným nástrojům zabudovaným do knihovny Aspose.Cells.

## Krok 1: Definujte zdrojový a výstupní adresář
Nejprve stanovte umístění souborů:

```csharp
// Definujte zdrojový a výstupní adresář
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Nahraďte zástupné cesty skutečnými adresáři, kde jsou uloženy vaše soubory.

## Krok 2: Vytvořte prázdný cílový sešit
Dále vytvořte nový sešit, do kterého zkopírujete uživatelský formulář a makra:

```csharp
// Vytvořte prázdný cílový sešit
Workbook target = new Workbook();
```

Tím se inicializuje prázdný sešit, který slouží jako vaše plátno pro nadcházející přenos dat.

## Krok 3: Načtěte sešit šablon
Načtěte sešit obsahující uživatelský formulář a makra:

```csharp
// Načtěte soubor aplikace Excel obsahující formulář uživatele VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Upravit`"sampleDesignerForm.xlsm"` na název vašeho skutečného souboru.

## Krok 4: Zkopírujte listy do cílového sešitu
Nyní zkopírujeme listy ze šablony do cílového sešitu:

```csharp
// Zkopírujte všechny šablony listů do cílového sešitu
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Přidejte zprávu do buňky A2 cílového listu
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Tento kód prochází každý list v šabloně a zkopíruje jej do cílového sešitu, čímž zajistí bezproblémový přenos všech dat.

## Krok 5: Zkopírujte makra VBA ze šablony
Dále zkopírujeme makra VBA, včetně modulů UserForm Designer, do nového sešitu:

```csharp
// Zkopírujte UserForm VBA-Macro Designer ze šablony do cíle
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Zkopírujte kód modulu ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Zkopírujte kód a data ostatních modulů
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Získejte úložiště návrháře uživatelských formulářů
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Přidejte úložiště návrháře do cílového projektu Vba
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Tento kód zajišťuje, že se zkopíruje nejen kód, ale také návrh uživatelského formuláře, čímž se zachová funkčnost vašich maker.

## Krok 6: Uložte cílový sešit
Po dokončení procesu kopírování uložte nový sešit:

```csharp
// Uložte cílový sešit
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Podle potřeby upravte název výstupního souboru. Tento krok vytvoří váš přizpůsobený sešit plný maker a uživatelských formulářů.

## Krok 7: Potvrďte úspěch
Nakonec vytiskněte zprávu o úspěchu do konzole:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Tento jednoduchý řádek vás ujišťuje, že váš proces proběhl hladce – zásadní potvrzení vaší tvrdé práce!

## Závěr
Gratuluji! Úspěšně jste se naučili, jak kopírovat VBA Macro User Form Designer z jednoho sešitu do druhého pomocí Aspose.Cells for .NET. I když se to na první pohled může zdát skličující, díky praxi budete v manipulaci se sešitem zdatní. Pamatujte, že kódování je o experimentování, takže neváhejte prozkoumat různé funkce v souborech aplikace Excel. Pokud máte nějaké dotazy nebo potřebujete pomoc, fóra a dokumentace Aspose jsou skvělými zdroji podpory.

## FAQ

### Jaké verze aplikace Excel podporuje Aspose.Cells?
Aspose.Cells podporuje různé formáty Excelu, včetně XLSX, XLSM, CSV a dalších.

### Mohu používat Aspose.Cells zdarma?
 Ano! Můžete začít s bezplatnou zkušební verzí knihovny:[Bezplatná zkušební verze](https://releases.aspose.com/).

### Potřebuji ke spuštění tohoto kódu Visual Studio?
Zatímco Visual Studio je doporučeno pro jeho uživatelsky přívětivé funkce, postačí jakékoli C# IDE, které podporuje vývoj .NET.

### Kde najdu další příklady a dokumentaci?
 Můžete prozkoumat[Dokumentace Aspose.Cells](https://reference.aspose.com/cells/net/) pro více příkladů a podrobných vysvětlení.

### Jak vyřeším problémy při používání Aspose.Cells?
 Měli byste navštívit[Aspose Support Forum](https://forum.aspose.com/c/cells/9) za pomoc od komunity a podpůrného personálu Aspose.