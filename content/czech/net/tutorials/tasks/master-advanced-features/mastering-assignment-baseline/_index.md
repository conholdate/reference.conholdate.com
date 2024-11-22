---
title: Zvládnutí základních linií přiřazení pomocí Aspose.Tasks pro .NET
linktitle: Správa základního plánu přiřazení v Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Naučte se, jak efektivně spravovat základní linie přiřazení pomocí Aspose.Tasks for .NET. Tento podrobný průvodce pokrývá načítání projektů, nastavení směrných plánů, načítání dat, porovnávání směrných plánů a další pro optimalizaci pracovních postupů projektového řízení.
type: docs
weight: 14
url: /cs/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## Zavedení

Efektivní řízení projektů závisí na přesném sledování a správě výchozích linií zadání. S Aspose.Tasks for .NET získáte robustní sadu nástrojů pro zefektivnění manipulace se základními liniemi zadání pro lepší přehled o projektech. V tomto článku vás provedeme procesem správy základních linií zadání a zajistíme, že vaše projekty zůstanou na správné cestě.

## Předpoklady

Než se pustíte do implementace, ujistěte se, že máte následující:

- Znalosti programování: Základní znalost C#.
- Vývojové prostředí: Visual Studio nainstalované a nakonfigurované.
-  Aspose.Tasks for .NET Library: Stáhněte si ji z[Vydání Aspose.Tasks](https://releases.aspose.com/tasks/net/).
- Project File: Přístup k souboru projektu ve formátu MPP.

## Importujte požadované jmenné prostory

Chcete-li používat funkce Aspose.Tasks, zahrňte do souboru projektu následující jmenné prostory:

```csharp
using Aspose.Tasks;
using System;
```

## Krok 1: Načtěte projekt a nastavte základní linie

Načtení projektu a nastavení směrného plánu je základem správy směrných plánů přiřazení. Následující kód ukazuje, jak načíst projekt a vytvořit jeho směrný plán.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// Nastavení základní linie projektu
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## Krok 2: Načtěte základní data přiřazení

Pro každé přiřazení zdrojů můžete extrahovat podrobné základní informace. Jak na to:

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## Krok 3: Porovnejte základní linie mezi úkoly

Aspose.Tasks umožňuje programově porovnávat směrné plány a vyhodnocovat rozdíly mezi přiřazením zdrojů.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## Krok 4: Programově upravte podrobnosti základního plánu

Data základního plánu můžete programově upravit tak, aby vyhovovala vyvíjejícím se potřebám projektu:

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // Úprava základní ceny
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // Přidání pracovní doby

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## Závěr

Efektivní správa výchozích hodnot úkolů je nedílnou součástí udržení kontroly nad harmonogramy projektů a rozpočty. Aspose.Tasks for .NET vás vybaví nezbytnými nástroji pro přesné zpracování základních linií a umožňuje rozhodování na základě dat.

## FAQ

### Dokáže Aspose.Tasks zpracovat více směrných plánů pro jeden projekt?  
Ano, Aspose.Tasks podporuje více základních linií a poskytuje flexibilitu při sledování různých verzí projektů.

### Je Aspose.Tasks kompatibilní se soubory projektů, které nejsou MPP?  
Absolutně. Aspose.Tasks podporuje formáty jako XML, MPX a další.

### Mohu zautomatizovat základní aktualizace?  
Ano, API umožňuje programově dynamické a automatizované základní úpravy.

### Poskytuje Aspose.Tasks časově fázovaná základní data?  
Ano, lze získat a analyzovat podrobná časová základní data.

### Kde získám přístup k podpoře a dokumentaci?  
 Návštěva[Dokumentace Aspose.Tasks](https://reference.aspose.com/words/net/) nebo se připojte k[Aspose Support Forum](https://forum.aspose.com/c/words/8) o pomoc. 