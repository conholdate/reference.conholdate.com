---
title: 使用 Aspose.PDF for .NET 在 PDF 中新增文字框
linktitle: 使用 Aspose.PDF for .NET 在 PDF 中新增文字框
second_title: Aspose.PDF for .NET API 參考
description: 這個綜合教學探討如何使用 Aspose.PDF for .NET 將 PDF 文件轉換為互動式表單。了解新增可自訂文字方塊欄位的逐步流程，從而提高使用者體驗和資料收集效率。
type: docs
weight: 290
url: /zh-hant/net/tutorials/pdf/mastering-pdf-forms/adding-text-boxes/
---
## 介紹

在當今的數位環境中，透過互動式文件增強使用者體驗至關重要。互動式 PDF 表單不僅簡化了資料收集，而且以靜態文件無法做到的方式吸引使用者。 Aspose.PDF for .NET 是一個功能強大的程式庫，旨在幫助開發人員輕鬆地將各種表單欄位整合到 PDF 文件中。其中，文字方塊對於以結構化方式收集使用者輸入特別有用。在本教學中，我們將逐步介紹使用 Aspose.PDF for .NET 將文字方塊新增至 PDF 的過程，確保您全面了解每個步驟。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1. C# 基礎知識：熟悉 C# 語法和結構將有助於您理解程式碼。
2. 已安裝 Aspose.PDF for .NET：從下列位置下載並安裝 Aspose.PDF 庫：[地點](https://releases.aspose.com/pdf/net/).
3. 開發環境：使用Visual Studio等IDE進行編碼和測試。
4. .NET Framework：請確保您安裝了相容版本的 .NET Framework。

滿足這些先決條件後，我們就可以開始編碼了！

### 打開你的IDE

啟動您首選的開發環境（建議使用 Visual Studio）。

### 建立一個新項目

為了簡單起見，選擇「建立新專案」並選擇控制台應用程式範本來設定新的 C# 專案。

### 安裝Aspose.PDF包

使用 NuGet Package Manager 將 Aspose.PDF 庫整合到您的專案中。在套件管理器控制台中，執行：

```bash
Install-Package Aspose.PDF
```

## 導入 Aspose.PDF 命名空間

在主程式文件的頂部（通常是`Program.cs`），包括以下命名空間：

```csharp
using System.IO;
using System;
using Aspose.Pdf.Forms;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
```

此設定讓您為接下來的令人興奮的任務做好準備！

現在一切準備就緒，讓我們分解一下在 PDF 文件中新增文字方塊的步驟。

## 第 1 步：定義您的文件目錄

首先，指定 PDF 文件所在的目錄。代替`"YOUR DOCUMENT DIRECTORY"`與實際路徑：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：開啟 PDF 文檔 

將 PDF 文件載入到實例中`Document`班級：

```csharp
Document pdfDocument = new Document(dataDir + "TextField.pdf");
```

確保`"TextField.pdf"`存在於您指定的目錄中。

## 第 3 步：建立文字方塊字段

現在，讓我們建立文字方塊欄位：

```csharp
TextBoxField textBoxField = new TextBoxField(pdfDocument.Pages[1], new Aspose.Pdf.Rectangle(100, 200, 300, 300));
```

- 一個新的`TextBoxField`為 PDF 的第二頁初始化物件。
- 這`Rectangle`參數使用座標 (x1, y1, x2, y2) 指定文字方塊的位置和大小。

## 步驟 4：設定文字方塊欄位的屬性 

使用以下屬性自訂文字方塊：

```csharp
textBoxField.PartialName = "textbox1";
textBoxField.Value = "Text Box";
```

- `PartialName`為文字方塊提供唯一識別碼。
- `Value`設定出現在框框中的預設文字。

## 第 5 步：自訂邊框

讓我們透過自訂邊框來增強文字方塊的外觀：

```csharp
Border border = new Border(textBoxField);
border.Width = 5; 
border.Dash = new Dash(1, 1);
textBoxField.Border = border;
textBoxField.Color = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Green);
```

- 建立邊框並設定其寬度。
- 對邊框套用虛線樣式。
- 為文字方塊指定綠色。

## 步驟 6：將文字方塊新增至文件中

現在，我們將文字方塊欄位新增至 PDF 文件：

```csharp
pdfDocument.Form.Add(textBoxField, 1);
```

該行將文字方塊合併到 PDF 的第一頁。

## 第7步：儲存修改後的PDF

最後，使用以下程式碼儲存變更：

```csharp
dataDir = dataDir + "TextBox_out.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nTextbox field added successfully.\nFile saved at " + dataDir);
```

此程式碼片段以新名稱儲存修改後的 PDF。檢查新建立的 PDF 的輸出路徑！

## 結論

恭喜！您已使用 Aspose.PDF for .NET 成功將文字方塊新增至 PDF 文件。此過程不僅增強了 PDF 的互動性，還顯著提高了使用者參與度。無論您是收集使用者輸入、進行調查或建立表單，文字方塊都可以提升 PDF 文件的功能。下次建立 PDF 時，請記住互動式欄位的強大功能以及使用 Aspose.PDF 實現它們是多麼容易。

## 常見問題解答

### 什麼是 Aspose.PDF for .NET？
Aspose.PDF for .NET 是一個綜合庫，可以在 .NET 應用程式中建立、操作和轉換 PDF 文件。

### 我可以免費試用 Aspose.PDF 嗎？
是的，Aspose 提供免費試用版，您可以訪問[這裡](https://releases.aspose.com/).

### 如何獲得 Aspose.PDF 支援？
您可以在以下位置找到支持和社區討論：[Aspose論壇](https://forum.aspose.com/c/pdf/10).

### 我可以使用 Aspose.PDF 新增哪些類型的表單欄位？
您可以新增文字方塊、複選框、建立互動式單選按鈕、下拉式清單等。

### 如何取得 Aspose.PDF 的臨時授權？
您可以向以下機構申請臨時許可證[這個連結](https://purchase.aspose.com/temporary-license/).