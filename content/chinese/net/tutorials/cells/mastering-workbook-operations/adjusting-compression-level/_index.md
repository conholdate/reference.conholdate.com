---
title: 调整工作簿中的压缩级别
linktitle: 调整工作簿中的压缩级别
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何通过使用 Aspose.Cells for .NET 调整压缩级别来有效管理大型 Excel 文件。本分步指南涵盖从设置目录到测量压缩时间的所有内容，帮助您优化文件大小并提高性能。
type: docs
weight: 14
url: /zh/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## 介绍

管理大型 Excel 文件可能是一项挑战，尤其是在存储和传输效率方面。幸运的是，文件压缩可以显著减少这些文件的大小，使它们更易于处理。如果您使用 Aspose.Cells for .NET，则可以轻松调整工作簿的压缩级别。本指南将逐步引导您完成该过程，并提供代码每个部分的清晰解释。

## 先决条件

在深入研究代码之前，请确保您满足以下先决条件：

1. C# 基础知识：熟悉 C# 编程将帮助您更好地理解代码片段。
2.  Aspose.Cells 库：从以下网址下载并安装 Aspose.Cells 库[这里](https://releases.aspose.com/cells/net/).
3. Visual Studio：运行代码需要像 Visual Studio 这样的开发环境。
4. .NET Framework：确保您的项目设置了兼容版本的 .NET Framework。

## 导入必要的包

首先，您需要在 C# 项目中导入必要的包。在代码文件顶部添加以下几行：

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

这些包对于使用 Aspose.Cells 库处理 Excel 文件至关重要。`Aspose.Cells`命名空间包含操作 Excel 文件所需的所有类，而`Aspose.Cells.Xlsb`提供以 XLSB 格式保存文件的选项。

## 步骤 1：定义源和输出目录

首先，设置源文件所在的目录以及要保存输出文件的目录：

```csharp
//定义源目录和输出目录
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

确保更换`"Your Document Directory\\"`替换目录的实际路径。这可确保您的程序能够找到需要处理的文件。

## 步骤 2：加载工作簿

接下来，加载要压缩的工作簿：

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

在这里，我们创建一个新的实例`Workbook`类并加载现有的 Excel 文件。确保文件名与源目录中的文件名匹配。

## 步骤 3：设置保存选项

现在，配置工作簿的保存选项：

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

这`XlsbSaveOptions`该类允许您在以 XLSB 格式保存工作簿时指定各种选项，包括压缩级别。

## 步骤 4：测量 1 级压缩时间

从第一个压缩级别开始，测量保存工作簿所需的时间：

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此代码片段将压缩类型设置为 1 级，保存工作簿，并测量经过的时间。

## 步骤 5：测量第 6 级的压缩时间

接下来，测试使用 6 级压缩的性能：

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此步骤与上一步类似，但压缩级别更高。

## 步骤 6：测量第 9 级的压缩时间

最后，评估最高压缩级别的性能：

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此步骤将压缩级别设置为 9 级，您可能会看到文件大小最显著的减少，尽管处理时间可能会更长。

## 步骤7：最终输出

完成所有压缩级别后，输出一条消息表明该过程已成功完成：

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

这行简单的话即可确认您的程序已顺利执行。

## 结论

使用 Aspose.Cells for .NET 调整工作簿的压缩级别是一个简单的过程，可以显著改善文件大小和性能。通过遵循本指南中概述的步骤，您可以有效地在应用程序中实施压缩，从而增强 Excel 文件管理功能。

## 常见问题解答

### 什么是 Aspose.Cells？  
Aspose.Cells 是一个强大的.NET 库，允许开发人员无需 Microsoft Excel 即可创建、操作和转换 Excel 文件。

### 如何安装 Aspose.Cells？  
您可以从[Aspose 网站](https://releases.aspose.com/cells/net/).

### 有哪些压缩级别？  
Aspose.Cells 支持多种压缩级别，从 1 级（最低压缩）到 9 级（最高压缩）。

### 我可以免费测试 Aspose.Cells 吗？  
是的！您可以免费试用 Aspose.Cells[这里](https://releases.aspose.com/).

### 在哪里可以找到对 Aspose.Cells 的支持？  
如有任何疑问或需要支持，请访问 Aspose 支持论坛[这里](https://forum.aspose.com/c/cells/9).