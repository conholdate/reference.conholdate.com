---
title: 使用 GroupDocs.Signature 对带有元数据的图像进行签名的指南
linktitle: 使用元数据对图像进行签名的指南
second_title: GroupDocs.Signature .NET API
description: 了解如何使用 GroupDocs.Signature 在 .NET 应用程序中高效地使用元数据对图像进行签名。本分步教程涵盖了从安装到实施的所有内容，使您能够轻松地使用元数据签名增强文档。
type: docs
weight: 10
url: /zh/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## 介绍

GroupDocs.Signature for .NET 是一个功能强大的库，允许开发人员使用元数据高效地对图像进行签名。本教程将逐步指导您完成该过程。

## 先决条件

在开始之前，请确保您已准备好以下物品：

1.  GroupDocs.Signature for .NET：在您的 .NET 项目中安装 GroupDocs.Signature 包。您可以从以下位置下载[这里](https://releases.groupdocs.com/signature/net/).
2. 图像文件：准备要用元数据签名的图像文件。

## 导入必要的命名空间

在 C# 代码中，导入以下命名空间：

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 步骤 1：加载图像文件

首先指定图像文件的路径和签名图像的输出目录：

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## 步骤 2：创建元数据签名

接下来，创建元数据签名并将其添加到签名选项中：

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; //元数据的起始 ID
    MetadataSignOptions options = new MetadataSignOptions();

    //添加各种类型的元数据签名
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) //字符串值
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          //日期时间值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                //整数值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              //双倍值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              //十进制值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             //浮点值

    //签署文件并保存结果
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## 结论

在本教程中，您学习了如何使用 GroupDocs.Signature for .NET 使用元数据对图像进行签名。通过遵循这些步骤，您可以轻松地将元数据签名添加到 .NET 应用程序中，从而增强图像的功能和完整性。

## 常见问题解答

### 我可以使用 GroupDocs.Signature for .NET 对多个图像进行元数据签名吗？
是的，您可以通过遍历每个图像文件并应用元数据签名来签署多个图像。

### GroupDocs.Signature for .NET 有试用版吗？
是的，你可以从[这里](https://releases.groupdocs.com/).

### GroupDocs.Signature for .NET 除了支持图像之外还支持其他文件格式吗？
当然！GroupDocs.Signature 支持多种格式，包括 PDF、Word、Excel 等。

### 我可以自定义元数据签名的外观吗？
是的，您可以自定义字体大小、颜色和元数据签名的位置等方面。

### 在哪里可以获得 .NET 的 GroupDocs.Signature 支持？
如需支持，请访问 GroupDocs.Signature 论坛[这里](https://forum.groupdocs.com/c/signature/13).