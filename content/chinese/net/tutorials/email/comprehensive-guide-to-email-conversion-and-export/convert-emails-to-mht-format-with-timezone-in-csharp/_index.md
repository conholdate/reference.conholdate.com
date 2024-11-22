---
title: 使用 C# 将电子邮件转换为带时区的 MHT 格式
linktitle: 使用 C# 将电子邮件转换为带时区的 MHT 格式
second_title: Aspose.Email .NET 电子邮件处理 API
description: 本详细指南提供了清晰的说明，说明如何使用 Aspose.Email for .NET 库将电子邮件消息转换为 MHT 格式，同时准确处理时区信息。
type: docs
weight: 12
url: /zh/net/tutorials/email/comprehensive-guide-to-email-conversion-and-export/convert-emails-to-mht-format-with-timezone-in-csharp/
---
## 介绍

将电子邮件转换为各种格式是软件应用程序中的常见任务，尤其是在时间和时区数据至关重要的情况下。本指南将引导您完成将电子邮件转换为 MHT 格式的过程，同时确保准确保留时区信息。

## 设置你的开发环境

首先，请确保您拥有合适的开发环境：

1. 安装 Visual Studio：确保您的机器上安装了兼容版本的 Visual Studio。
2. 创建一个新的 C# 项目：启动 Visual Studio 并为您的电子邮件转换应用程序创建一个新的 C# 项目。

## 安装 Aspose.Email for .NET

Aspose.Email for .NET 是一个功能强大的库，可简化电子邮件处理任务。请按照以下步骤进行安装：

1. 在 Visual Studio 中打开您的项目。
2. 导航到工具>NuGet 包管理器>管理解决方案的 NuGet 包。
3. 搜索 Aspose.Email 并安装该包。
```csharp
//添加必要的 using 语句
using Aspose.Email;
```
## 加载和解析电子邮件

接下来，您需要加载并解析要转换的电子邮件消息。使用以下代码片段：

```csharp
//加载电子邮件消息
var message = MailMessage.Load("path/to/your/email.eml");

//访问消息属性
var subject = message.Subject;
var sender = message.From.Address;
//... 根据需要提供其他属性
```

## 处理时区信息

准确管理时区信息至关重要。以下代码片段演示了如何从电子邮件中提取和处理时区数据：

```csharp
var timezone = message.TimezoneOffset;
var timezoneId = Timezone.GetIdFromOffset(timezone);
var timezoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timezoneId);
//您现在可以使用 timezoneInfo 来处理时区转换
```

## 将电子邮件转换为 MHT 格式

现在，让我们使用 Aspose.Email 执行核心转换为 MHT 格式：

```csharp
//设置 MHT 保存选项
var mhtOptions = MhtSaveOptions.DefaultMhtml;

//为MHT输出创建内存流
using var mhtStream = new MemoryStream();
message.Save(mhtStream, mhtOptions);
```

## 保存MHT文件

将电子邮件转换为 MHT 格式后，就可以将其保存为文件了：

```csharp
//将 MHT 流保存到文件
using var fileStream = new FileStream("output.mht", FileMode.Create);
mhtStream.Seek(0, SeekOrigin.Begin);
mhtStream.CopyTo(fileStream);
```

## 结论

在本指南中，您学习了如何使用 Aspose.Email for .NET 将电子邮件转换为 MHT 格式，同时有效处理时区信息。通过遵循这些步骤并探索其他自定义选项，您可以将电子邮件转换功能无缝集成到您的应用程序中。

## 常见问题解答

### 如何在电子邮件转换期间处理附件？

要管理附件，请使用`Attachments`的财产`MailMessage`类。遍历附件并在转换过程中根据需要保存它们。

### 我可以使用 Aspose.Email for .NET 将电子邮件转换为其他格式吗？

当然！Aspose.Email for .NET 支持多种格式，包括 MSG、EML、PST 等。您可以调整提供的代码示例以适合您所需的输出格式。

### 时区信息是否以 MHT 格式保存？

是的，转换过程中会保留时区信息。通过处理时区偏移并使用适当的`TimeZoneInfo`方法，您可以确保 MHT 文件中的时区表示准确。

### 在哪里可以找到有关 Aspose.Email for .NET 的更多文档和更新？

有关全面的信息和更新，请参阅文档：[Aspose.Email for .NET API 参考](https://reference.aspose.com/email/net/)

### 如何下载最新版本的 Aspose.Email for .NET？

您可以从发布页面下载最新版本：[下载 Aspose.Email for .NET](https://releases.aspose.com/email/net/)