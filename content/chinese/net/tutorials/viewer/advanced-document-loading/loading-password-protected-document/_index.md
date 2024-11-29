---
title: 加载受密码保护的文档
linktitle: 加载受密码保护的文档
second_title: GroupDocs.Viewer .NET API
description: 了解如何使用 GroupDocs.Viewer 轻松地将文档查看功能集成到 .NET 应用程序中。本教程提供了全面的分步指南。
type: docs
weight: 12
url: /zh/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## 介绍

在数字领域，管理和查看各种文档格式的能力对于企业和个人来说至关重要。GroupDocs.Viewer for .NET 为开发人员提供了一个强大的解决方案，使他们能够轻松地将文档查看功能集成到他们的应用程序中。本教程将逐步指导您完成加载受密码保护的文档的过程，确保您可以在项目中无缝实现此功能。

## 先决条件

在开始之前，请确保您已准备好以下物品：

1. 已安装 GroupDocs.Viewer for .NET：从[网站](https://releases.groupdocs.com/viewer/net/).
2. 受密码保护的文档：准备好受密码保护的文档以供测试。

## 导入所需的命名空间

首先将必要的命名空间导入到您的项目中：

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## 步骤 1：定义输出目录

指定渲染输出的保存位置：

```csharp
string outputDirectory = "Your Document Directory";
```
确保更换`"Your Document Directory"`与您想要使用的实际路径。

## 步骤2：设置页面文件路径格式

定义每个渲染页面的文件路径的格式：

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

这将生成类似的路径`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`， ETC。

## 步骤 3：配置加载选项

设置受密码保护的文档的加载选项，包括密码：

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  //替换为您的文档密码
};
```

## 步骤 4：初始化查看器

使用您的文档和加载选项创建 GroupDocs.Viewer 的实例：

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    //下一步将添加查看选项的代码。
}
```
确保更换`"Path_to_your_document"`使用您的文档的实际路径。

## 步骤 5：配置 HTML 视图选项

设置用于呈现嵌入资源的文档的 HTML 视图选项：

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## 步骤 6：渲染文档

现在，使用配置的查看器和视图选项呈现文档：

```csharp
viewer.View(options);
```

## 步骤 7：显示成功消息

最后，通知用户文档已成功呈现：

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## 结论

在本教程中，我们探讨了如何使用 GroupDocs.Viewer for .NET 加载受密码保护的文档。通过遵循这些步骤，开发人员可以轻松地将此功能集成到他们的应用程序中，让用户轻松查看受保护的文档。

## 常见问题解答

### 除了受密码保护的文档之外，GroupDocs.Viewer 还能处理其他文档格式吗？

是的，GroupDocs.Viewer 支持多种格式，包括 PDF、DOCX、XLSX、PPTX 等。

### GroupDocs.Viewer 是否与 .NET Core 兼容？

当然！GroupDocs.Viewer 与 .NET Framework 和 .NET Core 环境兼容。

### 我可以自定义文档的渲染选项吗？

是的，GroupDocs.Viewer 提供各种渲染选项，允许您根据需要定制查看体验。

### GroupDocs.Viewer 是否支持文档注释？

是的，它支持文档注释，使用户可以添加评论、突出显示和其他注释。

### GroupDocs.Viewer 有试用版吗？

是的，你可以从[网站](https://releases.groupdocs.com/).