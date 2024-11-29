---
title: 在 GroupDocs 比较中保存 .NET 的文档元数据源
linktitle: 在 .NET 的 GroupDocs 比较中保存文档元数据源
second_title: GroupDocs.Comparison .NET API
description: 利用 GroupDocs Comparison for .NET，充分发挥 .NET 应用程序中文档比较的潜力。本分步教程将引导您轻松比较文档，同时重点介绍如何保存文档元数据源。
type: docs
weight: 14
url: /zh/net/tutorials/comparison/load-and-save-documents/save-documents-metadata-source/
---
## 介绍

在软件开发中，特别是在法律、金融和教育等行业中，高效地比较文档的能力至关重要。GroupDocs Comparison for .NET 提供了一个强大的解决方案，可以在您的 .NET 应用程序中无缝地比较文档。本教程将指导您利用这个强大的库来保存文档元数据源，确保您最大限度地发挥其功能来完成文档比较任务。

## 先决条件

在开始之前，请确保您已进行以下设置：

1. 开发环境：您的机器上已准备好.NET 开发环境。
2. GroupDocs Comparison 安装：从[地点](https://releases.groupdocs.com/comparison/net/).
3. 文档文件：准备您想要比较的源文档文件和目标文档文件。
4. C# 基础知识：熟悉 C# 编程基础知识将帮助您理解所提供的代码片段。

## 导入所需的命名空间

首先将必要的命名空间导入到您的项目中：

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## 步骤 1：定义输出目录和文件名

首先，指定比较的文档的保存位置及其名称：

```csharp
string outputDirectory = "Your Document Directory"; //例如，“C:\\Documents”
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```

## 步骤 2：初始化比较器对象

创建一个`Comparer`实例使用源文档的路径：

```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
这将初始化`Comparer`对象，为您的文档比较提供基础。

## 步骤 3：添加目标文档

接下来，将目标文档纳入比较：

```csharp
comparer.Add("TARGET.docx");
```
此步骤指定您想要与源进行比较的文档。

## 步骤 4：比较文档并保存元数据源

现在，是时候进行比较并保存文档元数据源了：

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
在这里，`Compare`方法比较源文档和目标文档。通过使用`CloneMetadataType`，确保保留源文档的元数据。

## 步骤5：显示输出消息

比较完成后，提供有关操作的反馈：

```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
此消息确认比较成功并指示在何处找到输出文档。

## 结论

GroupDocs Comparison for .NET 是一款非常有价值的工具，可用于在 .NET 应用程序中执行文档比较任务。通过遵循本指南，您将学会如何高效地保存文档元数据源，从而增强文档比较过程和整体生产力。

## 常见问题解答

### GroupDocs Comparison for .NET 可以比较不同格式的文档吗？

是的，它支持多种格式，包括 DOCX、PDF、PPTX 等。

### 有试用版吗？

您可以从[这里](https://releases.groupdocs.com/).

### 我可以自定义比较文档的输出格式吗？

当然！GroupDocs Comparison 允许对输出格式进行广泛的自定义。

### 是否为用户提供技术支持？

是的，你可以通过[支持论坛](https://forum.groupdocs.com/c/comparison/12).

### 我可以在哪里购买许可证？

可以从 GroupDocs 网站购买许可证[这里](https://purchase.groupdocs.com/buy).