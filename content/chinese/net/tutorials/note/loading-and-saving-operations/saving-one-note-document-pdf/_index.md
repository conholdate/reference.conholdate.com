---
title: 使用 Aspose.Note for .NET 将 OneNote 文档保存为 PDF
linktitle: 将 OneNote 文档保存为 PDF
second_title: Aspose.Note .NET API
description: 了解如何使用 Aspose.Note for .NET 高效地将 Microsoft OneNote 文档保存为 PDF 文件。本指南将引导您完成必要的先决条件，并提供有用的常见问题解答。
type: docs
weight: 26
url: /zh/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## 介绍

在本教程中，我们将探索如何使用 Aspose.Note for .NET 将文档保存为 PDF 格式。Aspose.Note 是一个功能强大的库，使开发人员能够以编程方式处理 Microsoft OneNote 文件。我们将介绍先决条件、导入命名空间，并提供将文档以各种页面布局保存为 PDF 的分步指南。

## 先决条件
1. Visual Studio：确保它已安装。
2. Aspose.Note for .NET：下载并安装该库。
3. C# 知识：需要对该语言有基本的了解。

## 导入必要的命名空间
继续之前，请在代码中导入以下命名空间：

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## 步骤 1：使用信函页面设置保存为 PDF
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; //更新此路径
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
加载 OneNote 文档并使用信纸大小的页面设置将其保存为 PDF。

## 步骤 2：使用 A4 页面设置保存为 PDF（无高度限制）
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; //更新此路径
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
与步骤 1 类似，但使用 A4 页面设置，没有高度限制。

## 结论
本教程成功演示了如何使用 Aspose.Note 将 OneNote 文件转换为 PDF 格式。通过利用不同的页面设置，开发人员可以获得文档管理的灵活性。

## 常见问题解答
### Aspose.Note 可以处理复杂的 OneNote 文件吗？
是的，它可以有效地处理复杂的 OneNote 文件的各种功能。

### Aspose.Note 适合商业项目吗？
是的，购买许可证后您可以将其用于商业应用。

### Aspose.Note 提供免费试用吗？
是的，可以免费试用以供探索。

### 在哪里可以找到 Aspose.Note 的文档？
详细文档可在 Aspose 参考网站上找到。

### 需要进一步的帮助吗？
如有疑问和支持，请参阅 Aspose.Note 论坛。
