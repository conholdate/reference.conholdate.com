---
title: 创建新的数字签名行并设置提供商 ID
linktitle: 创建新的数字签名行并设置提供商 ID
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 以编程方式将签名行添加到 Word 文档中。本综合指南涵盖了从设置开发环境到插入签名行和安全签署文档的所有内容。
type: docs
weight: 10
url: /zh/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## 介绍

大家好，技术爱好者们！您是否曾经想过自动在 Word 文档中添加签名行？今天，我们将深入探讨如何使用 Aspose.Words for .NET 实现此目的。本分步指南将引导您创建签名行并设置提供商 ID，从而使您的文档处理任务更加高效和简化。

## 先决条件

在开始之前，请确保您已完成所有设置：

1.  Aspose.Words for .NET：如果您尚未安装，请下载[这里](https://releases.aspose.com/words/net/).
2. 开发环境：使用 Visual Studio 或任何 C# 开发设置。
3. .NET Framework：确保您的机器上安装了 .NET Framework。
4. PFX 证书：您需要一个 PFX 证书来签署文档，该证书可以从受信任的证书颁发机构获得。

## 导入必要的命名空间

首先，将所需的命名空间导入到您的 C# 项目中：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

现在，让我们深入了解创建新签名行和设置提供商 ID 的细节。

## 步骤 1：创建新文档

首先，我们需要创建一个新的 Word 文档，它将作为我们签名行的画布：

```csharp
//指定文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在这里我们初始化一个新的`Document`和一个`DocumentBuilder`，这使得我们可以轻松添加元素。

## 第 2 步：定义签名行选项

接下来，我们将定义签名行的选项，包括签名者的姓名、职务、电子邮件和其他相关详细信息：

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

这些选项有助于个性化签名行，使其清晰、专业。

## 步骤 3：插入签名行

准备好选项后，我们现在可以将签名行插入文档：

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

这`InsertSignatureLine`方法添加签名行，我们为其分配一个唯一的提供者ID。

## 步骤 4：保存文档

插入签名行后，我们来保存文档：

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

这将保存您的文档以及新添加的签名行。

## 步骤 5：设置签名选项

现在，我们将配置签名选项，包括签名行 ID、提供商 ID、评论和签名时间：

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

这些设置确保文档使用正确的详细信息进行签名。

## 步骤 6：创建证书持有者

为了签署文档，我们需要使用 PFX 证书创建证书持有者：

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

代替`"morzal.pfx"`替换为您的实际证书文件名`"aw"`使用您的证书密码。

## 步骤 7：签署文件

最后，我们将使用数字签名实用程序对文档进行签名：

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

此过程对文档进行签名并将其保存为新文件。

## 结论

恭喜！您已成功使用 Aspose.Words for .NET 在 Word 文档中创建签名行并设置提供商 ID。这个强大的库简化了文档处理任务，使您的工作流程更加高效。尝试一下，看看它如何增强您的项目！

## 常见问题解答

### 我可以自定义签名行的外观吗？
当然！您可以在`SignatureLineOptions`以满足您的风格和要求。

### 如果我没有 PFX 证书怎么办？
您需要从受信任的证书颁发机构获取一个，因为它对于对文档进行数字签名至关重要。

### 我可以在一份文档中添加多个签名行吗？
是的，您可以通过使用不同的选项重复插入过程来添加多个签名行。

### Aspose.Words for .NET 是否与 .NET Core 兼容？
是的，Aspose.Words for .NET 支持 .NET Core，使其适用于各种开发环境。

### 数字签名有多安全？
只要您使用有效且受信任的证书，使用 Aspose.Words 创建的数字签名就非常安全。