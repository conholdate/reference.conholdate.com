---
title: 向已签名的 Excel 文件添加新的数字签名
linktitle: 向已签名的 Excel 文件添加新的数字签名
second_title: Aspose.Cells .NET Excel 处理 API
description: 了解如何使用 Aspose.Cells for .NET 将新数字签名添加到现有已签名的 Excel 文件。本综合指南涵盖所有先决条件、分步说明和代码示例。
type: docs
weight: 12
url: /zh/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## 介绍

在当今的数字环境中，确保文档的真实性和完整性比以往任何时候都更加重要。数字签名提供了一种可靠的方法来验证文档未被更改并且来自合法来源。如果您在 .NET 中使用 Excel 文件并且需要向已签名的文件添加新的数字签名，本指南适合您！我们将逐步介绍使用 Aspose.Cells for .NET 向现有签名的 Excel 文件添加数字签名的过程。

## 先决条件

在深入实施之前，请确保您已满足以下条件：

1.  Aspose.Cells for .NET：从以下网站下载并安装 Aspose.Cells[发布页面](https://releases.aspose.com/cells/net/).
2. .NET Framework：确保您的机器已安装 .NET Framework，并且您熟悉基本的 .NET 编程概念。
3. 数字证书：获取 .pfx 格式的有效数字证书。为了进行测试，您可以创建自签名证书。
4. 开发环境：使用 Visual Studio 等 IDE 编写和执行 C# 代码。
5. 示例 Excel 文件：有一个已经过数字签名的现有 Excel 文件，该文件将作为添加新签名的目标。

有了这些先决条件，我们就可以开始编写代码了！

## 导入必要的包

在 C# 文件的顶部，包含以下命名空间以访问所需的类和方法：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 步骤 1：定义目录

指定源文件的目录以及保存输出文件的位置：

```csharp
//源目录
string sourceDir = "Your Document Directory"; //替换为您的实际目录
//输出目录
string outputDir = "Your Document Directory"; //替换为您的实际目录
```

## 步骤 2：加载现有的签名工作簿

加载已经签名的Excel工作簿：

```csharp
//加载已经过数字签名的工作簿
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## 步骤 3：创建数字签名集合

创建一个集合来管理您的数字签名：

```csharp
//创建数字签名集合
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## 步骤 4：加载证书

加载您的数字证书，它将用于创建新的签名：

```csharp
//证书文件及其密码
string certFileName = sourceDir + "AsposeDemo.pfx"; //您的证书文件
string password = "aspose"; //您的证书密码

//创建新证书
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## 步骤 5：创建新的数字签名

现在，创建一个新的数字签名并将其添加到您的收藏中：

```csharp
//创建新的数字签名并将其添加到集合中
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## 步骤 6：将签名集合添加到工作簿

将数字签名集合添加到工作簿：

```csharp
//将数字签名集合添加到工作簿
workbook.AddDigitalSignature(dsCollection);
```

## 步骤 7：保存工作簿

保存包含新数字签名的工作簿：

```csharp
//保存工作簿
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## 步骤8：确认成功

执行成功后提供反馈：

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## 结论

恭喜！您已成功使用 Aspose.Cells for .NET 将新数字签名添加到已签名的 Excel 文件中。此过程可增强文档的安全性并确保其真实性和完整性。

## 常见问题解答

### 什么是数字签名？

数字签名是一种数学方案，用于验证数字信息或文档的真实性和完整性，确保它们没有被更改并确认签名者的身份。

### 我是否需要特殊证书来创建数字签名？

是的，需要由受信任的证书颁发机构 (CA) 颁发的数字证书才能创建有效的数字签名。

### 我可以使用自签名证书进行测试吗？

当然可以！您可以将自签名证书用于开发和测试目的，但对于生产，建议使用来自受信任 CA 的证书。

### 如果我尝试在未签名的文档中添加签名会发生什么？

如果您尝试将数字签名添加到尚未签名的文档中，它将正常工作，但原始签名将不存在。

### 在哪里可以找到有关 Aspose.Cells 的更多信息？

有关详细指南和 API 参考，请查看[Aspose.Cells 文档](https://reference.aspose.com/cells/net/).