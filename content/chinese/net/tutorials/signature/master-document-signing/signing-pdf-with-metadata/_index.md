---
title: 使用 GroupDocs.Signature 签署带元数据的 PDF 的指南
linktitle: 使用元数据签署 PDF 的指南
second_title: GroupDocs.Signature .NET API
description: 了解如何使用 GroupDocs.Signature for .NET 对 PDF 文档进行元数据签名，从而增强 PDF 文档的安全性和可追溯性。本综合教程提供了清晰的说明。
type: docs
weight: 11
url: /zh/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## 介绍

在本教程中，我们将学习如何使用 GroupDocs.Signature for .NET 签署 PDF 文档并添加元数据。添加元数据可通过提供作者、创建日期、文档 ID 等基本信息来增强文档的效果。

## 先决条件

在开始之前，请确保您已准备好以下内容：

1.  GroupDocs.Signature for .NET：从以下网址下载[这里](https://releases.groupdocs.com/signature/net/).
2. PDF 文档：准备好要签名的示例 PDF 文件。
3. C# 编程基础知识：熟悉 C# 语法对于理解代码示例是必要的。

## 导入命名空间

首先导入所需的命名空间来访问必要的类和方法：

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 步骤 1：加载 PDF 文档

指定要签名的PDF文档的路径：

```csharp
string filePath = "sample.pdf";
```

## 第 2 步：指定输出文件路径

定义已签名 PDF 及其元数据的保存位置：

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## 步骤 3：创建签名实例

初始化一个`Signature`PDF 文档路径实例：

```csharp
using (Signature signature = new Signature(filePath))
{
    //签名相关代码将放在此处
}
```

## 步骤 4：定义元数据选项

创造`MetadataSignOptions`并添加元数据字段及其值：

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) //字符串值
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       //日期时间值
    .Add(new PdfMetadataSignature("DocumentId", 123456))            //整数值
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         //双倍值
    .Add(new PdfMetadataSignature("Amount", 123.456M))              //十进制值
    .Add(new PdfMetadataSignature("Total", 123.456F));              //浮点值
```

## 第 5 步：签署文件

使用指定的元数据选项对 PDF 文档进行签名并保存签名的文档：

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## 结论

在本教程中，我们介绍了如何使用 GroupDocs.Signature for .NET 使用元数据对 PDF 文档进行签名。通过遵循这些步骤，您可以轻松地使用有价值的元数据丰富您的 PDF 文件，从而提高其可追溯性和实用性。

## 常见问题解答

### 我可以向我的 PDF 文档添加自定义元数据字段吗？

是的，您可以使用 GroupDocs.Signature for .NET 指定字段名称及其对应的值来添加自定义元数据字段。

### GroupDocs.Signature for .NET 是否与所有版本的 .NET Framework 兼容？

GroupDocs.Signature for .NET 与 .NET Framework 的各个版本兼容，确保灵活性和易于集成。

### GroupDocs.Signature 是否支持签署除 PDF 之外的其他文档格式？

是的，GroupDocs.Signature 支持多种文档格式，包括 Word、Excel、PowerPoint 等。

### 我可以使用 GroupDocs.Signature for .NET 批量签署多个文档吗？

当然可以！您可以通过遍历文件列表并以编程方式应用签名流程来批量签署多个文档。

### GroupDocs.Signature 用户可以获得技术支持吗？

是的，GroupDocs 通过其论坛提供专门的技术支持。您可以访问支持论坛[这里](https://forum.groupdocs.com/c/signature/13).