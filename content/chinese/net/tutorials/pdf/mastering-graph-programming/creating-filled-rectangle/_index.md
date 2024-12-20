---
title: 创建填充矩形
linktitle: 创建填充矩形
second_title: Aspose.PDF for .NET API 参考
description: 在本分步教程中，使用 Aspose.PDF for .NET 解锁 PDF 操作的强大功能。了解如何通过绘制填充矩形以编程方式创建具有视觉吸引力的 PDF 文档。
type: docs
weight: 50
url: /zh/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## 介绍

您是否曾想过以编程方式创建视觉效果出色的 PDF？如果是这样，那么您来对地方了！在本教程中，我们将探索 Aspose.PDF for .NET，这是一个功能强大的库，可简化 PDF 文档操作。今天，我们将重点介绍如何在 PDF 文件中创建填充矩形。无论您是经验丰富的开发人员还是刚刚入门，本指南都将以友好且引人入胜的方式引导您完成每个步骤。所以，戴上您的编码帽，让我们开始吧！

## 先决条件

在深入研究代码之前，请确保您具有以下内容：

1. Visual Studio：在您的机器上安装 Visual Studio，因为它是用于 .NET 开发的优秀 IDE。
2. Aspose.PDF for .NET：从以下网址下载并安装 Aspose.PDF 库[这里](https://releases.aspose.com/pdf/net/).
3. C# 基础知识：熟悉 C# 编程将帮助您更好地理解代码片段。

## 步骤 1：创建新项目

1. 打开 Visual Studio 并创建一个新的控制台应用程序项目。
2. 给你的项目起一个合适的名字。

## 第 2 步：添加 Aspose.PDF 引用

1. 在解决方案资源管理器中右键单击您的项目。
2. 选择管理 NuGet 包。
3. 搜索 Aspose.PDF 并安装最新版本。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

现在我们已经设置好了一切，让我们深入研究代码！

## 步骤 3：设置文档目录

指定 PDF 的保存路径：

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`使用您想要保存 PDF 的机器上的实际路径。

## 步骤 4：创建文档实例

初始化一个新的 PDF 文档：

```csharp
//创建 Document 实例
Document doc = new Document();
```

## 步骤 5：向文档添加页面

每个 PDF 至少需要一页。让我们添加一页：

```csharp
//将页面添加到 PDF 文件的页面集合
Page page = doc.Pages.Add();
```

## 步骤 6：创建图形实例

一个`Graph`实例充当绘制形状的画布：

```csharp
//创建 Graph 实例
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## 步骤 7：将图表添加到页面

将图表附加到页面：

```csharp
//将图形对象添加到页面实例的段落集合中
page.Paragraphs.Add(graph);
```

## 步骤 8：创建矩形实例

定义矩形的位置和大小：

```csharp
//创建 Rectangle 实例
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## 步骤 9：指定填充颜色

选择矩形的颜色。在本例中，我们将使用红色：

```csharp
//指定图形对象的填充颜色
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## 步骤 10：将矩形添加到图形中

将矩形添加到图形中：

```csharp
//将矩形对象添加到图形对象的形状集合中
graph.Shapes.Add(rect);
```

## 步骤 11：保存 PDF 文档

最后，将您的文档保存到指定目录：

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
//保存 PDF 文件
doc.Save(dataDir);
```

## 步骤12：确认信息

打印确认消息以表明成功：

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## 结论

恭喜！您已成功使用 Aspose.PDF for .NET 在 PDF 文档中创建了一个填充矩形。这个功能强大的库为 PDF 操作开辟了无限可能，让您能够以编程方式生成令人惊叹的文档。无论您是创建报告、发票还是任何其他类型的 PDF，Aspose.PDF 都能满足您的需求。

## 常见问题解答

### 什么是 Aspose.PDF for .NET？
Aspose.PDF for .NET 是一个库，允许开发人员以编程方式创建、操作和转换 PDF 文档。

### 我可以免费使用 Aspose.PDF 吗？
是的，Aspose 提供免费试用版，你可以使用它来探索该库的功能。你可以下载它[这里](https://releases.aspose.com/).

### 有没有办法获得对 Aspose.PDF 的支持？
当然！您可以通过 Aspose 论坛获得支持[这里](https://forum.aspose.com/c/pdf/10).

### 如何购买 Aspose.PDF？
您可以通过访问购买页面购买 Aspose.PDF[这里](https://purchase.aspose.com/buy).

### 我可以使用 Aspose.PDF 创建哪些类型的形状？
您可以使用 Aspose.PDF 库创建各种形状，包括矩形、圆形、线条等。