---
title: 将所有 CSS 规则保存在单个文件中
linktitle: 在单个文件中写入所有 CSS 规则
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在使用 HtmlFixedSaveOptions 保存文档时将所有 CSS 规则写入单个文件。请按照此详细教程获取分步指导。
type: docs
weight: 10
url: /zh/net/tutorials/words/html-fixed-save-options/save-all-css-rules-in-single-file/
---
## 介绍

在将 Word 文档转换为 HTML 时，您是否曾为一堆杂乱的 CSS 规则而苦恼？您并不孤单！幸运的是，Aspose.Words for .NET 提供了一项强大的功能，可让您将所有 CSS 规则合并到一个文件中。这不仅可以清理您的代码，还可以简化您的工作流程。让我们踏上更干净、更高效的 HTML 输出之旅吧！

## 先决条件

在开始编码之前，请确保您具有以下内容：

1.  Aspose.Words for .NET：从以下位置获取库[这里](https://releases.aspose.com/words/net/).
2. .NET 开发环境：像 Visual Studio 这样的设置对于开发来说是理想的。
3. 基本 C# 知识：熟悉 C# 将帮助您浏览代码。
4. Word 文档：准备好要转换的 .docx 文件。

## 导入命名空间

首先，让我们在 C# 项目中导入必要的命名空间。这将使我们能够轻松访问 Aspose.Words 功能。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

让我们将这个过程分解为可管理的步骤，以确保顺利转换。

## 步骤 1：设置文档目录

首先，建立 Word 文档所在的目录路径以及转换后的 HTML 的保存位置。

```csharp
//定义文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## 第 2 步：加载 Word 文档

接下来，使用`Document`Aspose.Words 库中的类。

```csharp
//加载 Word 文档
Document doc = new Document(dataDir + "Document.docx");
```

## 步骤 3：配置 HTML 保存选项

现在，让我们配置 HTML 保存选项。我们希望通过设置来启用将所有 CSS 规则合并到单个文件中的功能`SaveFontFaceCssSeparately`到`false`.

```csharp
//配置 HTML 保存选项以将所有 CSS 规则写入一个文件中
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## 步骤 4：将文档转换为 HTML

最后，使用指定的选项将文档保存为 HTML 文件。这可确保所有 CSS 规则整齐地组织在一个文件中。

```csharp
//将文档转换为 HTML
doc.Save(dataDir + "ConvertedDocument.html", saveOptions);
```

## 结论

恭喜！只需几行代码，您就成功将 Word 文档转换为 HTML，确保所有 CSS 规则都整齐地编译到单个文件中。这种方法简化了 CSS 管理并增强了 HTML 文档的可维护性。下次您需要转换 Word 文档时，您将拥有一个轻松便捷的流程！

## 常见问题解答

### 为什么我应该对 HTML 输出使用单个 CSS 文件？
单个 CSS 文件简化了样式管理，使您的 HTML 更清晰、更易于维护。

### 如果需要，我可以分离字体 CSS 规则吗？
当然！通过设置`SaveFontFaceCssSeparately`到`true`，您可以将字体 CSS 规则分离到不同的文件中。

### Aspose.Words for .NET 可以免费使用吗？
 Aspose.Words 提供免费试用版供下载[这里](https://releases.aspose.com/)。如需继续使用，请考虑购买许可证[这里](https://purchase.aspose.com/buy).

### Aspose.Words for .NET 还可以转换为哪些其他格式？
Aspose.Words 支持各种格式，包括 PDF、TXT 和 JPEG 和 PNG 等图像格式。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多资源？
有关全面指南和 API 参考，请查看[文档](https://reference.aspose.com/words/net/).
