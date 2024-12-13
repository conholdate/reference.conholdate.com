---
title: 使用 Aspose.Cells for .NET 在 Excel 工作簿中複製數據
linktitle: 使用 Aspose.Cells for .NET 在 Excel 工作簿中複製數據
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何使用 Aspose.Cells for .NET 在 Excel 工作簿中有效複製資料。請按照此逐步指南輕鬆複製工作表、傳輸資料和管理 Excel 檔案。
type: docs
weight: 12
url: /zh-hant/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## 介紹

在本詳細指南中，我們將示範如何使用 Aspose.Cells for .NET 在相同工作簿中複製資料。透過遵循下面概述的逐步說明，您將學習如何以程式設計方式複製工作表，保留其內容和格式。

## 使用 Aspose.Cells 在 Excel 中複製資料的先決條件

在深入編碼過程之前，讓我們確保一切準備就緒：

1. Aspose.Cells for .NET 函式庫：您需要安裝 Aspose.Cells for .NET 函式庫。您可以從以下位置下載最新版本[Aspose.Cells for .NET 下載頁面](https://releases.aspose.com/cells/net/).
2. 開發環境：編寫和執行程式碼需要 .NET 相容的 IDE（例如 Visual Studio）。
3.  Aspose 授權：您可以使用免費試用版或購買的授權。欲了解更多信息，請訪問[這裡](https://purchase.aspose.com/temporary-license/).

設定先決條件後，您就可以開始使用該程式庫了。

## 導入所需的套件

首先，您需要從 Aspose.Cells 匯入相關的命名空間。這允許您使用 Aspose.Cells 提供的類別和方法來處理 Excel 檔案。

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

這些命名空間將使您能夠訪問`Workbook`類別（用於處理 Excel 檔案）和`WorksheetCollection`（用於存取工作簿中的多個工作表）。

## 步驟1：初始化工作簿的檔案路徑

為了保持程式碼井井有條，必須定義工作簿所在的檔案路徑以及要儲存修改後的檔案的位置。以下是指定路徑的方法：

```csharp
//定義Excel檔案所在的目錄路徑。
string dataDir = "Your Directory Path";

//定義輸入工作簿的完整路徑。
string inputPath = dataDir + "book1.xls";
```

代替`"Your Directory Path"`包含工作簿的目錄的實際路徑。這有助於確保程式碼靈活並且您可以有效地管理路徑。

## 步驟 2：開啟工作簿以存取數據

現在文件路徑已設置，下一步是將 Excel 工作簿載入到`Workbook`目的。這允許您存取其內容進行操作。

```csharp
//將 Excel 檔案載入到 Workbook 物件中。
Workbook wb = new Workbook(inputPath);
```

透過這一行，你已經成功加載了`book1.xls`進入`wb`對象，使其資料可存取。

## 第 3 步：存取工作表集合

載入工作簿後，您可以存取其中包含的工作表。 Aspose.Cells 提供了`Worksheets`集合，它允許您與工作簿中的每個工作表進行互動。

```csharp
//從工作簿中檢索工作表集合。
WorksheetCollection sheets = wb.Worksheets;
```

這`sheets`物件現在可以讓您存取其中的所有工作表`book1.xls`，您可以對它們執行各種操作，包括將資料從一張紙複製到另一張紙。

## 步驟 4：將資料從一張紙複製到另一張紙

要將資料從一個工作表複製到同一工作簿中的另一個工作表，Aspose.Cells 提供了一種易於使用的方法，稱為`AddCopy`。此方法建立指定工作表的副本並將其附加到工作簿。

```csharp
//將資料從「Sheet1」複製到工作簿中的新工作表。
sheets.AddCopy("Sheet1");
```

在此範例中，我們將資料從「Sheet1」複製到新工作表。這`AddCopy`方法將複製整個工作表，保留其所有內容，包括公式、格式和值。

## 步驟5：儲存修改後的工作簿

複製資料後，您可以使用新名稱或位置儲存修改後的工作簿。這是透過呼叫來完成的`Save`方法上的`Workbook`目的。

```csharp
//使用新名稱儲存修改後的工作簿。
wb.Save(dataDir + "book1_copy.xls");
```

這會將工作簿與複製的工作表儲存為`book1_copy.xls`在指定目錄中。您可以根據需要更改檔案名稱和路徑。

## 結論

使用 Aspose.Cells for .NET 在 Excel 工作簿中複製資料是一項簡單的任務，本指南提供了高效完成此操作所需的步驟。無論您是複製整個工作表還是特定資料範圍，Aspose.Cells 都提供強大且靈活的 API，使 Excel 自動化變得簡單且有效。

## 常見問題解答

### 我可以一次影印多張紙嗎？

Aspose.Cells 不支援在一次呼叫中複製多個工作表。但是，您可以循環瀏覽要複製的工作表並單獨複製它們。

### 如何重新命名複製的工作表？

複製工作表後，您可以將其重命名如下：

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells 與 .NET Core 相容嗎？

是的，Aspose.Cells 與 .NET Framework 和 .NET Core 環境完全相容。

### Aspose.Cells 如何在複製過程中處理格式？

這`AddCopy`方法在複製工作表時保留所有內容和格式，確保複製的資料看起來與原始資料相同。

### 我可以將工作表複製到不同的工作簿嗎？

是的，您可以使用以下命令將工作表複製到不同的工作簿`Copy`方法並引用目標工作簿。

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```