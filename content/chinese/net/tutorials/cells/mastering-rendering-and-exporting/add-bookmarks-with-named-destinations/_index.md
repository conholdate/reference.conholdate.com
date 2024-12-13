---
title: 在 Excel 文件的 PDF 中添加带有命名目标的书签
linktitle: 在 Excel 文件的 PDF 中添加带有命名目标的书签
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何使用 Aspose.Cells for .NET 轻松地从 Excel 文件创建交互式 PDF。本教程介绍如何添加带有命名目标的书签以增强 PDF 导航。
type: docs
weight: 10
url: /zh/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## 介绍

浏览大型 PDF 文件通常感觉像大海捞针，尤其是当它们是由大量 Excel 电子表格生成时。PDF 文档中的书签提供了一种在文件相关部分之间无缝跳转的方式，从而增强了用户体验。本详细指南将引导您完成使用 Aspose.Cells for .NET 将带有命名目标的书签添加到由 Excel 文件生成的 PDF 的过程。

## 使用 Aspose.Cells for .NET 的先决条件

在深入研究代码之前，必须确保已设置好所有工具，以便成功实施。以下是先决条件：

1. Visual Studio：推荐用于 .NET 开发的 IDE。请确保它已在您的系统上安装并正确配置。
2.  Aspose.Cells for .NET：以编程方式操作 Excel 文件所需的核心库。您可以[点击下载](https://releases.aspose.com/cells/net/)。如果您是 Aspose 新手，可以从[免费试用](https://releases.aspose.com/).
3. .NET Framework：确保您使用的是兼容版本的 .NET Framework。Aspose.Cells 支持多个版本。
4. 基本 C# 知识：对 C# 的基本了解将有助于理解代码。

有了这些组件，您就可以开始创建带有书签的 PDF 文档了！

## 设置你的项目

一旦您的开发环境准备就绪，您就可以继续在 Visual Studio 中创建一个新的 C# 项目。为了使用 Aspose.Cells 功能，您需要导入所需的命名空间。

## 导入所需的命名空间

在 C# 文件的顶部添加以下内容`using`语句以确保您的项目可以访问 Aspose.Cells for .NET：

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

这些命名空间提供对基本类的访问，可帮助您操作 Excel 数据并将其转换为 PDF。

## 步骤 1：设置输入和输出文件的目录

第一步是定义输入和输出文件目录。这可确保源 Excel 文件和生成的 PDF 文件位于正确的位置。

```csharp
string sourceDir = "Your Document Directory";  // Excel 文件的路径
string outputDir = "Your Document Directory"; //输出 PDF 的保存路径
```

这类似于在开始一个项目之前组织您的工作空间。

## 步骤 2：加载 Excel 工作簿

下一步是加载源 Excel 文件。Aspose.Cells 允许您轻松地将 Excel 文件加载到`Workbook`对象，提供对其所有工作表、单元格和内容的访问。

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

这将打开工作簿并准备进行操作。您现在可以开始提取数据并将其格式化为 PDF。

## 步骤 3：访问工作表

现在工作簿已加载，是时候访问书签相关单元格所在的工作表了。在此示例中，我们将使用第一个工作表：

```csharp
Worksheet ws = wb.Worksheets[0]; //访问第一个工作表
```

此步骤为您的书签建立了画布。书签所引用的每个单元格都将来自此工作表。

## 步骤 4：创建带有命名目标的书签

此时，我们可以开始创建书签。书签本质上是提供快速访问文档特定区域的链接。在此示例中，我们将为单元格“C5”创建书签。

### 为单个单元格创建书签

要创建书签，您必须先访问要链接到的单元格。之后，您将创建一个`PdfBookmarkEntry`并将其与细胞的位置联系起来。

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; //书签的文字
bookmarkEntry.Destination = cell;  //将书签链接到单元格
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; //唯一目的地名称
```

可以将其视为在文档中标记一个点，单击即可返回。您可以将任何文本指定为书签（例如“C5 书签”）并将其链接到特定单元格。

### 添加子书签以增强导航

您可以通过添加从主书签分支出来的子书签来增强用户体验。这些子书签可以指向同一工作表中的不同区域或其他工作表。

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; //第一个子书签的文本
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; //第二个子书签的文本
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

这些子书签充当了浏览文档的附加路标，就像书中的章节一样。

### 将子书签分组到主书签下

为了创建层次结构，您可以在主书签下添加这些子书签。这让用户更容易导航到不同的部分。

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; //向主书签添加子书签
```

这会创建一个树状结构，其中每个书签可以有多个子书签。

## 步骤 5：使用书签保存 PDF

### 设置 PDF 保存选项

在将文档保存为 PDF 之前，我们需要指定保存选项并确保包含书签。我们将使用`PdfSaveOptions`为了这个目的。

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  //将书签分配给 PDF
```

这告诉 Aspose.Cells 生成一个包含我们刚刚创建的书签的 PDF。

### 保存文档

现在已经设置了书签，我们可以将工作簿保存为 PDF。

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

这将生成带有可点击书签的最终 PDF，允许用户快速跳转到文档的特定部分。

## 结论

通过遵循这些简单的步骤，您已成功使用 Aspose.Cells for .NET 从 Excel 文件创建了带有书签和命名目标的 PDF。添加书签的功能不仅可以增强用户体验，还可以使大型文档中的导航更加高效。无论您是在处理报告、指南还是演示文稿，为关键部分添加书签都将有助于您的读者充分利用您的文档。

## 常见问题解答

### 什么是 Aspose.Cells for .NET？
Aspose.Cells for .NET 是一个功能强大的用于处理 Excel 文件的 API，可让您以编程方式创建、编辑和转换 Excel 文档。您可以使用此工具轻松处理数据、图表和格式。

### 如何获得 Aspose.Cells for .NET 的免费试用版？
您可以从以下网址下载 Aspose.Cells for .NET 的免费试用版[这里](https://releases.aspose.com/).

### Aspose.Cells 可以处理哪些文件格式？
Aspose.Cells 支持多种文件格式，包括 XLSX、XLS、CSV、PDF 等。

### 我可以自动创建 PDF 书签吗？
是的！通过在您的应用程序中集成 Aspose.Cells，该过程可以完全自动化，允许您在工作流程中动态生成带有书签的基于 Excel 的 PDF。

### 在哪里可以获得 Aspose.Cells for .NET 的支持？
您可以访问[Aspose 论坛](https://forum.aspose.com/c/cells/9)提出问题或报告问题。