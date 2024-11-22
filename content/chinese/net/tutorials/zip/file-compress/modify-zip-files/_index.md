---
title: 使用 Aspose.Zip for .NET 修改 Zip 文件
linktitle: 修改 Zip 文件
second_title: 用于文件压缩和归档的 Aspose.Zip .NET API
description: 了解如何以编程方式高效地提取、删除和添加 zip 文件的条目，从而增强您的文件操作能力。
type: docs
weight: 15
url: /zh/net/tutorials/zip/file-compress/modify-zip-files/
---
## 介绍

Zip 文件对于数据组织和压缩至关重要，但如何以编程方式修改其内容？解决方案在于 Aspose.Zip for .NET，这是一个强大的库，可简化使用 C# 的 zip 文件操作。在本教程中，我们将逐步指导您提取、删除和添加 zip 文件中的条目。

## 先决条件

在深入研究之前，请确保您具备以下条件：

1.  Aspose.Zip for .NET Library：在您的项目中安装该库。您可以下载它[这里](https://releases.aspose.com/zip/net/).
   
2. 文档目录：设置一个目录来存储您的 zip 文件。替换`"Your Document Directory"`在代码中使用您的实际路径。

## 导入必要的命名空间

首先导入所需的命名空间：

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## 步骤 1：打开外部 Zip 文件

首先打开你的主 zip 文件（外部 zip）：

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    //继续识别内部 zip 条目
}
```

## 第 2 步：识别内部 Zip 条目

接下来，识别并准备删除所有内部 zip 文件：

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            //提取内部条目
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## 步骤 3：删除内部存档条目

收集完所需的条目后，删除内部 zip 条目：

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## 步骤 4：将修改后的条目添加到外部 Zip

现在，你可以将新提取的条目添加回外部 zip 文件中：

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## 步骤5：保存修改后的Zip文件

最后，将更改保存到新的 zip 文件中：

```csharp
outer.Save(dataDir + "flatten.zip");
```

## 结论

Aspose.Zip for .NET 提供了一种强大而直接的方法来以编程方式操作 zip 文件。本教程介绍了如何提取、删除和添加 zip 文件的条目，说明了该库的多功能性。探索不同的场景，并提高您的文件操作技能！

## 常见问题解答

### 我可以将 Aspose.Zip for .NET 与其他编程语言一起使用吗？
Aspose.Zip 主要用于 .NET 应用程序，但 Aspose 为各种编程语言提供了类似的库。

### Aspose.Zip for .NET 有免费试用版吗？
是的，可以下载免费试用版[这里](https://releases.aspose.com/).

### 如何获得 Aspose.Zip for .NET 的支持？
访问[Aspose.Zip 论坛](https://forum.aspose.com/c/zip/37)寻求支持和讨论。

### 我可以购买 Aspose.Zip for .NET 的临时许可证吗？
是的，你可以获得临时驾照[这里](https://purchase.conholdate.com/temporary-license/).

### 在哪里可以找到 Aspose.Zip for .NET 的文档？
完整文档可供查看[这里](https://reference.aspose.com/zip/net/).