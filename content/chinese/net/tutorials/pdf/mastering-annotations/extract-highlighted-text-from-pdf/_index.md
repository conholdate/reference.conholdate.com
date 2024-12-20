---
title: 使用 Aspose.PDF for .NET 从 PDF 中提取突出显示的文本
linktitle: 使用 Aspose.PDF for .NET 从 PDF 中提取突出显示的文本
second_title: Aspose.PDF for .NET API 参考
description: 通过学习如何使用 Aspose.PDF for .NET 提取突出显示的文本，释放 PDF 文档的潜力。本综合指南将引导您完成从设置到实施的每个步骤。
type: docs
weight: 60
url: /zh/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## 介绍

处理 PDF 文件时，提取突出显示的文本对于数据分析、内容审查或整理笔记至关重要。如果您使用的是 Aspose.PDF for .NET，那么您很幸运。本教程提供了清晰的分步说明，说明如何有效地从 PDF 文档中提取突出显示的文本。

## 先决条件

在开始之前，请确保已准备好以下事项：

-  Aspose.Pdf for .NET Library：从以下网址下载该库[发布页面](https://releases.aspose.com/pdf/net/).
- 开发环境：像 Visual Studio 这样的工作环境。
- C# 基础知识：必须熟悉 C# 和面向对象编程。
-  Aspose 许可证：虽然你可以从免费试用开始，[临时执照](https://purchase.aspose.com/temporary-license/)或完整许可[这里](https://purchase.aspose.com/buy)将提供不受限制的访问。

## 导入必要的命名空间

首先在 C# 项目中导入所需的命名空间：

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

这些命名空间提供处理 PDF 文档和注释所需的类和方法的访问。

## 步骤 1：设置项目目录

指定 PDF 文件所在的目录：

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

确保用 PDF 文件的实际目录替换路径。

## 第 2 步：加载 PDF 文档

使用以下代码加载PDF文档：

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

确保指定的文件存在于给定的目录中。

## 步骤 3：访问页面上的注释

要访问注释，请循环遍历所需页面（在本例中为第一页）上的注释：

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

此代码过滤`TextMarkupAnnotation`类型，代表亮点。

## 步骤 4：提取突出显示的文本

现在，从突出显示的注释中提取并显示文本：

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

这将检索与突出显示相关的所有标记文本片段并将其打印到控制台。

## 结论

使用 Aspose.PDF for .NET 从 PDF 中提取突出显示的文本非常简单，并且可以显著增强您的文档处理流程。通过遵循上述步骤，您可以高效地收集突出显示的文本以用于各种应用程序，例如报告准备或数据分析。

## 常见问题解答

### 我可以提取其他类型的注释吗？
是的，只需调整`if`条件包括不同的注释类型，如`TextAnnotation`或者`StampAnnotation`.

### 如何从所有 PDF 页面中提取突出显示的文本？
您可以使用以下方法循环遍历所有页面：
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Aspose.PDF for .NET 需要许可证吗？
可以免费试用，但请考虑[临时执照](https://purchase.aspose.com/temporary-license/)或获取完整许可证以获得完全访问权限。

### 我可以将提取的文本保存到文件中吗？
当然可以！您可以修改代码，将提取的文本写入文本文件。

### Aspose.PDF 是否支持其他平台？
是的，Aspose.PDF 也支持 Java 和其他平台，提供类似的功能。