---
title: 使用 Aspose.Cells for .NET 在 Excel 工作簿中复制数据
linktitle: 使用 Aspose.Cells for .NET 在 Excel 工作簿中复制数据
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何使用 Aspose.Cells for .NET 在 Excel 工作簿中高效复制数据。按照此分步指南，轻松复制工作表、传输数据和管理 Excel 文件。
type: docs
weight: 12
url: /zh/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## 介绍

在本详细指南中，我们将演示如何使用 Aspose.Cells for .NET 在同一工作簿内复制数据。通过遵循下面概述的分步说明，您将学习如何以编程方式复制工作表，并保留其内容和格式。

## 使用 Aspose.Cells 在 Excel 中复制数据的先决条件

在深入编码过程之前，请确保一切准备就绪：

1. Aspose.Cells for .NET 库：您需要安装 Aspose.Cells for .NET 库。您可以从[Aspose.Cells for .NET 下载页面](https://releases.aspose.com/cells/net/).
2. 开发环境：编写和运行代码需要与 .NET 兼容的 IDE（例如 Visual Studio）。
3.  Aspose 许可证：您可以使用免费试用版或购买许可证。有关更多信息，请访问[这里](https://purchase.aspose.com/temporary-license/).

一旦设置了先决条件，您就可以开始使用该库了。

## 导入所需包

首先，您需要从 Aspose.Cells 导入相关的命名空间。这样您就可以使用 Aspose.Cells 提供的类和方法处理 Excel 文件。

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

这些命名空间将允许你访问`Workbook`类（用于处理 Excel 文件）和`WorksheetCollection`（用于访问工作簿中的多张工作表）。

## 步骤 1：初始化工作簿的文件路径

为了使代码井然有序，必须定义工作簿所在的文件路径以及要保存修改后的文件的位置。指定路径的方法如下：

```csharp
//定义Excel文件所在的目录路径。
string dataDir = "Your Directory Path";

//定义输入工作簿的完整路径。
string inputPath = dataDir + "book1.xls";
```

代替`"Your Directory Path"`替换为包含工作簿的目录的实际路径。这有助于确保代码灵活，并且您可以有效地管理路径。

## 步骤 2：打开工作簿以访问数据

现在文件路径已设置，下一步是将 Excel 工作簿加载到`Workbook`对象。这允许您访问其内容并进行操作。

```csharp
//将 Excel 文件加载到 Workbook 对象中。
Workbook wb = new Workbook(inputPath);
```

通过此行，您已成功加载`book1.xls`进入`wb`对象，使其数据可访问。

## 步骤 3：访问工作表集合

工作簿加载后，您可以访问其中包含的工作表。 Aspose.Cells 提供`Worksheets`集合，它允许您与工作簿中的每个工作表进行交互。

```csharp
//从工作簿中检索工作表集合。
WorksheetCollection sheets = wb.Worksheets;
```

这`sheets`对象现在允许您访问其中的所有工作表`book1.xls`，并且您可以对其执行各种操作，包括将数据从一张表复制到另一张表。

## 步骤 4：将数据从一张表复制到另一张表

要将数据从一个工作表复制到同一工作簿中的另一个工作表，Aspose.Cells 提供了一种易于使用的方法，称为`AddCopy`.此方法创建指定工作表的副本并将其附加到工作簿。

```csharp
//将数据从“Sheet1”复制到工作簿内的新工作表。
sheets.AddCopy("Sheet1");
```

在此示例中，我们将数据从“Sheet1”复制到新工作表。`AddCopy`方法将复制整个工作表，保留其所有内容，包括公式、格式和值。

## 步骤 5：保存修改的工作簿

复制数据后，您可以使用新名称或位置保存修改后的工作簿。这可以通过调用`Save`方法`Workbook`目的。

```csharp
//使用新名称保存修改后的工作簿。
wb.Save(dataDir + "book1_copy.xls");
```

这会将工作簿和复制的工作表保存为`book1_copy.xls`在指定的目录中。您可以根据需要更改文件名和路径。

## 结论

使用 Aspose.Cells for .NET 在 Excel 工作簿中复制数据是一项简单的任务，本指南提供了高效执行此操作所需的步骤。无论您是复制整个工作表还是特定数据范围，Aspose.Cells 都提供了强大而灵活的 API，使 Excel 自动化变得简单而有效。

## 常见问题解答

### 我可以一次复印多张纸吗？

Aspose.Cells 不支持在一次调用中复制多个工作表。但是，您可以循环遍历要复制的工作表并单独复制它们。

### 我如何重命名复制的工作表？

复制工作表后，您可以按如下方式重命名它：

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells 与 .NET Core 兼容吗？

是的，Aspose.Cells 与 .NET Framework 和 .NET Core 环境完全兼容。

### Aspose.Cells 如何在复制过程中处理格式？

这`AddCopy`该方法在复制工作表时保留所有内容和格式，确保复制的数据与原始数据完全相同。

### 我可以将工作表复制到不同的工作簿吗？

是的，您可以使用`Copy`方法并引用目标工作簿。

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```