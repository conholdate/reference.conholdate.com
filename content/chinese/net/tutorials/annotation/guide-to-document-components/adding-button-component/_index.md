---
title: 使用 GroupDocs.Annotation for .NET 添加按钮组件
linktitle: 添加按钮组件
second_title: GroupDocs.Annotation .NET API
description: 了解如何通过使用 GroupDocs.Annotation for .NET 添加交互式按钮组件来提升 PDF 文档的质量。本分步教程。
type: docs
weight: 10
url: /zh/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## 介绍

在本教程中，我们将引导您完成使用 GroupDocs.Annotation for .NET 库向 PDF 文档添加按钮组件的简单过程。在本指南结束时，您将能够使用交互式功能增强 PDF 文档。

## 先决条件

在开始之前，请确保已准备好以下事项：

1.  GroupDocs.Annotation for .NET：从以下位置下载并安装 GroupDocs.Annotation for .NET 库[这里](https://releases.groupdocs.com/annotation/net/).
2. 开发环境：设置合适的开发环境，安装.NET框架。

## 步骤 1：导入必要的命名空间

首先将所需的命名空间导入到您的项目中：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## 第 2 步：初始化输出路径

定义保存修改后的 PDF 的输出路径：

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步骤 3：添加按钮组件

现在，让我们创建按钮组件并将其添加到您的 PDF：

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), //按钮的位置和大小
        PenColor = 65535,                       //按钮边框颜色
        Style = BorderStyle.Dashed,             //边框样式
        BorderWidth = 0,                        //边框宽度
        BorderColor = 0,                        //边框颜色
        AlternateName = "Name",                 //按钮的替代名称
        PartialName = "Partial Name",           //按钮的部分名称
        NormalCaption = "Caption",               //按钮上显示的文字
        ButtonColor = 16761035,                 //按钮的背景颜色
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); //将按钮添加到注释器
    annotator.Save("result.pdf"); //保存修改后的 PDF
}
```

## 步骤4：显示输出路径

最后，告知用户输出文件的保存位置：

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

恭喜！您已成功使用 GroupDocs.Annotation for .NET 将按钮组件添加到 PDF 文档。

## 结论

在本教程中，我们演示了如何使用 GroupDocs.Annotation for .NET 将按钮组件合并到 PDF 文档中。通过遵循这些步骤，您可以显著增强 PDF 文档的交互性。

## 常见问题解答

### 我可以自定义按钮的外观吗？

当然可以！您可以修改各种属性，例如大小、颜色和样式，以满足您的要求。

### .NET 的 GroupDocs.Annotation 是否与所有 PDF 版本兼容？

是的，GroupDocs.Annotation for .NET 支持广泛的 PDF 版本，确保与大多数文档兼容。

### 我可以向单个 PDF 文档添加多个按钮组件吗？

是的，您可以根据需要向 PDF 文档中添加任意数量的按钮组件。

### GroupDocs.Annotation for .NET 是否支持其他文件格式？

是的，除了 PDF，它还支持各种文档格式，包括 DOCX、PPTX 和 XLSX。

### 是否有可供测试的试用版？

是的，您可以从以下网址免费试用 GroupDocs.Annotation for .NET[这里](https://releases.groupdocs.com/).
