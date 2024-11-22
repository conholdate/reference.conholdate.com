---
title: Filtrowanie zadań i operacja w Aspose.Tasks
linktitle: Filtrowanie zadań i operacja w Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Dowiedz się, jak wykorzystać klasę w Aspose.Tasks dla .NET do filtrowania zadań projektu na podstawie wielu warunków. Łącząc kryteria, takie jak zadania podsumowujące i atrybuty inne niż null.
type: docs
weight: 10
url: /pl/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Wstęp

 tym samouczku pokażemy, jak wykonywać zaawansowane filtrowanie zadań projektu w Aspose.Tasks dla .NET, wykorzystując`Util.And` Klasa. Ta potężna funkcja pozwala deweloperom filtrować zadania na podstawie wielu kryteriów w sposób efektywny.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Podstawowa znajomość programowania w języku C#.
2.  Aspose.Tasks dla .NET zainstalowany. Jeśli jeszcze tego nie zrobiłeś, możesz pobrać go z[ten link](https://releases.aspose.com/tasks/net/).
3. Zintegrowane środowisko programistyczne (IDE), takie jak Visual Studio, służące do pisania i uruchamiania kodu.

## Importowanie przestrzeni nazw

Aby rozpocząć, musisz zaimportować wymagane przestrzenie nazw do swojego projektu C#. Umożliwi ci to dostęp do funkcjonalności udostępnianych przez Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Krok 1: Zainicjuj projekt i zbierz zadania

 Najpierw zainicjuj projekt Aspose.Tasks i zbierz wszystkie zadania w nim zawarte. W celach demonstracyjnych załóżmy, że istnieje plik projektu o nazwie`Project2.mpp`.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Zbierz wszystkie zadania podrzędne
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Krok 2: Zdefiniuj warunki filtrowania

tym kroku zdefiniujemy warunki filtrowania zadań. W naszym przykładzie utworzymy dwa warunki: jeden do filtrowania zadań podsumowujących i drugi, aby upewnić się, że zadania nie są nullem.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Krok 3: Połącz warunki za pomocą operacji AND

 Następnym krokiem jest połączenie tych warunków za pomocą`Util.And` klasa. Pozwala nam to stworzyć złożony warunek, który wymaga obu kryteriów.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Krok 4: Zastosuj połączony warunek i zadania filtrowania

Teraz zastosujmy połączony warunek do zebranych zadań, aby odfiltrować konkretne zadania spełniające oba warunki.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Krok 5: Wyjście odfiltrowanych zadań

Na koniec przejdziemy przez nasze odfiltrowane zadania i wyprowadzimy odpowiednie szczegóły. Pomoże nam to zrozumieć zadania, które spełniają nasze kryteria.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Wniosek

 W tym samouczku pokazaliśmy, jak wykonywać zaawansowane operacje filtrowania w Aspose.Tasks dla .NET przy użyciu`Util.And`klasa. Łącząc wiele warunków, możemy skutecznie filtrować zadania, zwiększając w ten sposób użyteczność naszych aplikacji do zarządzania projektami.

## Najczęściej zadawane pytania

### Czym jest Aspose.Tasks dla .NET?

Aspose.Tasks for .NET to wszechstronny interfejs API przeznaczony dla programistów, który umożliwia programistyczne manipulowanie plikami Microsoft Project w aplikacjach .NET.

### Czy mogę łączyć więcej niż dwa warunki za pomocą Util.And?

 Tak!`Util.And` Klasa ta umożliwia łączenie wielu warunków, umożliwiając złożoną logikę filtrowania dostosowaną do Twoich potrzeb.

### Czy jest dostępna bezpłatna wersja próbna Aspose.Tasks?

 Tak, możesz pobrać bezpłatną wersję próbną ze strony[ten link](https://releases.aspose.com/).

### Gdzie mogę znaleźć szczegółową dokumentację Aspose.Tasks?

 Dostępna jest szczegółowa dokumentacja[Tutaj](https://reference.aspose.com/tasks/net/).

### Gdzie mogę uzyskać pomoc dotyczącą Aspose.Tasks?

 Pomoc jest dostępna za pośrednictwem forum społeczności Aspose.Tasks, do którego można uzyskać dostęp[Tutaj](https://forum.aspose.com/c/tasks/15).