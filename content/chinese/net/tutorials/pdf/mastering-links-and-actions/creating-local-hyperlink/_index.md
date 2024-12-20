---
title: 在 PDF 文件中创建本地超链接
linktitle: 在 PDF 文件中创建本地超链接
second_title: Aspose.PDF for .NET API 参考
description: 了解如何通过使用 Aspose.PDF for .NET 创建本地超链接来改善 PDF 文档中的导航。本分步教程将引导您完成整个过程。
type: docs
weight: 40
url: /zh/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## 介绍

在本指南中，我们将引导您完成使用 Aspose.PDF for .NET 在 PDF 文件中创建本地超链接的过程。我们将清晰地分解每个步骤，确保即使您是 PDF 操作新手，也能轻松跟上。

## 先决条件

在深入研究代码之前，请确保您已具备以下条件：

1.  Visual Studio：从以下位置下载[Visual Studio 网站](https://visualstudio.microsoft.com/).
2. Aspose.PDF for .NET：通过以下网址下载该库[Aspose 网站](https://releases.aspose.com/pdf/net/).该库提供了一组丰富的PDF操作功能。
3. C# 基础知识：熟悉 C# 编程会有所帮助，但不用担心；我们会逐行解释代码。
4. .NET Framework：确保您的机器上安装了 .NET Framework。检查 Aspose.PDF 上的要求[文档](https://reference.aspose.com/pdf/net/).

有了这些先决条件，您就可以学习如何在 PDF 文档中创建本地超链接了！

## 导入所需包

现在您已完成所有设置，是时候将必要的包导入到您的 C# 项目中了。

### 打开你的项目

打开您现有的 .NET 项目或在 Visual Studio 中创建一个新项目。如果您是新开始，请从启动屏幕中选择“创建新项目”。

### 添加对 Aspose.PDF 的引用

在解决方案资源管理器中，右键单击项目文件夹中的“依赖项”。选择“管理 NuGet 包”，搜索`Aspose.PDF`，并安装最新版本。这将带来创建和操作 PDF 所需的所有工具。

### 导入命名空间

在 .cs 文件的顶部，添加以下使用指令：

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

这些指令允许您无缝访问该库的功能。

让我们将创建本地超链接的过程分解为简单的步骤。

## 步骤 1：设置文档实例

创建一个新的实例`Document`类，代表您将使用的 PDF 文件。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; //设置文档目录
Document doc = new Document(); //创建 Document 实例
```

代替`"YOUR_DOCUMENT_DIRECTORY"`使用系统中保存 PDF 的实际路径。

## 步骤 2：向文档添加页面

接下来，向您的 PDF 文档添加一页。

```csharp
Page page = doc.Pages.Add(); //添加新页面
```

此行将向文档添加一个新页面，所有内容都将放置在该页面中。

## 步骤 3：创建文本片段

现在，让我们创建一段可作为可点击链接的文本。

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); //创建文本片段
```

这`TextFragment`将显示用户可以点击的文本。

## 步骤 4：创建本地超链接

现在，创建指向第 7 页的本地超链接。

```csharp
LocalHyperlink link = new LocalHyperlink(); //创建本地超链接
link.TargetPageNumber = 7; //设置链接的目标页面
text.Hyperlink = link; //设置文本片段的超链接
```

这`LocalHyperlink`类允许您指定超链接的目标页码。

## 步骤 5：将文本片段添加到页面

将可点击的文本添加到您创建的页面。

```csharp
page.Paragraphs.Add(text); //将文本片段添加到页面
```

此行将您的文本添加到页面的段落集合中。

## 步骤 6：创建另一个文本片段（可选）

让我们添加另一个超链接以导航回第 1 页。

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); //创建新的文本片段
textBack.IsInNewPage = true; //表明它应该在新页面上
```

## 步骤 7：设置第二个本地超链接

为第 1 页创建另一个本地超链接。

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); //创建另一个本地超链接
linkBack.TargetPageNumber = 1; //设置第二个超链接的目标页面
textBack.Hyperlink = linkBack; //设置第二个文本片段的超链接
```

## 步骤 8：将第二个文本片段添加到新页面

将第二个文本片段添加到其页面。

```csharp
Page newPage = doc.Pages.Add(); //为第二个链接添加新页面
newPage.Paragraphs.Add(textBack); //将文本片段添加到新页面
```

## 步骤 9：保存文档

最后，保存您的文档。

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; //指定输出文件名
doc.Save(dataDir); //保存更新的文档
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

此行将您的目录路径与文件名组合在一起，并且`Save()`方法保存您的文档。

## 结论

使用 Aspose.PDF for .NET 在 PDF 文件中创建本地超链接是一项实用功能，可增强导航和用户体验。现在，您掌握了直接引导读者找到所需信息的知识，从而使您的 PDF 更具交互性和用户友好性。

## 常见问题解答

### 什么是 Aspose.PDF for .NET？
Aspose.PDF for .NET 是一个库，允许开发人员使用 .NET 框架以编程方式创建、操作和转换 PDF 文档。

### 我可以创建指向外部网页的超链接吗？
是的，除了 PDF 内的本地超链接外，Aspose.PDF 还支持创建指向外部 URL 的超链接。

### Aspose.PDF 有免费试用版吗？
当然可以！您可以从[Aspose 网站](https://releases.aspose.com/).

### Aspose 支持哪些编程语言？
Aspose 提供各种编程语言的库，包括 Java、C++，以及 Python 等等。

### 如何获得 Aspose 产品的支持？
您可以通过以下方式寻求支持[Aspose 论坛](https://forum.aspose.com/c/pdf/10).