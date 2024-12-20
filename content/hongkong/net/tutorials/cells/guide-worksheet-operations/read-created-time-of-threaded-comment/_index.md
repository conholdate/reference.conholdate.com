---
title: 使用 Aspose.Cells 讀取線程評論的建立時間
linktitle: 使用 Aspose.Cells 讀取線程評論的建立時間
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何使用 Aspose.Cells for .NET 輕鬆讀取 Excel 工作表中串聯註解的建立時間。請按照我們的詳細指南和逐步說明進行操作。
type: docs
weight: 21
url: /zh-hant/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## 介紹

使用 Excel 檔案時，管理註釋對於協作和回饋追蹤至關重要。在本指南中，我們將引導您完成使用 Aspose.Cells for .NET 讀取 Excel 工作表中執行緒註解的建立時間的過程。這個強大的工具提供了一種與 Excel 文件互動的有效方式，使開發人員能夠從註釋中提取詳細信息，這對於追蹤協作場景中的反饋時間特別有用。

## 先決條件

在開始之前，確保正確設定您的開發環境以使用 Aspose.Cells for .NET 非常重要。這是您需要的：

1.  Aspose.Cells for .NET：您需要安裝 Aspose.Cells 函式庫。您可以從以下位置取得最新版本[阿斯普斯網站](https://releases.aspose.com/cells/net/).
2. IDE：用於編寫和執行程式碼的 Visual Studio（或您選擇的任何 .NET IDE）。
3. 基本 C# 知識：熟悉 C# 程式設計將使您更容易理解範例。
4.  Excel 檔案：在本教學中，我們將使用名為的 Excel 文件`ThreadedCommentsSample.xlsx`，其中包括一些線索評論。確保您的文件包含要遵循的註釋。

## 導入所需的套件

首先，您需要匯入使用 Aspose.Cells 所需的命名空間。開啟 C# 專案並在程式碼檔案頂部新增以下 using 指令：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

這`Aspose.Cells`命名空間可讓您存取操作 Excel 檔案所需的所有類別和方法，同時`System`輸出和異常處理等一般功能需要。

## 步驟1：指定Excel檔案的目錄

第一步是定義 Excel 檔案的儲存路徑。該路徑將用於以程式設計方式定位該檔案。

```csharp
//定義Excel檔案的目錄
string sourceDir = "Your Document Directory";
```

代替`"C:\\YourDirectory\\"`與文件的實際路徑。這確保了程序知道在哪裡可以找到`ThreadedCommentsSample.xlsx`.

## 第 2 步：載入工作簿

設定目錄後，我們現在可以載入 Excel 工作簿。這是透過創建一個新的`Workbook`物件並將檔案路徑傳遞給它。

```csharp
//載入 Excel 工作簿
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

如果在指定路徑中找不到該文件，則會拋出異常，因此請在繼續之前確保文件路徑正確。

## 第 3 步：存取所需的工作表

載入工作簿後，您需要存取包含線索註釋的工作表。在此範例中，我們將檢索工作簿的第一個工作表。

```csharp
//訪問工作簿中的第一個工作表
Worksheet worksheet = workbook.Worksheets[0];
```

如果您的註解位於不同的工作表中，只需相應地修改索引即可。例如，使用`Worksheets[1]`對於第二個工作表，依此類推。

## 第 4 步：檢索線索評論

若要檢索線索註釋，您需要指定包含註釋的儲存格。在這種情況下，我們關注的是細胞`A1`。方法`GetThreadedComments`用於獲取與特定單元格關聯的所有評論。

```csharp
//從儲存格 A1 取得線程註釋
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

這將傳回單元格 A1 的線程註釋集合。如果指定儲存格中不存在註釋，則集合將為空。

## 第 5 步：迭代評論並提取創建時間

檢索到線索評論後，下一步是迭代集合並提取相關詳細信息，包括每個評論的創建時間。我們可以透過循環來輕鬆實現這一點`ThreadedCommentCollection`.

```csharp
//循環瀏覽每個線程評論並顯示詳細信息
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

此程式碼將輸出評論的內容、作者姓名以及評論的建立時間。這`CreatedTime`屬性傳回最初建立評論時的時間戳記。

## 第 6 步：顯示確認訊息

成功閱讀線程註釋並顯示訊息後，在程式碼中包含確認訊息始終是一個好習慣。這有助於確認該過程是否正確執行。

```csharp
//確認訊息
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

程式碼執行完成後，此訊息將列印到控制台，確認進程運行沒有錯誤。

## 結論

現在您已經了解如何使用 Aspose.Cells for .NET 輕鬆讀取 Excel 工作表中串聯註解的建立時間。此功能對於追蹤協作環境中的評論和回饋非常有價值，為文件審閱流程提供必要的時間戳記。透過遵循本指南，您可以在 .NET 應用程式中有效地提取和利用註釋數據，從而增強您的工作流程並改善與團隊成員的協作。

## 常見問題解答

### 什麼是 Aspose.Cells for .NET？

Aspose.Cells for .NET 是一個綜合函式庫，使開發人員能夠在 .NET 應用程式中建立、操作和管理 Excel 檔案。它提供了以程式設計方式讀取、寫入和修改 Excel 檔案的強大工具。

### 如何下載 Aspose.Cells for .NET？

您可以從以下位置下載最新版本的 Aspose.Cells for .NET[阿斯普斯網站](https://releases.aspose.com/cells/net/).

### 有免費試用嗎？

是的，Aspose 提供 Aspose.Cells for .NET 免費試用版。您可以從以下位置下載試用版[免費試用頁面](https://releases.aspose.com/).

### 我可以訪問其他單元的評論嗎？

是的，您可以透過修改工作表中的儲存格參考來存取工作表中任何儲存格的線索註釋`GetThreadedComments`方法。只需改變`"A1"`到所需單元格的引用。

### 我可以在哪裡獲得 Aspose.Cells 的支援？

如果您需要支援或有疑問，請訪問[Aspose論壇](https://forum.aspose.com/c/cells/9)，您可以在其中找到答案或向社區尋求幫助。