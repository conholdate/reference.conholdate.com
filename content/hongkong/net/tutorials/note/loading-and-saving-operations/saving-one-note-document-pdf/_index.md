---
title: 使用 Aspose.Note for .NET 將 OneNote 文件儲存為 PDF
linktitle: 將 OneNote 文件儲存為 PDF
second_title: Aspose.Note .NET API
description: 了解如何使用 Aspose.Note for .NET 將 Microsoft OneNote 文件有效地儲存為 PDF 檔案。本指南將引導您完成必要的先決條件，並提供有用的常見問題。
type: docs
weight: 26
url: /zh-hant/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## 介紹

在本教學中，我們將探討如何使用 Aspose.Note for .NET 將文件儲存為 PDF 格式。 Aspose.Note 是一個功能強大的函式庫，使開發人員能夠以程式設計方式處理 Microsoft OneNote 檔案。我們將介紹先決條件、匯入命名空間，並提供將文件儲存為各種頁面佈局的 PDF 的逐步指南。

## 先決條件
1. Visual Studio：確保已安裝。
2. Aspose.Note for .NET：下載並安裝該程式庫。
3. C# 知識：需要對該語言有基本的了解。

## 導入必要的命名空間
在繼續之前，請在程式碼中匯入以下命名空間：

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## 第 1 步：使用 Letter 頁面設定儲存為 PDF
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; //更新此路徑
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
載入 OneNote 文件並使用 letter 大小的頁面設定將其另存為 PDF。

## 步驟 2：使用 A4 頁面設定儲存為 PDF（無高度限制）
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; //更新此路徑
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
與步驟 1 類似，但使用 A4 頁面設置，沒有高度限制。

## 結論
本教學成功示範如何使用 Aspose.Note 將 OneNote 檔案轉換為 PDF 格式。透過利用不同的頁面設置，開發人員可以獲得文件管理的靈活性。

## 常見問題解答
### Aspose.Note 可以處理複雜的 OneNote 檔案嗎？
是的，它有效地處理複雜 OneNote 檔案的各種功能。

### Aspose.Note適合商業項目嗎？
是的，您可以在購買許可證後將其用於商業應用。

### Aspose.Note 提供免費試用嗎？
是的，可以免費試用以進行探索。

### 在哪裡可以找到 Aspose.Note 的文檔？
詳細文件可在 Aspose 參考網站上找到。

### 需要進一步幫助嗎？
有關問題和支持，請參閱 Aspose.Note 論壇。
