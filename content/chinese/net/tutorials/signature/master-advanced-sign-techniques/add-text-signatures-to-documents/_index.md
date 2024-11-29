---
title: 使用 GroupDocs.Signature 向文档添加文本签名
linktitle: 在文档中添加文本签名
second_title: GroupDocs.Signature .NET API
description: 了解如何使用 GroupDocs.Signature for .NET 签署带有文本的文档。以编程方式添加文本签名的分步指南。
type: docs
weight: 17
url: /zh/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## 介绍

在当今的数字环境中，电子文档签名已成为简化工作流程和节省资源的必不可少的手段。GroupDocs.Signature for .NET 提供了一种强大的解决方案，可以以编程方式将文本签名添加到各种文档格式。本教程将指导您完成使用 GroupDocs.Signature for .NET 签署带有文本的文档的步骤。

## 先决条件

在开始之前，请确保您已准备好以下物品：

1.  GroupDocs.Signature for .NET：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/signature/net/).
2. 开发环境：设置您的 .NET 开发环境。
3. 文档：准备您想要签名的文档（例如 PDF、Word）。

## 导入必要的命名空间

首先将所需的命名空间导入到您的 .NET 项目中：

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 步骤 1：加载文档

首先加载您要签署的文档：

```csharp
string filePath = "sample.pdf"; //文档路径
string fileName = Path.GetFileName(filePath);
```

## 第 2 步：定义输出文件路径

接下来，设置保存签名文档的输出文件路径：

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## 步骤 3：创建签名选项

配置文本签名的选项，包括内容、位置、大小、颜色和字体样式：

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X 位置
    Top = 200, // 位置
    Width = 100, //签名的宽度
    Height = 30, //签名的高度
    ForeColor = Color.Red, //文本颜色
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } //字体设置
};
```

## 步骤 4：签署文件

最后，使用 GroupDocs.Signature 应用文本签名并保存签名的文档：

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); //签署文件
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## 结论

在本教程中，我们演示了如何使用 GroupDocs.Signature for .NET 以编程方式向文档添加文本签名。通过遵循这些步骤，您可以有效地增强文档的安全性和真实性。

## 常见问题解答

### 我可以自定义文本签名的外观吗？
是的，您可以自定义文本签名的各种属性，例如颜色、字体、大小和位置，以满足您的需求。

### GroupDocs.Signature 是否兼容多种文档格式？
当然！GroupDocs.Signature 支持多种格式，包括 PDF、Word、Excel、PowerPoint 等。

### 我可以在单个文档中添加多个文本签名吗？
是的，您可以添加多个文本签名，每个签名都有自己的自定义选项。

### GroupDocs.Signature 签署后能保证文档的完整性吗？
是的，图书馆采用强大的加密算法来确保文档的完整性，防止签名后被篡改。

### 购买前是否有试用版可供测试？
是的，你可以从以下网站下载免费试用版[这里](https://releases.groupdocs.com/)在购买之前探索其功能。