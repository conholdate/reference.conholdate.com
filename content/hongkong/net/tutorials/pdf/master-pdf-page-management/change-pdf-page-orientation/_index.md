---
title: 更改 PDF 頁面方向
linktitle: 更改 PDF 頁面方向
second_title: Aspose.PDF for .NET API 參考
description: 了解如何使用 Aspose.PDF for .NET 輕鬆調整 PDF 檔案的頁面方向。本逐步指南提供了有關載入、旋轉和儲存文件的清晰說明。
type: docs
weight: 10
url: /zh-hant/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## 介紹

您是否遇到過頁面方向完全錯誤的 PDF 檔案？無論是掃描錯誤的文檔還是僅需要不同佈局的文檔，調整方向都可以帶來截然不同的效果。幸運的是，Aspose.PDF for .NET 提供了一種強大且使用者友好的方式來操作 PDF 文件，包括更改頁面方向。在本指南中，我們將逐步引導您完成整個過程，無論您是想從縱向切換到橫向，還是反之亦然。

## 先決條件

在我們深入了解詳細資訊之前，請確保您已準備好以下內容：

-  Aspose.PDF for .NET：請確定您已安裝 Aspose.PDF 庫。如果您還沒有這樣做，您可以[在這裡下載](https://releases.aspose.com/pdf/net/).
- .NET 開發環境：您可以使用 Visual Studio、JetBrains Rider 或您喜歡的任何其他 IDE 進行 .NET 開發。
- C# 基礎：熟悉 C# 將幫助您更輕鬆地進行操作。
- PDF 檔案：準備好範例 PDF 檔案以供測試。您可以建立一個或線上下載範例。

如果您剛開始，請考慮嘗試使用 Aspose.PDF[免費臨時許可證](https://purchase.aspose.com/temporary-license/)在決定之前[購買完整版](https://purchase.aspose.com/buy).

## 導入命名空間

要操作 PDF 頁面，您首先需要在 C# 專案中匯入必要的命名空間。在程式碼檔案的頂部新增以下行：

```csharp
using System.IO;
using Aspose.Pdf;
```

現在我們已經完成了所有設置，讓我們開始吧！

## 第 1 步：載入 PDF 文檔

第一步是載入您要修改的 PDF 檔案。使用`Document`來自 Aspose.PDF 命名空間的類別：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

確保更換`"YOUR DOCUMENT DIRECTORY"`與 PDF 檔案的實際路徑。

## 第 2 步：循環瀏覽每一頁

接下來，我們將循環瀏覽 PDF 文件中的每個頁面。這允許我們將方向更改應用到所有頁面：

```csharp
foreach (Page page in doc.Pages)
{
    //操縱每個頁面
}
```

## 第 3 步：造訪頁面的 MediaBox

每個 PDF 頁面都有一個`MediaBox`定義了它的邊界。我們需要訪問它來檢查當前方向並進行調整：

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

這`MediaBox`提供頁面的尺寸，包括寬度和高度。

## 第 4 步：交換寬度和高度

若要變更頁面方向，我們將交換寬度和高度值。此調整將改變頁面的尺寸：

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

在這裡，我們計算新的尺寸並重新定位左下角（`LLY`） 因此。

## 第 5 步：更新 MediaBox 和 CropBox

現在我們有了新的維度，我們將把這些變更應用到`MediaBox`和`CropBox`確保頁面正確顯示：

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## 第 6 步：旋轉頁面

為了完成方向更改，我們將旋轉頁面。這對 Aspose.PDF 來說很簡單：

```csharp
page.Rotate = Rotation.on90; //旋轉90度
```

該行有效地將頁面翻轉到所需的方向。

## 第 7 步：儲存輸出 PDF

修改所有頁面的方向後，將更新的文件儲存到新文件中：

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

確保提供新的檔案名稱以避免覆蓋原始文件。

## 結論

現在你就得到它了！使用 Aspose.PDF for .NET 變更 PDF 檔案的頁面方向是一個簡單的過程。透過載入文件、循環瀏覽頁面、更新 MediaBox 和儲存文件，您可以輕鬆調整佈局以滿足您的需求。無論您是要修正掃描品質不佳的文件還是要格式化簡報的頁面，本指南都可以幫助您有效率地完成工作。

## 常見問題解答

### 我可以旋轉 PDF 中的特定頁面而不是所有頁面嗎？  
是的，您可以修改循環以透過索引定位特定頁面，而不是迭代所有頁面。

### 什麼是`MediaBox`?  
這`MediaBox`定義 PDF 檔案中頁面的大小和形狀，確定內容的放置位置。

### Aspose.PDF for .NET 是否可以與其他文件格式一起使用？  
是的，Aspose.PDF 可以處理各種檔案格式，包括 HTML、XML、XPS 等。

### 有沒有適用於 .NET 的 Aspose.PDF 免費版本？  
是的，您可以從[免費試用](https://releases.aspose.com/)或請求[臨時執照](https://purchase.aspose.com/temporary-license/).

### 儲存後我可以撤銷更改嗎？  
儲存文件後，所做的變更將是永久性的。建議處理原始文件的副本或保留原始文件的備份。