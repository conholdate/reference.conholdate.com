---
title: 使用 Aspose.Words for .NET 将 DOCX 转换为 MHTML 并发送电子邮件
linktitle: 使用 Aspose.Words for .NET 将 DOCX 转换为 MHTML 并发送电子邮件
second_title: Aspose.Words 文档处理 API
description: 本综合指南提供了有关将 DOCX 文档转换为 MHTML 格式并使用 .NET 中的 Aspose.Words 和 Aspose.Email 库通过电子邮件发送的分步教程。
type: docs
weight: 10
url: /zh/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## 介绍

在当今的数字环境中，将文档在不同格式之间转换并通过电子邮件发送是一项常见任务。本指南将指导您使用功能强大的 .NET Aspose.Words 和 Aspose.Email 库将 DOCX 文件转换为 MHTML 格式并通过电子邮件发送。我们将清楚地分解每个步骤，确保您可以轻松跟进。让我们开始吧！

## 先决条件

在深入了解该过程之前，请确保已进行以下设置：

1.  Aspose.Words for .NET：从以下位置下载并安装该库[Aspose 发布页面](https://releases.aspose.com/words/net/).
2. Aspose.Email for .NET：从以下位置下载并安装此库[Aspose 发布页面](https://releases.aspose.com/email/net/).
3. .NET Framework：确保您的机器上安装了 .NET Framework。
4. SMTP 服务器：您需要访问 SMTP 服务器来发送电子邮件。

## 导入必要的命名空间

要在项目中使用 Aspose.Words 和 Aspose.Email，您必须导入所需的命名空间。在 C# 文件顶部添加以下使用指令：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## 步骤 1：加载 DOCX 文档

首先加载要转换的 DOCX 文档。使用`Document`来自 Aspose.Words 的类来完成此操作。

```csharp
//指定文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 步骤 2：将文档另存为 MHTML

接下来，将加载的文档转换为 MHTML 格式。此操作使用`Save`方法`Document`班级。

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    //将流位置重置为读取的开头。
    stream.Position = 0;
}
```

## 步骤 3：创建电子邮件

现在，使用 Aspose.Email 从 MHTML 流创建电子邮件消息。您将利用`MailMessage`为此目的而设的班级。

```csharp
//将 MHTML 流加载到 Aspose.Email MIME 电子邮件消息中。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 步骤 4：发送电子邮件

最后，使用 SMTP 客户端发送电子邮件。使用您的服务器详细信息配置 SMTP 客户端，并使用`Send`方法来发送消息。

```csharp
//使用 Aspose.Email 配置并发送消息。
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## 结论

恭喜！您已成功将 DOCX 文档转换为 MHTML，并使用 Aspose.Words 和 Aspose.Email for .NET 通过电子邮件发送。此过程包括加载文档、将其转换为 MHTML、创建电子邮件消息以及通过 SMTP 客户端发送。通过这些步骤，您可以在应用程序中无缝地自动转换和发送电子邮件。

## 常见问题解答

### 我可以使用此方法来转换其他文档格式吗？
当然！Aspose.Words 支持多种格式，允许您将 DOC、DOCX、RTF 等转换为 MHTML。

### 如何在电子邮件中添加附件？
您可以使用`Attachments`的财产`MailMessage`班级。

### Aspose.Words 与 .NET Core 兼容吗？
是的，Aspose.Words 与 .NET Core 兼容，因此适合在 .NET Core 应用程序中使用。

### 我需要 Aspose.Words 和 Aspose.Email 的许可证吗？
是的，这两个库都需要许可证。您可以从[Aspose 购买页面](https://purchase.conholdate.com/temporary-license/).

### 在哪里可以找到更多文档？
有关详细文档，请查看 Aspose.Words[这里](https://reference.aspose.com/words/net/)和 Aspose.Email[这里](https://reference.aspose.com/email/net/).