---
title: 掌握使用 .NET 中的 Aspose.CAD 进行 DGN 文件操作
linktitle: 掌握 DGN 文件操作
second_title: Aspose.CAD .NET - CAD 和 BIM 文件格式
description: 了解如何加载 DGN 文件、遍历其元素、管理 2D 和 3D 实体以及将它们导出为光栅图像——同时利用 Aspose.CAD 库的强大功能。
type: docs
weight: 18
url: /zh/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## 介绍

您是渴望将 DGN 文件集成到应用程序中的 .NET 开发人员吗？Aspose.CAD for .NET 提供了一个功能强大的库，专门用于处理 DGN 文件格式。在本教程中，我们将探讨如何有效地处理 DGN 文件，包括支持的元素以及如何在 .NET 项目中操作它们。

## 先决条件

开始之前，请确保您已完成以下设置：

- .NET 编程基础知识：熟悉 C# 或 VB.NET 将会有所帮助。
- Visual Studio：安装在您的机器上，用于项目开发。
-  CAD软件 for .NET 库：从以下网址下载[Aspose.CAD](https://releases.aspose.com/cad/net/).

## 步骤 1：导入必要的命名空间

要利用 Aspose.CAD 的功能，首先将所需的命名空间导入到您的项目中。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## 步骤 2：加载 DGN 文件

首先将现有的 DGN 文件加载到您的应用程序中。这可以通过实例化`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    //继续你的逻辑
}
```

## 步骤 3：遍历 DGN 元素

加载 DGN 文件后，您可以遍历其元素。Aspose.CAD 提供多种 DGN 元素类型供您操作。

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    //处理每个元素
}
```

## 步骤 4：处理 2D 和 3D 实体

您可以区分 2D 和 3D DGN 元素。以下是如何有效地处理它们：

### 处理 2D 实体

您可以使用 switch-case 块管理以前支持的 2D 实体。

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        //在此处添加您的处理逻辑
        break;
}
```

### 处理 3D 实体

同样地，按如下方式处理 3D 实体：

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        //在此处添加您的处理逻辑
        break;
}
```

## 步骤 5：导出 DGN 文件

处理完 DGN 元素后，您可能希望将文件导出为光栅图像。这可以通过 Aspose.CAD 轻松实现。

```csharp
string outputFilePath = myDir + "Exported_Image.png"; //定义输出路径
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## 结论

在本教程中，我们学习了如何使用 Aspose.CAD for .NET 有效地管理 DGN 文件。按照概述的步骤，您可以轻松处理 2D 和 3D DGN 元素并将它们导出为光栅图像。这个强大的库可以将 DGN 处理无缝集成到您的 .NET 应用程序中，从而增强您的项目功能。

## 常见问题解答

### 在哪里可以找到 Aspose.CAD for .NET 的文档？

提供全面的文档[这里](https://reference.aspose.com/cad/net/).

### 如何下载 Aspose.CAD for .NET？

您可以下载最新版本的库[这里](https://releases.aspose.com/cad/net/).

### Aspose.CAD for .NET 有免费试用版吗？

是的，可以免费试用[这里](https://releases.aspose.com/).

### 如何获取 Aspose.CAD for .NET 的临时许可证？

您可以申请临时执照[这里](https://purchase.conholdate.com/temporary-license/).

### 需要帮助或者有疑问吗？

如需支持或咨询问题，请访问 Aspose.CAD 社区[支持论坛](https://forum.aspose.com/c/cad/19).