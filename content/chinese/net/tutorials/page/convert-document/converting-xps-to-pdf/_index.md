---
title: 使用 Aspose.Page for .NET 将 XPS 转换为 PDF
linktitle: 将 XPS 转换为 PDF
second_title: Aspose.Page .NET API
description: 了解如何使用强大的 Aspose.Page for .NET 库将 XPS（XML 纸张规范）文档无缝转换为 PDF（可移植文档格式）。
type: docs
weight: 11
url: /zh/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## 介绍

在本教程中，我们将探索如何使用多功能 Aspose.Page for .NET 库将 XPS（XML 纸张规范）文档转换为 PDF（可移植文档格式）。这个功能强大的库简化了文档转换并提供各种自定义选项，使其成为开发人员的绝佳选择。

## 先决条件

在开始之前，请确保您已准备好以下事项：

-  Aspose.Page for .NET 库：从以下位置下载并安装 Aspose.Page for .NET 库[Aspose.Page 文档](https://reference.aspose.com/page/net/).
  
- 开发环境：使用 Visual Studio 或其他兼容 IDE 设置 .NET 开发环境。

- XPS 文档：准备好您想要转换的 XPS 文件，并将其存储在指定的目录中。

## 步骤 1：导入所需的命名空间

首先导入必要的命名空间来访问 Aspose.Page 功能：

```csharp
using Aspose.Page.XPS;
```

## 第 2 步：初始化文档目录

定义存储文档的目录路径：

```csharp
string dataDir = "Your Document Directory";
```

确保更换`"Your Document Directory"`使用包含 XPS 文档的目录的实际路径。

### 步骤 3：打开 PDF 和 XPS 流

接下来，初始化输入 XPS 文件和输出 PDF 文件的流：

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

确保为你的文件设置了正确的路径。

### 步骤 4：加载 XPS 文档

现在，使用 Aspose.Page 库加载您的 XPS 文档：

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### 步骤 5：配置 PDF 保存选项

设置 PDF 的保存选项，包括图像质量和压缩参数：

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, //设置 JPEG 质量级别
    ImageCompression = PdfImageCompression.Jpeg, //对图像使用 JPEG 压缩
    TextCompression = PdfTextCompression.Flate, //对文本应用 Flat 压缩
    PageNumbers = new int[] { 1, 2, 6 } //指定要包含的页码
};
```

请根据您的要求随意调整这些参数。

### 步骤 6：创建 PDF 渲染设备

创建 PDF 格式的渲染设备：

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### 步骤 7：将文档保存为 PDF

最后，使用指定的设备和选项将 XPS 文档保存为 PDF：

```csharp
document.Save(device, options);
```

## 结论

恭喜！您已成功使用 Aspose.Page for .NET 将 XPS 文档转换为 PDF。此库不仅简化了文档转换，还提供了处理各种格式的广泛功能。

## 常见问题解答

### 我可以将多个 XPS 文件转换为一个 PDF 吗？

当然可以！您可以遍历多个 XPS 文件，并按照相同的转换步骤将它们合并为一个 PDF 文档。

### Aspose.Page for .NET 支持哪些其他输出格式？

除了 PDF，Aspose.Page for .NET 还支持一系列格式，包括 TIFF、JPEG 和 PNG。

### 如何自定义转换后的 PDF 的外观？

您可以在`PdfSaveOptions`对象，例如 JPEG 质量和压缩设置，以实现所需的外观。

### Aspose.Page for .NET 有试用版吗？

是的，您可以免费试用 Aspose.Page for .NET[这里](https://releases.aspose.com/).

### 在哪里可以找到 Aspose.Page for .NET 的社区支持？

如需社区讨论和支持，请访问[Aspose.Page 论坛](https://forum.aspose.com/c/page/39).