---
title: 在 PDF 檔案中新增圖像
linktitle: 在 PDF 檔案中新增圖像
second_title: Aspose.PDF for .NET API 參考
description: 了解如何使用 Aspose.PDF for .NET 以程式設計方式將影像新增至 PDF 檔案。這個綜合教程涵蓋了從設定環境到在特定頁面上渲染圖像的每個步驟。
type: docs
weight: 10
url: /zh-hant/net/tutorials/pdf/mastering-image-Processing/adding-image/
---
## 介紹

您是否曾經需要以程式設計方式將影像插入 PDF 檔案中？無論您是開發文件產生系統還是新增品牌元素，Aspose.PDF for .NET 都能讓這項任務變得簡單。在本教程中，我們將引導您完成將圖像新增至 PDF 檔案的步驟。

## 先決條件

在我們開始編碼之前，請確保您具備以下條件：

-  Aspose.PDF for .NET Library：從以下位置下載並安裝最新版本[Aspose下載](https://releases.aspose.com/pdf/net/).
- .NET 開發環境：您可以使用 Visual Studio 或您選擇的任何 IDE。
- C# 基礎：熟悉 C# 程式設計和物件導向原則會很有幫助。
- 範例文件：一個 PDF 文件和一個要插入的圖像（例如徽標）。

## 第 1 步：設定您的開發環境

首先在 IDE 中建立一個新的 C# 專案。匯入必要的命名空間以使用 Aspose.PDF：

```csharp
using System.IO;
using Aspose.Pdf;
using System;
```

這些命名空間將允許您有效地操作 PDF 文件並處理文件流。

## 第 2 步：開啟 PDF 文檔

找到您的 PDF 檔案並使用`Document`班級：

```csharp
//指定文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

//開啟 PDF 文檔
Document pdfDocument = new Document(dataDir + "AddImage.pdf");
```

確保更換`YOUR DOCUMENT DIRECTORY`與儲存 PDF 的實際路徑。

## 第 3 步：定義圖像座標

設定影像在 PDF 中的放置位置的座標：

```csharp
//定義影像的座標
int lowerLeftX = 100;
int lowerLeftY = 100;
int upperRightX = 200;
int upperRightY = 200;
```

這些座標確定圖像在頁面上的位置和大小。

## 步驟 4：選擇影像插入頁面

選擇 PDF 中要新增圖像的頁面。請記住，Aspose.PDF 對頁面使用基於 1 的索引：

```csharp
//取得 PDF 的第一頁
Page page = pdfDocument.Pages[1];
```

## 第 5 步：將圖像載入到流中

載入要插入流中的圖像：

```csharp
//將圖像載入到流中
using (FileStream imageStream = new FileStream(dataDir + "aspose-logo.jpg", FileMode.Open))
{
    //新增圖片到頁面資源
    page.Resources.Images.Add(imageStream);
}
```

確保影像檔案路徑正確。

## 第6步：儲存目前圖形狀態

在放置影像之前，請儲存目前圖形狀態：

```csharp
//儲存目前圖形狀態
page.Contents.Add(new Aspose.Pdf.Operators.GSave());
```

## 步驟 7：使用矩形和矩陣定義影像放置

創建一個`Rectangle`用於影像放置和`Matrix`用於縮放：

```csharp
//建立矩形和矩陣對象
Aspose.Pdf.Rectangle rectangle = new Aspose.Pdf.Rectangle(lowerLeftX, lowerLeftY, upperRightX, upperRightY);
Matrix matrix = new Matrix(new double[] { rectangle.URX - rectangle.LLX, 0, 0, rectangle.URY - rectangle.LLY, rectangle.LLX, rectangle.LLY });
```

## 步驟 8：應用矩陣變換

使用`ConcatenateMatrix`操作員正確定位影像：

```csharp
//應用矩陣變換
page.Contents.Add(new Aspose.Pdf.Operators.ConcatenateMatrix(matrix));
```

## 第 9 步：在 PDF 頁面上渲染圖像

使用渲染圖像`Do`操作員：

```csharp
XImage ximage = page.Resources.Images[page.Resources.Images.Count];
//在頁面上繪製圖像
page.Contents.Add(new Aspose.Pdf.Operators.Do(ximage.Name));
```

## 步驟10：恢復圖形狀態

渲染影像後，恢復圖形狀態：

```csharp
//恢復圖形狀態
page.Contents.Add(new Aspose.Pdf.Operators.GRestore());
```

## 第11步：儲存更新後的PDF文檔

最後儲存修改後的PDF：

```csharp
dataDir = dataDir + "AddImage_out.pdf";
//儲存更新後的文檔
pdfDocument.Save(dataDir);
```

## 結論

當分解為清晰的步驟時，使用 Aspose.PDF for .NET 將影像插入 PDF 是一個簡單的過程。此方法可讓您使用徽標、浮水印或其他圖像無縫地自訂 PDF。

## 常見問題解答

### 我可以將多個圖像新增到單一頁面嗎？
是的，您可以對要插入的每個圖像重複這些步驟。

### 如何控制插入影像的大小？
大小由您定義的矩形座標決定。

### 我可以插入其他文件類型（例如 PNG 或 GIF）嗎？
是的，Aspose.PDF 支援各種圖片格式，包括 PNG、GIF、BMP 和 JPEG。

### 可以動態新增圖片嗎？
絕對地！您可以透過提供檔案路徑或使用流來動態載入圖片。

### 我可以將圖像批量添加到多個頁面嗎？
是的，您可以循環瀏覽文件中的頁面並使用相同的方法新增圖像。