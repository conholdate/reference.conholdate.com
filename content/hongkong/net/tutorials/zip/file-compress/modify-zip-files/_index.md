---
title: 使用 Aspose.Zip for .NET 修改 Zip 文件
linktitle: 修改 Zip 檔案
second_title: 用於檔案壓縮和歸檔的 Aspose.Zip .NET API
description: 了解如何以程式設計方式有效地提取、刪除和新增條目到 zip 文件，從而增強您的文件操作能力。
type: docs
weight: 15
url: /zh-hant/net/tutorials/zip/file-compress/modify-zip-files/
---
## 介紹

Zip 檔案對於資料組織和壓縮至關重要，但如何以程式設計方式修改其內容？解決方案在於 Aspose.Zip for .NET，這是一個強大的函式庫，可以簡化使用 C# 進行 zip 檔案操作。在本教程中，我們將指導您逐步提取、刪除和新增 zip 檔案中的條目。

## 先決條件

在我們深入之前，請確保您具備以下條件：

1.  Aspose.Zip for .NET Library：在專案中安裝該程式庫。你可以下載它[這裡](https://releases.aspose.com/zip/net/).
   
2. 文檔目錄：設定一個目錄來儲存 zip 檔案。代替`"Your Document Directory"`在程式碼中使用您的實際路徑。

## 導入必要的命名空間

首先導入所需的命名空間：

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## 第 1 步：開啟外部 Zip 文件

首先開啟您的主 zip 檔案（外部 zip）：

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    //繼續識別內部 zip 條目
}
```

## 第 2 步：識別內部拉鍊條目

接下來，識別並準備刪除所有內部 zip 檔案：

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
            
            //提取內部條目
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

## 步驟 3：刪除內部存檔項目

收集完所需的條目後，刪除內部 zip 條目：

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## 步驟 4：將修改後的條目新增至外拉鍊

現在，您可以將新提取的條目新增回外部 zip 檔案中：

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## 第 5 步：儲存修改後的 Zip 文件

最後，將變更儲存到新的 zip 檔案中：

```csharp
outer.Save(dataDir + "flatten.zip");
```

## 結論

Aspose.Zip for .NET 提供了一種強大且簡單的方法來以程式設計方式操作 zip 檔案。本教學介紹了提取、刪除和新增條目到 zip 檔案中，展示了該庫的多功能性。探索不同的場景，提升你的文件操作技巧！

## 常見問題解答

### 我可以將 Aspose.Zip for .NET 與其他程式語言一起使用嗎？
Aspose.Zip 主要是為 .NET 應用程式設計的，但 Aspose 為各種程式語言提供了類似的程式庫。

### Aspose.Zip for .NET 有沒有免費試用版？
是的，可以下載免費試用版[這裡](https://releases.aspose.com/).

### 如何獲得 Aspose.Zip for .NET 支援？
參觀[Aspose.Zip 論壇](https://forum.aspose.com/c/zip/37)以尋求支持和討論。

### 我可以購買 Aspose.Zip for .NET 的臨時授權嗎？
是的，您可以獲得臨時許可證[這裡](https://purchase.conholdate.com/temporary-license/).

### 在哪裡可以找到 Aspose.Zip for .NET 的文檔？
完整的文檔可用[這裡](https://reference.aspose.com/zip/net/).