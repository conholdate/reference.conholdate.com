---
title: Aspose.Tasks 中的任务过滤与操作
linktitle: Aspose.Tasks 中的任务过滤与操作
second_title: Aspose.Tasks .NET API
description: 了解如何利用 Aspose.Tasks for .NET 中的类根据多种条件过滤项目任务。通过组合诸如摘要任务和非空属性等条件。
type: docs
weight: 10
url: /zh/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## 介绍

在本教程中，我们将探索如何利用 Aspose.Tasks for .NET 中的`Util.And`类。这个强大的功能允许开发人员根据多个标准高效地过滤任务。

## 先决条件

在开始之前，请确保您已准备好以下物品：

1. C# 编程的基本知识。
2. 已安装 Aspose.Tasks for .NET。如果你还没有安装，可以从以下位置下载[此链接](https://releases.aspose.com/tasks/net/).
3. 像 Visual Studio 这样的集成开发环境 (IDE)，用于编写和运行代码。

## 导入命名空间

首先，您需要将所需的命名空间导入到您的 C# 项目中。这将允许您访问 Aspose.Tasks 提供的功能。

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## 步骤 1：初始化项目并收集任务

首先，初始化一个 Aspose.Tasks 项目并收集其中的所有任务。为了演示目的，我们假设有一个名为的项目文件`Project2.mpp`.

```csharp
//文档目录的路径
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

//收集所有子任务
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## 第 2 步：定义过滤条件

在此步骤中，我们将定义过滤任务的条件。在我们的示例中，我们将创建两个条件：一个用于过滤摘要任务，另一个用于确保任务不为空。

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## 步骤 3：使用 AND 运算组合条件

下一步是利用`Util.And`类。这样我们就可以创建一个同时满足两个条件的复合条件。

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## 步骤 4：应用组合条件和筛选任务

现在，让我们将组合条件应用到收集到的任务上，筛选出同时满足两个条件的特定任务。

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## 步骤5：输出过滤后的任务

最后，我们将遍历已筛选的任务并输出相关详细信息。这将帮助我们了解符合我们标准的任务。

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## 结论

在本教程中，我们演示了如何使用`Util.And`类。通过组合多个条件，我们可以有效地过滤任务，从而提高我们项目管理应用程序的实用性。

## 常见问题解答

### 什么是 Aspose.Tasks for .NET？

Aspose.Tasks for .NET 是一个全面的 API，专为开发人员在 .NET 应用程序内以编程方式操作 Microsoft Project 文件而设计。

### 我可以使用 Util.And 组合两个以上的条件吗？

是的！`Util.And`该类允许您组合多个条件，从而实现根据您的需要定制的复杂过滤逻辑。

### Aspose.Tasks 有免费试用版吗？

是的，你可以从以下网站下载免费试用版[此链接](https://releases.aspose.com/).

### 在哪里可以找到 Aspose.Tasks 的详细文档？

有详细文档可供查阅[这里](https://reference.aspose.com/tasks/net/).

### 我如何寻求对 Aspose.Tasks 的支持？

可以通过 Aspose.Tasks 社区论坛获得支持，可以访问[这里](https://forum.aspose.com/c/tasks/15).