---
title: Aufgabenfilterung und -Operation in Aspose.Tasks
linktitle: Aufgabenfilterung und -Operation in Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Erfahren Sie, wie Sie die Klasse in Aspose.Tasks für .NET nutzen, um Projektaufgaben basierend auf mehreren Bedingungen zu filtern. Durch die Kombination von Kriterien wie Zusammenfassungsaufgaben und Attributen ungleich Null.
type: docs
weight: 10
url: /de/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Einführung

In diesem Tutorial werden wir untersuchen, wie man eine erweiterte Filterung von Projektaufgaben in Aspose.Tasks für .NET durchführt, indem man die`Util.And` Klasse. Mit dieser leistungsstarken Funktion können Entwickler Aufgaben effizient anhand mehrerer Kriterien filtern.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Grundkenntnisse der C#-Programmierung.
2.  Aspose.Tasks für .NET installiert. Wenn Sie dies noch nicht getan haben, können Sie es hier herunterladen:[dieser Link](https://releases.aspose.com/tasks/net/).
3. Eine integrierte Entwicklungsumgebung (IDE) wie Visual Studio zum Schreiben und Ausführen des Codes.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Dadurch können Sie auf die von Aspose.Tasks bereitgestellten Funktionen zugreifen.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Schritt 1: Projekt initialisieren und Aufgaben sammeln

 Initialisieren Sie zunächst ein Aspose.Tasks-Projekt und sammeln Sie alle darin enthaltenen Aufgaben. Zu Demonstrationszwecken nehmen wir an, dass es eine Projektdatei mit dem Namen gibt`Project2.mpp`.

```csharp
// Pfad zum Dokumentenverzeichnis
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Sammeln Sie alle untergeordneten Aufgaben
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Schritt 2: Filterbedingungen definieren

In diesem Schritt definieren wir die Bedingungen zum Filtern von Aufgaben. In unserem Beispiel erstellen wir zwei Bedingungen: eine zum Filtern nach Zusammenfassungsaufgaben und eine andere, um sicherzustellen, dass Aufgaben nicht null sind.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Schritt 3: Bedingungen mit der UND-Operation verknüpfen

 Der nächste Schritt besteht darin, diese Bedingungen zu kombinieren, indem man`Util.And` Klasse. Dadurch können wir eine zusammengesetzte Bedingung erstellen, die beide Kriterien erfordert.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Schritt 4: Kombinierte Bedingung anwenden und Aufgaben filtern

Wenden wir nun die kombinierte Bedingung auf die gesammelten Aufgaben an, um die spezifischen Aufgaben herauszufiltern, die beide Bedingungen erfüllen.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Schritt 5: Ausgabe der gefilterten Aufgaben

Abschließend durchlaufen wir unsere gefilterten Aufgaben und geben relevante Details aus. Dies hilft uns dabei, die Aufgaben zu verstehen, die unseren Kriterien entsprechen.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Abschluss

 In diesem Tutorial haben wir gezeigt, wie Sie erweiterte Filtervorgänge in Aspose.Tasks für .NET mithilfe der`Util.And`Klasse. Durch die Kombination mehrerer Bedingungen können wir Aufgaben effektiv filtern und so den Nutzen unserer Projektmanagementanwendungen steigern.

## Häufig gestellte Fragen

### Was ist Aspose.Tasks für .NET?

Aspose.Tasks für .NET ist eine umfassende API, die für Entwickler entwickelt wurde, um Microsoft Project-Dateien programmgesteuert in .NET-Anwendungen zu bearbeiten.

### Kann ich mit Util.And mehr als zwei Bedingungen kombinieren?

 Ja! Die`Util.And` Die Klasse ermöglicht Ihnen die Kombination mehrerer Bedingungen und ermöglicht so eine komplexe, auf Ihre Bedürfnisse zugeschnittene Filterlogik.

### Gibt es eine kostenlose Testversion für Aspose.Tasks?

 Ja, Sie können eine kostenlose Testversion herunterladen von[dieser Link](https://releases.aspose.com/).

### Wo finde ich eine ausführliche Dokumentation für Aspose.Tasks?

 Detaillierte Dokumentation ist verfügbar[Hier](https://reference.aspose.com/tasks/net/).

### Wie kann ich Support für Aspose.Tasks beantragen?

 Support ist über das Aspose.Tasks-Community-Forum verfügbar, auf das zugegriffen werden kann[Hier](https://forum.aspose.com/c/tasks/15).