---
title: Filtrování úloh A operace v Aspose.Tasks
linktitle: Filtrování úloh A operace v Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Naučte se, jak využít třídu v Aspose.Tasks pro .NET k filtrování projektových úkolů na základě více podmínek. Kombinací kritérií, jako jsou souhrnné úkoly a nenulové atributy.
type: docs
weight: 10
url: /cs/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Zavedení

 tomto tutoriálu prozkoumáme, jak provádět pokročilé filtrování projektových úkolů v Aspose.Tasks for .NET pomocí`Util.And` třída. Tato výkonná funkce umožňuje vývojářům efektivně filtrovat úkoly na základě více kritérií.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Základní znalost programování v C#.
2.  Aspose.Tasks for .NET nainstalován. Pokud jste to ještě neudělali, můžete si to stáhnout z[tento odkaz](https://releases.aspose.com/tasks/net/).
3. Integrované vývojové prostředí (IDE), jako je Visual Studio, pro psaní a spouštění kódu.

## Import jmenných prostorů

Chcete-li začít, musíte do svého projektu C# importovat požadované jmenné prostory. To vám umožní přístup k funkcím poskytovaným Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Krok 1: Inicializujte projekt a shromážděte úkoly

 Nejprve inicializujte projekt Aspose.Tasks a shromážděte v něm všechny úkoly. Pro demonstrační účely budeme předpokládat, že existuje soubor projektu s názvem`Project2.mpp`.

```csharp
// Cesta k adresáři dokumentů
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Sbírejte všechny dětské úkoly
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Krok 2: Definujte podmínky filtru

tomto kroku definujeme podmínky pro filtrování úloh. V našem příkladu vytvoříme dvě podmínky: jednu pro filtrování souhrnných úkolů a druhou pro zajištění, že úkoly nebudou null.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Krok 3: Zkombinujte podmínky s operací AND

 Dalším krokem je zkombinovat tyto podmínky pomocí`Util.And` třída. To nám umožňuje vytvořit složenou podmínku, která vyžaduje obě kritéria.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Krok 4: Aplikujte úkoly kombinované podmínky a filtru

Nyní aplikujme kombinovanou podmínku na shromážděné úkoly, abychom odfiltrovali konkrétní úkoly, které splňují obě podmínky.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Krok 5: Výstup filtrovaných úloh

Nakonec projdeme naše filtrované úkoly a vydáme příslušné podrobnosti. To nám pomůže pochopit úkoly, které splňují naše kritéria.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Závěr

 V tomto tutoriálu jsme ukázali, jak provádět pokročilé operace filtrování v Aspose.Tasks pro .NET pomocí`Util.And`třída. Kombinací více podmínek můžeme efektivně filtrovat úkoly, a tím zvýšit užitečnost našich aplikací pro řízení projektů.

## FAQ

### Co je Aspose.Tasks pro .NET?

Aspose.Tasks for .NET je komplexní API určené pro vývojáře k programové manipulaci se soubory Microsoft Project v rámci aplikací .NET.

### Mohu pomocí Util.And kombinovat více než dvě podmínky?

 Ano! The`Util.And` třída umožňuje kombinovat více podmínek, což umožňuje komplexní logiku filtrování přizpůsobenou vašim potřebám.

### Je k dispozici bezplatná zkušební verze pro Aspose.Tasks?

 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tento odkaz](https://releases.aspose.com/).

### Kde najdu podrobnou dokumentaci k Aspose.Tasks?

 K dispozici je podrobná dokumentace[zde](https://reference.aspose.com/tasks/net/).

### Jak mohu vyhledat podporu pro Aspose.Tasks?

 Podpora je dostupná prostřednictvím komunitního fóra Aspose.Tasks, které je přístupné[zde](https://forum.aspose.com/c/tasks/15).