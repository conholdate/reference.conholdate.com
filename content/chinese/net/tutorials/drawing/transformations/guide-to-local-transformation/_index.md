---
title: 使用 Aspose.Drawing for .NET 进行本地转换的指南
linktitle: Aspose.Drawing 局部变换指南
second_title: Aspose.Drawing .NET API - System.Drawing.Common 的替代品
description: 使用 Aspose.Drawing 进行局部转换，提升 .NET 应用程序的视觉功能。本综合教程将指导您通过应用转换矩阵创建令人惊叹的图形。
type: docs
weight: 11
url: /zh/net/tutorials/drawing/transformations/guide-to-local-transformation/
---
## 介绍

Aspose.Drawing for .NET 使开发人员能够通过局部转换创建复杂的图形。本简要指南将逐步指导您设置局部转换。

## 先决条件

1.  Aspose.Drawing for .NET：从以下网址下载并安装[这里](https://releases.aspose.com/drawing/net/).
2. 文档目录：选择一个目录来保存您的图像。
3. 基本 .NET 知识：熟悉 C# 和图形编程概念。

## 导入命名空间

首先将必要的命名空间导入到您的 C# 项目中：

```csharp
using System.Drawing;
using System.Drawing.Drawing2D;
```

## 步骤 1：创建位图

```csharp
Bitmap bitmap = new Bitmap(1000, 800, System.Drawing.Imaging.PixelFormat.Format32bppPArgb);
```

## 步骤 2：创建图形对象

```csharp
Graphics graphics = Graphics.FromImage(bitmap);
graphics.Clear(Color.FromKnownColor(KnownColor.Gray));
```

### 步骤 3：创建 GraphicsPath

绘制椭圆：

```csharp
GraphicsPath path = new GraphicsPath();
path.AddEllipse(300, 300, 400, 200);
```

### 步骤 4：应用局部变换

设置旋转变换矩阵：

```csharp
Matrix matrix = new Matrix();
matrix.RotateAt(45, new Point(500, 400));
path.Transform(matrix);
```

### 步骤 5：绘制变换后的路径

使用笔在图形对象上绘制路径：

```csharp
Pen pen = new Pen(Color.Blue, 2);
graphics.DrawPath(pen, path);
```

### 步骤 6：保存转换后的图像

```csharp
bitmap.Save(@"Your Document Directory\CoordinateSystemsTransformations\LocalTransformation_out.png");
```

## 结论

通过遵循这些步骤，您可以轻松地使用 Aspose.Drawing 实现本地转换，丰富您的.NET 应用程序的视觉功能。

## 常见问题解答

### 我可以按顺序应用多个转换吗？  
是的，您可以使用矩阵链接转换。

### 它适合复杂的图形应用程序吗？  
当然！Aspose.Drawing 支持广泛的图形操作。

### 还有其他类型的转换吗？  
是的，它支持平移、缩放和倾斜。

### 如何处理异常？  
实施错误处理并咨询[文档](https://reference.aspose.com/drawing/net/)寻求指导。

### 我可以在购买之前试用吗？  
是的，探索[免费试用](https://releases.aspose.com/).