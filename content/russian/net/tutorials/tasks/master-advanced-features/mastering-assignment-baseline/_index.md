---
title: Освоение базовых показателей заданий с помощью Aspose.Tasks для .NET
linktitle: Управление базовым планом заданий в Aspose.Tasks
second_title: API Aspose.Tasks .NET
description: Узнайте, как эффективно управлять базовыми планами назначений с помощью Aspose.Tasks для .NET. Это пошаговое руководство охватывает загрузку проектов, установку базовых планов, извлечение данных, сравнение базовых планов и многое другое для оптимизации рабочих процессов управления проектами.
type: docs
weight: 14
url: /ru/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## Введение

Эффективное управление проектами зависит от точного отслеживания и управления базовыми планами назначений. С Aspose.Tasks для .NET вы получаете надежный инструментарий для оптимизации обработки базовых планов назначений для лучшего понимания проекта. В этой статье мы проведем вас через процесс управления базовыми планами назначений, гарантируя, что ваши проекты будут идти по плану.

## Предпосылки

Прежде чем приступить к реализации, убедитесь, что у вас есть следующее:

- Опыт программирования: базовые знания C#.
- Среда разработки: установленная и настроенная Visual Studio.
-  Библиотека Aspose.Tasks для .NET: загрузите ее с сайта[Релизы Aspose.Tasks](https://releases.aspose.com/tasks/net/).
- Файл проекта: доступ к файлу проекта в формате MPP.

## Импорт требуемых пространств имен

Чтобы использовать функциональность Aspose.Tasks, включите в файл проекта следующие пространства имен:

```csharp
using Aspose.Tasks;
using System;
```

## Шаг 1: Загрузите проект и установите базовые показатели

Загрузка проекта и установка базовой линии являются основополагающими для управления базовыми линиями назначения. Следующий код демонстрирует, как загрузить проект и установить его базовую линию.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// Установление исходного уровня проекта
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## Шаг 2: Извлечение базовых данных по назначению

Вы можете извлечь подробную базовую информацию для каждого назначения ресурсов. Вот как это сделать:

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

## Шаг 3: Сравните исходные данные между заданиями

Aspose.Tasks позволяет программно сравнивать базовые показатели для оценки различий между назначениями ресурсов.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## Шаг 4: Программное изменение базовых данных

Вы можете программно изменять исходные данные в соответствии с меняющимися потребностями проекта:

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // Корректировка базовой стоимости
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // Добавление рабочих часов

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## Заключение

Эффективное управление базовыми планами заданий является неотъемлемой частью поддержания контроля над графиками и бюджетами проектов. Aspose.Tasks для .NET предоставляет вам необходимые инструменты для точной обработки базовых планов, позволяя принимать решения на основе данных.

## Часто задаваемые вопросы

### Может ли Aspose.Tasks обрабатывать несколько базовых планов для одного проекта?  
Да, Aspose.Tasks поддерживает несколько базовых планов, обеспечивая гибкость в отслеживании различных версий проекта.

### Совместим ли Aspose.Tasks с файлами проектов, отличными от MPP?  
Безусловно. Aspose.Tasks поддерживает такие форматы, как XML, MPX и другие.

### Могу ли я автоматизировать базовые обновления?  
Да, API позволяет программно вносить динамические и автоматизированные изменения в базовые данные.

### Предоставляет ли Aspose.Tasks базовые данные, привязанные к определенному времени?  
Да, можно получить и проанализировать подробные базовые данные, распределенные по времени.

### Где я могу получить доступ к поддержке и документации?  
 Посещать[Документация Aspose.Tasks](https://reference.aspose.com/words/net/)или присоединяйтесь к[Форум поддержки Aspose](https://forum.aspose.com/c/words/8) за помощь. 