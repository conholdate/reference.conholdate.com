---
title: 向 PDF 文档添加目录
linktitle: 向 PDF 文档添加目录
second_title: Aspose.PDF for .NET API 参考
description: 本教程演示如何使用 Aspose.Pdf for .NET 向 PDF 文档添加目录 (TOC)。
type: docs
weight: 40
url: /zh/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## 介绍

在 PDF 文档中创建目录 (TOC) 可以大大增强其导航和可访问性。在本指南中，我们将演示如何使用 Aspose.Pdf for .NET 将目录添加到 PDF 文件。

## 先决条件

开始之前，请确保您已准备好以下物品：

1.   Aspose.PDF for .NET: 从以下网址下载并安装最新版本[这里](https://releases.aspose.com/pdf/net/).
2.  开发环境：设置一个.NET开发环境，如Visual Studio。
3.  许可证：如有需要，请申请临时许可证；请访问[Aspose.Pdf 许可页面](https://asposepdf.com/developers)了解更多信息。

导入必要的库

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## 步骤 1：加载 PDF 文档

将现有的 PDF 文件加载到要添加目录的位置。指定文档目录的路径。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## 步骤 2：插入目录的新页面

在 PDF 文档开头插入新页面。该页面将作为目录 (TOC)。

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## 步骤 3：创建 TOC 信息对象

创建一个表示目录信息的对象。添加标题和链接以便更好地导航。

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## 步骤 4：定义目录元素

定义目录中将显示的元素（或标题）。这些元素可以帮助读者导航到文档的特定部分。

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## 步骤 5：创建目录标题

为目录中的前两个元素创建标题。这些标题将链接到其各自的页面。

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## 步骤 6：保存包含目录的 PDF

最后，保存更新后的PDF文件。

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## 确认信息

显示确认消息以让用户知道该过程已完成。

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## 结论

使用 Aspose.PDF for .NET，向 PDF 添加目录不仅简单，而且可自定义。无论您需要创建简单的导航链接还是复杂的结构，此工具都能满足您的需求。因此，下次处理较长的 PDF 时，不要忘记添加目录以增添专业感。

## 常见问题解答

### 我可以自定义 Aspose.PDF 中 TOC 的外观吗？

是的，您可以完全自定义目录的外观，包括字体样式、大小和对齐方式。

### 如何向目录中添加副标题？

您可以通过调整`Heading`水平（例如，`Heading(2)`）。

### 如果文档发生变化，是否可以自动更新目录？

不会，目录不会自动更新。如果文档结构发生变化，则需要重新创建目录。

### 我可以将目录条目链接到外部文档吗？

是的，您可以使用超链接将目录条目链接到外部 PDF 或 URL。

### Aspose.PDF 是否支持多级目录？

是的，Aspose.PDF 支持带有子部分的复杂文档的多级目录。
