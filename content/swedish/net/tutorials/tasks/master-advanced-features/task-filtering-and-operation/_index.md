---
title: Uppgiftsfiltrering OCH drift i Aspose.Tasks
linktitle: Uppgiftsfiltrering OCH drift i Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Lär dig hur du använder klassen i Aspose.Tasks för .NET för att filtrera projektuppgifter baserat på flera villkor. Genom att kombinera kriterier som sammanfattande uppgifter och icke-nullattribut.
type: docs
weight: 10
url: /sv/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Introduktion

 den här handledningen kommer vi att utforska hur man utför avancerad filtrering av projektuppgifter i Aspose.Tasks för .NET genom att använda`Util.And` klass. Denna kraftfulla funktion tillåter utvecklare att effektivt filtrera uppgifter baserat på flera kriterier.

## Förutsättningar

Innan vi börjar, se till att du har följande:

1. Grundläggande kunskaper i C#-programmering.
2.  Aspose.Tasks för .NET installerat. Om du inte har gjort det ännu kan du ladda ner det från[denna länk](https://releases.aspose.com/tasks/net/).
3. En integrerad utvecklingsmiljö (IDE) som Visual Studio för att skriva och köra koden.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden till ditt C#-projekt. Detta ger dig tillgång till funktionerna som tillhandahålls av Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Steg 1: Initiera projektet och samla in uppgifter

 Initiera först ett Aspose.Tasks-projekt och samla alla uppgifter inom det. För demonstrationsändamål antar vi att det finns en projektfil med namnet`Project2.mpp`.

```csharp
// Sökväg till dokumentkatalogen
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Samla alla barnuppgifter
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Steg 2: Definiera filtervillkor

det här steget kommer vi att definiera villkoren för filtreringsuppgifter. I vårt exempel kommer vi att skapa två villkor: ett för att filtrera för sammanfattningsuppgifter och ett annat för att säkerställa att uppgifter inte är null.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Steg 3: Kombinera villkor med AND-operationen

 Nästa steg är att kombinera dessa villkor med hjälp av`Util.And` klass. Detta gör att vi kan skapa ett sammansatt villkor som kräver båda kriterierna.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Steg 4: Tillämpa de kombinerade villkoren och filteruppgifterna

Låt oss nu tillämpa det kombinerade villkoret på de insamlade uppgifterna för att filtrera bort de specifika uppgifterna som uppfyller båda villkoren.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Steg 5: Skriv ut de filtrerade uppgifterna

Slutligen kommer vi att upprepa våra filtrerade uppgifter och mata ut relevanta detaljer. Detta kommer att hjälpa oss att förstå de uppgifter som uppfyller våra kriterier.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Slutsats

 I den här handledningen demonstrerade vi hur man utför avancerade filtreringsoperationer i Aspose.Tasks för .NET med hjälp av`Util.And`klass. Genom att kombinera flera villkor kan vi effektivt filtrera uppgifter och därigenom förbättra användbarheten av våra projektledningsapplikationer.

## FAQ's

### Vad är Aspose.Tasks för .NET?

Aspose.Tasks för .NET är ett omfattande API designat för utvecklare att manipulera Microsoft Project-filer programmatiskt i .NET-applikationer.

### Kan jag kombinera mer än två villkor med Util.And?

 Ja! De`Util.And` klass låter dig kombinera flera villkor, vilket möjliggör komplex filtreringslogik anpassad efter dina behov.

### Finns det en gratis testversion tillgänglig för Aspose.Tasks?

 Ja, du kan ladda ner en gratis testversion från[denna länk](https://releases.aspose.com/).

### Var kan jag hitta detaljerad dokumentation för Aspose.Tasks?

 Detaljerad dokumentation finns tillgänglig[här](https://reference.aspose.com/tasks/net/).

### Hur kan jag söka stöd för Aspose.Tasks?

 Support är tillgängligt via Aspose.Tasks community-forum, som kan nås[här](https://forum.aspose.com/c/tasks/15).