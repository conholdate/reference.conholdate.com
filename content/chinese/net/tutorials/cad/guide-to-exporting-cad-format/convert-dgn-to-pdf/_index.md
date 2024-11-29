---
title: 在 Aspose.CAD for .NET 中将 DGN 转换为 PDF
linktitle: 在 Aspose.CAD for .NET 中将 DGN 转换为 PDF
second_title: Aspose.CAD .NET - CAD 和 BIM 文件格式
description: 了解如何使用功能强大的 Aspose.CAD .NET 库轻松将 DGN 文件转换为 PDF。本分步指南适用于各个级别的开发人员。
type: docs
weight: 12
url: /zh/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## 介绍

浏览 CAD 文件的世界可能具有挑战性，但使用 Aspose.CAD for .NET，开发人员可以轻松操作和转换各种 CAD 格式。一个常见的需求是将 DGN 文件转换为 PDF，我们将在本教程中逐步探索这一点。

## 先决条件

为了继续进行，请确保您具有以下条件：

- 熟练掌握 C# 和 .NET 框架的基本知识。
- 已安装 Aspose.CAD for .NET 库。您可以下载它[这里](https://releases.aspose.com/cad/net/).
- 示例 DGN 文件（例如 Nikon_D90_Camera.dgn）。 

## 步骤 1：导入所需的命名空间

首先在 C# 项目中导入相关的命名空间：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 步骤 2：加载 DGN 文件

指定 DGN 文件的目录并使用以下代码加载它：

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    //将在此处进行额外处理...
}
```

## 步骤 3：配置光栅化选项

接下来，设置光栅化选项来定义 DGN 在 PDF 中的呈现方式：

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, //根据需要调整宽度
    PageHeight = 300, //根据需要调整高度
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## 步骤 4：创建 PDF 选项

定义 PDF 选项，集成之前配置的光栅化设置：

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 步骤 5：将 DGN 保存为 PDF

最后，使用您配置的选项将 DGN 文件保存为 PDF：

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## 结论

恭喜！您已成功使用 Aspose.CAD for .NET 将 DGN 文件转换为 PDF。本简单易懂的教程将指导您加载 DGN 文件、设置光栅化选项以及将输出保存为 PDF。

## 常见问题解答

### 我需要具备 CAD 知识才能使用 Aspose.CAD 吗？  
当然！Aspose.CAD 旨在简化复杂的 CAD 任务，让所有开发人员都可以使用它，无论他们是否具备 CAD 知识。

### 在哪里可以找到有关 Aspose.CAD 的更多资源和文档？  
您可以在[Aspose.CAD 文档](https://reference.aspose.com/cad/net/).

### Aspose.CAD 有免费试用版吗？  
是的，可以免费试用[这里](https://releases.aspose.com/).

### 如何获得 Aspose.CAD 的临时许可证？  
您可以申请临时执照[这里](https://purchase.conholdate.com/temporary-license/).

### 需要帮助或者有疑问吗？  
加入对话[Aspose.CAD 论坛](https://forum.aspose.com/c/cad/19)获取社区支持和咨询。