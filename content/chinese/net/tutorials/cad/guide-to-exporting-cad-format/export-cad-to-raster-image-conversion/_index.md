---
title: 使用 Aspose.CAD for .NET 将 CAD 导出为光栅图像转换
linktitle: 导出 CAD 到光栅图像转换
second_title: Aspose.CAD .NET - CAD 和 BIM 文件格式
description: 了解如何使用 Aspose.CAD for .NET 高效地将 CAD 布局转换为各种光栅图像格式。本综合指南将通过清晰的代码引导您完成整个过程。
type: docs
weight: 10
url: /zh/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## 介绍

您是否希望使用 Aspose.CAD for .NET 轻松将 CAD 布局转换为光栅图像格式？本分步指南旨在帮助您完成整个过程，并配有简洁的代码片段，让您获得流畅的体验。无论您是经验丰富的开发人员还是刚刚起步，本教程都能为所有技能水平的开发人员提供宝贵的见解。

## 先决条件

在开始之前，请确保您已准备好以下物品：

-  Aspose.CAD for .NET 库：从以下网站下载并安装该库[Aspose.CAD 网站](https://releases.aspose.com/cad/net/).
- CAD 绘图文件：准备好 CAD 绘图文件（例如，`conic_pyramid.dxf`) 已准备好进行转换。

## 导入所需的命名空间

在您的 .NET 项目中，您需要导入必要的命名空间才能使用 Aspose.CAD 函数。将以下内容添加到代码顶部：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 步骤 1：加载 CAD 绘图

首先，指定目录并将 CAD 文件加载到 Image 实例中：

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

//加载 CAD 绘图
using (var image = Image.Load(sourceFilePath))
{
    //继续执行后续步骤
}
```

## 步骤 2：创建栅格化选项

接下来，设置光栅化选项，定义输出图像所需的尺寸：

```csharp
//初始化 CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## 步骤 3：指定要转换的图层

如果要转换特定图层，请将它们添加到栅格化选项中：

```csharp
//指定要转换的图层
rasterizationOptions.Layers = new [] { "LayerA" };
```

## 步骤 4：设置 JPEG 导出选项

现在，为您想要导出的图像格式创建选项（在本例中为 JPEG）：

```csharp
//创建用于导出的 JpegOptions
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 步骤 5：导出为 JPEG 格式

最后保存转换后的图像：

```csharp
//定义输出文件路径并保存图像
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## 附加功能：转换所有图层

要转换 CAD 绘图中的所有图层，您可以实现如下方法：

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    //遍历图层并将每个图层保存为单独的 JPEG 文件
    //您的实现代码在这里
}
```

## 结论

恭喜！您已经学会了如何使用 Aspose.CAD for .NET 有效地将 CAD 布局转换为光栅图像格式。本指南提供了一种简单的方法，适合那些希望实现高效 CAD 转换的开发人员。

## 常见问题解答

### 我可以导出不同的图像格式吗？

当然！只需交换`JpegOptions`使用其他格式选项，例如`PngOptions`或者`BmpOptions`，具体取决于您的需要。

### 有试用版吗？

是的，您可以按照以下步骤下载试用版来探索功能[关联](https://releases.aspose.com/cad/net/).

### 在哪里可以找到对 Aspose.CAD 的支持？

如需社区支持，请查看 Aspose.CAD[论坛](https://forum.aspose.com/c/cad/19)，或者考虑购买许可证以获得更专门的帮助。

### 可以办理临时执照吗？

是的，有临时执照；你可以申请一个[这里](https://purchase.conholdate.com/temporary-license/).

### 在哪里可以获得详细文档？

访问综合文档[这里](https://reference.aspose.com/cad/net/)了解更多信息。