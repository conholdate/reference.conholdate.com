---
title: 使用 Aspose.Words for .NET 在 Word 文档中创建书签
linktitle: 使用 Aspose.Words for .NET 在 Word 文档中创建书签
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 创建和管理书签来增强您的 Word 文档。这是分步教程指南。
type: docs
weight: 10
url: /zh/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## 介绍

浏览大型文档可能具有挑战性，但书签使它变得轻而易举！本教程将指导您使用 Aspose.Words for .NET 在 Word 文档中创建书签。您将逐步学习如何设置文档、添加书签并将其保存为 PDF。让我们开始吧！

## 先决条件

在深入研究之前，请确保您已准备好以下事项：

1.  Aspose.Words for .NET Library：从以下网址下载并安装[这里](https://releases.aspose.com/words/net/).
2. 开发环境：使用 Visual Studio 或任何与 .NET 兼容的 IDE。
3. 基本 C# 知识：熟悉 C# 编程概念将会有所帮助。

## 导入命名空间

首先，导入使用 Aspose.Words 所需的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：设置文档和 DocumentBuilder

创建新文档并初始化`DocumentBuilder`，您可以添加内容和书签。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 2：创建主书签

要创建书签，您需要指定其起点和终点。以下是创建名为“我的书签”的书签的方法：

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`：标记书签的开始。
- `Writeln`：在书签内添加文本。

## 步骤 3：创建嵌套书签

您可以嵌套书签以便更好地组织。以下是在“我的书签”中添加“嵌套书签”的方法：

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- 嵌套允许您创建层次结构。 
- `EndBookmark`：关闭当前书签。

## 步骤 4：在嵌套书签外添加文本

创建嵌套书签后，继续在主书签中添加内容：

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
这可确保主书签包含嵌套书签和任何附加文本。

## 步骤 5：配置 PDF 保存选项

要在 PDF 中包含书签，请配置保存选项：

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`：定义如何将文档保存为 PDF。
- `BookmarksOutlineLevels`：设置 PDF 中书签的层次结构。

## 步骤 6：保存文档

最后，将文档保存为 PDF：

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
这`Save`方法以指定的格式和位置保存文档，并附带书签。

## 结论

使用 Aspose.Words for .NET 在 Word 文档中创建书签非常简单，而且可以增强文档导航。无论您是生成报告、电子书还是管理大量文档，书签都是无价之宝。按照本教程操作，您将立即拥有一个组织良好、带有书签的 PDF！

## 常见问题解答

### 我可以创建多个不同级别的书签吗？
是的！您可以创建多个书签并在保存为 PDF 时定义其层次结构。

### 如何更新书签的文字？
使用`DocumentBuilder.MoveToBookmark`导航至书签并更新文本。

### 可以删除书签吗？
当然可以！使用`Bookmarks.Remove`方法通过指定书签的名称。

### 除了 PDF，我还可以创建其他格式的书签吗？
是的，Aspose.Words 支持 DOCX、HTML 和 EPUB 等格式的书签。

### 如何确保书签在 PDF 中正确显示？
定义`BookmarksOutlineLevels`正确地`PdfSaveOptions`确保书签包含在 PDF 大纲中。