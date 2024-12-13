---
title: 查找 XLS 和 XLSX 格式的最大行数和列数
linktitle: 查找 XLS 和 XLSX 格式的最大行数和列数
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何利用 Aspose.Cells for .NET 库高效管理 Excel 中的大型数据集。本指南提供了分步方法来确定 XLS 和 XLSX 文件格式支持的最大行数和列数。
type: docs
weight: 11
url: /zh/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## 介绍

在 Excel 中管理大型数据集可能具有挑战性，尤其是考虑到各种文件格式的限制。本教程将指导您使用 Aspose.Cells for .NET 库来确定 XLS（Excel 97-2003）和 XLSX（Excel 2007 及更高版本）格式支持的最大行数和列数。最后，您将能够有效地处理与 Excel 相关的任务。

## 先决条件

开始之前，请确保您已准备好以下物品：

1. [.NET 框架](https://dotnet.microsoft.com/en-us/download)或者[.NET 核心](https://dotnet.microsoft.com/en-us/download)安装在您的系统上。
2. [用于.NET的Aspose.Cells](https://releases.aspose.com/cells/net/)下载并引用到你的项目中的库（你也可以通过[NuGet](https://www.nuget.org/packages/Aspose.Cells/)）。

## 导入所需包

在 C# 文件顶部添加以下使用语句，从 Aspose.Cells 库导入必要的包：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 步骤 1：XLS 格式的最大行数和列数

让我们首先找出 XLS 格式支持的最大行数和列数。

```csharp
//打印有关 XLS 格式的消息。
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

//创建 XLS 格式的工作簿。
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

//检索最大行数和列数。
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

//显示结果。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. 打印一条消息以表明我们正在使用 XLS 格式。
2. 创建一个`Workbook` XLS 格式的实例使用`FileFormatType.Excel97To2003`.
3. 获取最大行数和列数`wb.Settings.MaxRow`和`wb.Settings.MaxColumn`，由于这些是从零开始的，所以加 1。
4. 将最大行数和最大列数输出到控制台。

## 步骤 2：XLSX 格式的最大行数和列数

接下来，我们将探讨 XLSX 格式支持的最大行数和列数。

```csharp
//打印有关 XLSX 格式的消息。
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

//创建 XLSX 格式的工作簿。
wb = new Workbook(FileFormatType.Xlsx);

//检索最大行数和列数。
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

//显示结果。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. 打印一条消息，表明我们正在使用 XLSX 格式。
2. 创建一个`Workbook` XLSX 格式的实例使用`FileFormatType.Xlsx`.
3. 像以前一样检索并输出最大行数和列数。

## 步骤 3：显示成功消息

执行完步骤之后我们就可以看到成功了。

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## 结论

在本教程中，您学习了如何使用 Aspose.Cells for .NET 库来查找 XLS 和 XLSX 文件格式支持的最大行数和列数。了解这些限制对于有效的 Excel 数据管理至关重要，可确保您的数据集符合格式功能。

## 常见问题解答

### XLS 格式支持的最大行数是多少？
XLS 格式支持的最大行数为 65,536。

### XLS 格式支持的最大列数是多少？
XLS 格式支持的最大列数为 256。

### XLSX 格式支持的最大行数是多少？
XLSX 格式支持的最大行数为 1,048,576。

### XLSX 格式支持的最大列数是多少？
XLSX 格式支持的最大列数为 16,384。

### 我可以将 Aspose.Cells for .NET 库与其他 Excel 文件格式一起使用吗？
是的，Aspose.Cells for .NET 支持多种文件格式，包括 XLS、XLSX、ODS 等。检查[文档](https://reference.aspose.com/cells/net/)了解所支持的特性和功能的详细信息。