---
title: 在 HTML 转换中解析字体名称
linktitle: 在 HTML 转换中解析字体名称
second_title: Aspose.Words 文档处理 API
description: 了解如何在使用 Aspose.Words for .NET 将 Word 文档转换为 HTML 时有效解决字体问题。本分步指南提供了有关配置保存选项的清晰说明，以确保您的字体在导出的 HTML 格式中正确显示。
type: docs
weight: 10
url: /zh/net/tutorials/words/words-processing-with-htmlsaveoptions/resolve-font-names-in-html-conversion/
---
## 介绍

嗨，程序员朋友们！如果您在将 Word 文档保存为 HTML 时遇到字体问题，那么您并不孤单。字体可能很棘手，但不用担心；本指南将帮助您使用 Aspose.Words for .NET 解析 Word 文档中的字体名称。让我们逐步深入了解该过程，以确保您的字体在 HTML 格式中看起来正确无误。

## 先决条件

在我们开始之前，请确保您已准备好所需的一切：

1.  Aspose.Words for .NET：下载[这里](https://releases.aspose.com/words/net/).
2. 有效许可证：购买许可证[这里](https://purchase.aspose.com/buy)或获得临时执照[这里](https://purchase.aspose.com/temporary-license/).
3. C# 和 .NET 的基础知识：假设熟悉 C# 中的基本编程概念。
4. Visual Studio：任何支持.NET 框架的版本都可以使用。

现在我们已经满足了先决条件，让我们开始行动吧！

## 导入必要的命名空间

在编码之前，请确保您已将必要的命名空间导入到项目中。这对于访问 Aspose.Words 功能至关重要。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：设置文档目录

首先，让我们设置您的文档目录的路径，这是您的 Word 文档所在的位置以及您保存输出的位置。

```csharp
//文档目录的路径。
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

这里，`dataDir`保存文档目录的路径。替换`"YOUR_DOCUMENT_DIRECTORY"`使用您系统上的实际路径。

## 第 2 步：加载 Word 文档

接下来，我们需要加载要处理的 Word 文档。此文档应包含要解析的字体。

```csharp
Document doc = new Document(dataDir + "MissingFont.docx");
```

我们创建`Document`对象并从我们的`dataDir`.

## 步骤 3：配置 HTML 保存选项

现在，让我们设置将文档保存为 HTML 的选项，确保字体名称正确解析。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

我们创建一个实例`HtmlSaveOptions`和`SaveFormat.Html`。 这`PrettyFormat`选项使 HTML 输出更具可读性，并且`ResolveFontNames`确保字体名称被解析。

## 步骤 4：将文档保存为 HTML

最后，我们使用配置的保存选项将文档保存为 HTML 文件。

```csharp
doc.Save(dataDir + "ResolvedFontNames.html", saveOptions);
```

我们称之为`Save`方法`Document`对象，指定我们配置的输出路径和保存选项。这将生成一个解析了字体名称的 HTML 文件。

## 结论

就这样！按照这些步骤，您已成功解析使用 Aspose.Words for .NET 将 Word 文档转换为 HTML 时的字体名称。这不仅可以确保您的字体正确显示，还可以使您的 HTML 输出看起来精致而专业。祝您编码愉快！

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员以编程方式创建、修改和转换 Word 文档。

### 如何安装 Aspose.Words for .NET？
您可以从以下位置下载 Aspose.Words for .NET[这里](https://releases.aspose.com/words/net/). 按照文档中提供的安装说明进行操作。

### 我可以在没有许可证的情况下使用 Aspose.Words for .NET 吗？
是的，但会有一些限制。要获得完整功能，您可以购买许可证[这里](https://purchase.aspose.com/buy)或获得临时执照[这里](https://purchase.aspose.com/temporary-license/).

### 为什么我的字体在 HTML 中无法正确显示？
如果在转换过程中字体没有正确解析，则可能会出现此问题。设置`ResolveFontNames = true`在`HtmlSaveOptions`可以帮助解决这个问题。

### 在哪里可以获得 Aspose.Words for .NET 的支持？
您可以从[Aspose.Words 支持论坛](https://forum.aspose.com/c/words/8).