---
title: 使用 Aspose.Slides 从 PowerPoint 中的超链接中提取音频
linktitle: 从超链接中提取音频
second_title: Aspose.Slides .NET PowerPoint 处理 API
description: 了解如何使用 Aspose.Slides for .NET 从 PowerPoint 演示文稿中的超链接中提取音频。本分步指南提供了清晰的说明。
type: docs
weight: 12
url: /zh/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## 介绍

在多媒体演示中，音频可显著增强幻灯片的影响力。如果您曾经遇到过带有音频超链接的 PowerPoint 演示文稿，并想知道如何提取该音频用于其他用途，那么您来对地方了。本指南将引导您完成使用 Aspose.Slides for .NET 库从 PowerPoint 演示文稿中的超链接中提取音频的过程。

## 先决条件

在开始之前，请确保您已准备好以下内容：

### Aspose.Slides for .NET 库

确保已安装 Aspose.Slides for .NET 库。如果尚未安装，可以从[Aspose.Slides for .NET 文档](https://reference.aspose.com/slides/net/).

### 带有音频超链接的 PowerPoint 演示文稿

您需要一个包含带相关音频的超链接的 PowerPoint 演示文稿 (PPTX)。此演示文稿将作为音频提取的来源。

## 导入所需的命名空间

为了有效地使用 Aspose.Slides for .NET，您需要将以下命名空间导入到您的 C# 项目中：

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

现在我们已经准备好一切，让我们将提取过程分解为简单的步骤。

## 步骤 1：定义文档目录

首先指定 PowerPoint 演示文稿所在的目录。替换`"Your Document Directory"`与实际路径。

```csharp
string dataDir = "Your Document Directory";
```

## 第 2 步：加载 PowerPoint 演示文稿

接下来，加载包含音频超链接的 PowerPoint 演示文稿 (PPTX)。替换`"HyperlinkSound.pptx"`替换为您的实际演示文稿文件名。

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    //继续下一步。
}
```

## 步骤 3：访问超链接声音

从第一张幻灯片的第一个形状中检索超链接。如果此超链接有关联的声音，我们可以继续提取它。

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    //继续下一步。
}
```

## 步骤 4：从超链接中提取音频

如果超链接包含声音，我们可以将其提取为字节数组并将其保存为媒体文件。

```csharp
//将超链接声音提取为字节数组
byte[] audioData = link.Sound.BinaryData;

//指定要保存提取的音频的路径
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

//将提取的音频保存为媒体文件
File.WriteAllBytes(outMediaPath, audioData);
```

恭喜！您已成功使用 Aspose.Slides for .NET 从 PowerPoint 演示文稿中的超链接中提取音频。您现在可以在多媒体项目中使用此音频。

## 结论

Aspose.Slides for .NET 提供了一种功能强大且用户友好的方法来从 PowerPoint 演示文稿中的超链接中提取音频。通过本指南中概述的步骤，您可以轻松地重复使用演示文稿中的音频内容来增强您的项目。

## 常见问题解答

### Aspose.Slides for .NET 是一个免费的库吗？
不，Aspose.Slides for .NET 是一个商业库，但你可以下载免费试用版来探索其功能[这里](https://releases.aspose.com/).

### 我可以从 PPT 等旧版 PowerPoint 格式中提取音频吗？
是的，Aspose.Slides for .NET 支持 PPTX 和 PPT 格式的音频提取。

### 是否有一个 Aspose.Slides 支持社区论坛？
当然！您可以在[Aspose.Slides 社区论坛](https://forum.aspose.com/).

### 我可以为短期项目购买 Aspose.Slides 临时许可证吗？
是的，您可以通过访问获取临时许可证，以满足您的短期项目需求[此链接](https://purchase.aspose.com/temporary-license/).

### 除了 MPG 之外，还支持提取其他音频格式吗？
是的，Aspose.Slides for .NET 允许提取各种音频格式。提取后，您可以将音频转换为您喜欢的格式。