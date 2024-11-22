---
title: 使用 Aspose.Tasks for .NET 將 MS 專案檔轉換為 PDF
linktitle: Aspose.Tasks 的 PDF 儲存選項
second_title: Aspose.Tasks .NET API
description: 了解如何使用 Aspose.Tasks for .NET 將 Microsoft Project (.mpp) 檔案轉換為 PDF。請依照此逐步指南自訂 PDF 輸出、選擇特定頁面以及自動批次轉換。
type: docs
weight: 13
url: /zh-hant/net/tutorials/tasks/guide-to-saving-options/convert-ms-project-files-to-pdf/
---
## 介紹

高效的專案文件管理在簡化工作流程和專案成功方面發揮關鍵作用。使用 Aspose.Tasks for .NET，開發人員可以精確、靈活地將 Microsoft Project 檔案轉換為 PDF 格式。在本指南中，我們將逐步介紹將 Microsoft Project (.mpp) 檔案儲存為 PDF 的過程，並提供可自訂的選項。

## 使用 Aspose.Tasks for .NET 的先決條件

在繼續之前，請確保滿足以下先決條件：

1. 用於 .NET 安裝的 Aspose.Tasks  
   從以下位置下載並安裝該程式庫[網站](https://releases.aspose.com/tasks/net/).

2. 開發環境  
   C# 程式語言的應用知識和已設定的 .NET 開發環境。

3. 輸入微軟專案文件  
   擁有有效的`.mpp`可用於轉換的檔案。

## 導入基本命名空間

在編碼之前，請包含存取 Aspose.Tasks 功能所需的名稱空間。 

```csharp
using Aspose.Tasks;
using Aspose.Tasks.Saving;
using Aspose.Tasks.Visualization;
using System.Collections.Generic;
```

## 第 1 步：載入 Microsoft Project 文件

首先，載入`.mpp`文件到`Project`目的。代替`"Your_Project_File_Path.mpp"`與輸入檔案的路徑。

```csharp
var project = new Project("Your_Project_File_Path.mpp");
```

## 步驟 2：設定 PDF 儲存選項

設定選項以自訂輸出 PDF。 Aspose.Tasks for .NET 提供了控制頁面渲染、佈局和其他方面的靈活性。

```csharp
var options = new PdfSaveOptions
{
    RenderToSinglePage = false, //是否在單一頁面上呈現所有內容
    Pages = new List<int>()     //要包含在 PDF 中的頁面
};
```

## 第 3 步：確定頁數

使用`PageCount`屬性來識別項目跨越了多少頁。這有助於決定是包含特定頁面還是匯出全部頁面。

```csharp
Console.WriteLine("Total Pages: " + options.PageCount);
```

## 步驟 4：選擇要匯出的特定頁面（可選）

透過填入指定要包含在 PDF 中的確切頁面`Pages`財產。例如，匯出第 1 頁和第 4 頁：

```csharp
options.Pages.Add(1);
options.Pages.Add(4);
```

## 第 5 步：將專案文件另存為 PDF

最後，保存`.mpp`透過呼叫將文件儲存為 PDF`Save`方法。指定輸出檔案路徑並傳遞配置的選項。

```csharp
project.Save("Output_PDF_File_Path.pdf", options);
```

## 結論

使用 Aspose.Tasks for .NET 將 Microsoft Project 檔案轉換為 PDF 可確保無縫且可自訂的體驗。從選擇特定頁面到自動批次匯出，該工具使開發人員能夠有效地處理專案文件。

## 常見問題解答

### 我可以自訂匯出的 PDF 的外觀嗎？
是的，Aspose.Tasks 允許自訂字體、顏色和頁面佈局以滿足您的特定需求。

### 是否可以轉換`.mpp` files from older versions of Microsoft Project?
Aspose.Tasks 支持`.mpp`Microsoft Project 2003 以上版本的檔案。

### 如何在單一 PDF 頁面上呈現所有項目資料？
設定`RenderToSinglePage`的財產`PdfSaveOptions`反對`true`.

```csharp
options.RenderToSinglePage = true;
```

### 我可以將項目資料匯出為其他文件格式嗎？
是的，Aspose.Tasks 支援匯出為各種格式，包括 Excel、HTML 以及 PNG 和 JPEG 等圖片格式。

### Aspose.Tasks for .NET 有沒有免費試用版？
是的，您可以下載一個[免費試用版在這裡](https://releases.aspose.com/).