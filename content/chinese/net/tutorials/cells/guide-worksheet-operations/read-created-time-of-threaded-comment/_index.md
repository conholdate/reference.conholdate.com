---
title: 使用 Aspose.Cells 读取主题评论的创建时间
linktitle: 使用 Aspose.Cells 读取主题评论的创建时间
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何使用 Aspose.Cells for .NET 轻松读取 Excel 工作表中线程注释的创建时间。按照我们的详细指南逐步说明进行操作。
type: docs
weight: 21
url: /zh/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## 介绍

使用 Excel 文件时，管理注释对于协作和反馈跟踪至关重要。在本指南中，我们将引导您完成使用 Aspose.Cells for .NET 读取 Excel 工作表中线程注释的创建时间的过程。这个强大的工具提供了一种与 Excel 文件交互的有效方法，使开发人员能够从注释中提取详细信息，这对于跟踪协作场景中的反馈时间特别有用。

## 先决条件

在开始之前，重要的是确保您的开发环境已正确设置以使用 Aspose.Cells for .NET。以下是您需要的内容：

1.  Aspose.Cells for .NET：您需要安装 Aspose.Cells 库。您可以从[Aspose 网站](https://releases.aspose.com/cells/net/).
2. IDE：Visual Studio（或您选择的任何 .NET IDE）用于编写和执行您的代码。
3. 基本 C# 知识：熟悉 C# 编程将使理解示例变得更容易。
4.  Excel 文件：在本教程中，我们将使用名为`ThreadedCommentsSample.xlsx`，其中包括一些主题评论。请确保您的文件包含要跟进的评论。

## 导入所需的包

首先，您需要导入使用 Aspose.Cells 所需的命名空间。打开您的 C# 项目并在代码文件顶部添加以下使用指令：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

这`Aspose.Cells`命名空间允许您访问操作 Excel 文件所需的所有类和方法，同时`System`是输出和异常处理等一般功能所必需的。

## 步骤 1：指定 Excel 文件的目录

第一步是定义 Excel 文件的存储路径。此路径将用于以编程方式定位文件。

```csharp
//定义Excel文件的目录
string sourceDir = "Your Document Directory";
```

代替`"C:\\YourDirectory\\"`替换为文件的实际路径。这确保程序知道在哪里找到`ThreadedCommentsSample.xlsx`.

## 步骤 2：加载工作簿

设置目录后，我们现在可以加载 Excel 工作簿。这是通过创建一个新的`Workbook`对象并将文件路径传递给它。

```csharp
//加载 Excel 工作簿
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

如果在指定路径下找不到文件，则会引发异常，因此在继续之前请确保文件路径正确。

## 步骤 3：访问所需工作表

工作簿加载完成后，您需要访问包含主题评论的工作表。在此示例中，我们将检索工作簿的第一个工作表。

```csharp
//访问工作簿中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];
```

如果您的评论位于不同的工作表中，只需相应地修改索引即可。例如，使用`Worksheets[1]`对于第二张工作表，依此类推。

## 步骤 4：检索主题评论

要检索主题评论，您需要指定包含评论的单元格。在本例中，我们重点关注单元格`A1` 方法`GetThreadedComments`用于获取与特定单元格相关的所有评论。

```csharp
//从单元格 A1 获取线索评论
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

这将返回单元格 A1 的线程评论集合。如果指定单元格中不存在评论，则集合将为空。

## 步骤 5：遍历评论并提取创建时间

检索到主题评论后，下一步是遍历集合并提取相关详细信息，包括每条评论的创建时间。我们可以通过循环遍历`ThreadedCommentCollection`.

```csharp
//循环遍历每个主题评论并显示详细信息
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

此代码将输出评论的内容、作者姓名以及评论的创建时间。`CreatedTime`属性返回评论最初创建的时间戳。

## 步骤 6：显示确认消息

成功读取主题评论并显示信息后，在代码中包含确认消息始终是一个好习惯。这有助于确认流程已正确执行。

```csharp
//确认信息
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

代码执行完成后，该消息将打印到控制台，确认过程运行没有错误。

## 结论

现在，您已经学会了如何使用 Aspose.Cells for .NET 轻松读取 Excel 工作表中线程注释的创建时间。此功能对于在协作环境中跟踪注释和反馈非常有用，可为文档审阅流程提供必要的时间戳。通过遵循本指南，您可以有效地提取和利用 .NET 应用程序中的注释数据，从而增强您的工作流程并改善与团队成员的协作。

## 常见问题解答

### 什么是 Aspose.Cells for .NET？

Aspose.Cells for .NET 是一个综合库，可帮助开发人员在 .NET 应用程序中创建、操作和管理 Excel 文件。它提供了强大的工具，用于以编程方式读取、写入和修改 Excel 文件。

### 如何下载 Aspose.Cells for .NET？

您可以从以下网址下载最新版本的 Aspose.Cells for .NET[Aspose 网站](https://releases.aspose.com/cells/net/).

### 有免费试用吗？

是的，Aspose 提供 Aspose.Cells for .NET 的免费试用版。您可以从[免费试用页面](https://releases.aspose.com/).

### 我能否访问其他单元格的评论？

是的，您可以通过修改工作表中的单元格引用来访问工作表中任意单元格的线程注释`GetThreadedComments`方法。只需更改`"A1"`到所需单元格的引用。

### 我可以在哪里获得 Aspose.Cells 的支持？

如果您需要支持或有疑问，请访问[Aspose 论坛](https://forum.aspose.com/c/cells/9)，您可以在这里找到答案或向社区寻求帮助。