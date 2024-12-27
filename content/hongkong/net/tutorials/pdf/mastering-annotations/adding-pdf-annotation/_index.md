---
title: 新增 PDF 註釋
linktitle: 新增 PDF 註釋
second_title: Aspose.PDF for .NET API 參考
description: 了解如何使用 Aspose.PDF for .NET 新增註解。本逐步教程涵蓋了從安裝庫到自訂註釋的所有內容。
type: docs
weight: 10
url: /zh-hant/net/tutorials/pdf/mastering-annotations/adding-pdf-annotation/
---
## 介紹

註釋豐富了 PDF 文檔，使其具有互動性和資訊性。無論您是與他人協作還是為讀者提供額外的見解，註釋都是必不可少的工具。在本教學中，我們將探討如何使用 Aspose.PDF for .NET 將 PDF 註解新增至 PDF 檔案中，引導您完成每個步驟，以確保您精通此流程。

## 先決條件

在我們深入研究程式碼之前，請確保您具備以下條件：

-  Aspose.PDF for .NET：從下列位置下載資料庫：[Aspose.PDF for .NET 下載頁面](https://releases.aspose.com/pdf/net/).
- 開發環境：使用 Visual Studio 或您選擇的任何 C# IDE。
- C# 基礎知識：假設熟悉 C# 程式設計。
- 範例 PDF 文件：您要新增註釋的 PDF 檔案。

如果您還沒有取得 Aspose.PDF 庫，您可以開始[免費試用](https://releases.aspose.com/)或購買一個[執照](https://purchase.aspose.com/buy).

## 導入必要的套件

在編碼之前，請確保導入所需的命名空間：

```csharp
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
```

這些命名空間提供 PDF 操作和註釋所需的類別和方法。

## 第 1 步：載入您的 PDF 文檔

首先載入要新增 PDF 註解的 PDF 文件。

```csharp
//指定文檔目錄的路徑。
string dataDir = "YOUR DATA DIRECTORY";
//載入 PDF 文件
Document pdfDocument = new Document(dataDir + "AddAnnotation.pdf");
```

此程式碼片段設定 PDF 檔案的目錄並將其載入到`Document`對象，以便進一步修改。

## 第 2 步：建立註釋

接下來，我們將創建一個`TextAnnotation`，非常適合添加評論或註釋。

```csharp
//建立文字註釋
TextAnnotation textAnnotation = new TextAnnotation(pdfDocument.Pages[1], new Aspose.Pdf.Rectangle(200, 400, 400, 600))
{
    Title = "Sample Annotation Title",
    Subject = "Sample Subject",
    Contents = "Sample contents for the annotation",
    Open = true,
    Icon = TextIcon.Key
};
```

- 位置和大小：`Rectangle`類別定義註解在頁面上的位置和尺寸。
- 屬性：可以設定註釋的標題、主題和內容。這`Open`屬性決定註釋是否預設顯示為開啟。
- 圖示:`TextIcon.Key`在註釋中加入視覺元素。

## 第 3 步：自訂註釋的外觀

透過自訂註釋的外觀來增強註釋的可見性。

```csharp
//自訂註解的邊框
Border border = new Border(textAnnotation)
{
    Width = 5,
    Dash = new Dash(1, 1)
};
textAnnotation.Border = border;
textAnnotation.Rect = new Aspose.Pdf.Rectangle(200, 400, 400, 600);
```

- 邊框：建立一個`Border`對象，設定其寬度和樣式（在本例中為虛線）以增強可見性。

## 步驟 4：將註解新增至 PDF 頁面

現在，是時候將註釋新增到 PDF 頁面了。

```csharp
//將註釋加入到頁面的註釋集合中
pdfDocument.Pages[1].Annotations.Add(textAnnotation);
```

此行將新建立的註釋新增至 PDF 的第一頁，並將其整合到文件中。

## 步驟5：儲存更新後的PDF文檔

最後，儲存文件以保留您的變更。

```csharp
//儲存更新的 PDF 文檔
dataDir = dataDir + "AddAnnotation_out.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nAnnotation added successfully.\nFile saved at " + dataDir);
```

此程式碼將修改後的文件另存為`AddAnnotation_out.pdf`，保留原始文件並確認註釋添加成功。

## 結論

在 PDF 中新增註解是一項強大的功能，使用 Aspose.PDF for .NET 可以輕鬆實現。無論是文件審查還是個人筆記，本指南都為您提供了有效建立和自訂註釋的知識。透過執行以下步驟，您可以增強 PDF 文件的互動性和實用性。

## 常見問題解答

### 我可以使用 Aspose.PDF for .NET 新增哪些類型的註解？
您可以新增各種註釋，包括文字、連結、突出顯示和圖章註釋。

### 我可以自訂註釋的外觀嗎？
絕對地！您可以修改註解的大小、顏色、邊框和圖示。

### 是否可以在一個頁面上新增多個註解？
是的，您可以為 PDF 中的任何頁面新增多個註解。

### 新增註釋後可以刪除嗎？
是的，可以使用以下命令刪除註釋`Annotations.Delete`Aspose.PDF提供的方法。

### 我需要許可證才能使用 Aspose.PDF for .NET 嗎？
是的，需要許可證才能解鎖所有功能並避免限制。您還可以獲得[臨時執照](https://purchase.aspose.com/temporary-license/)出於評估目的。