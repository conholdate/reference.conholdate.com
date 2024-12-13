---
title: 在 Excel 檔案中的 PDF 中新增帶有命名目標的書籤
linktitle: 在 Excel 檔案中的 PDF 中新增帶有命名目標的書籤
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何使用 Aspose.Cells for .NET 從 Excel 檔案輕鬆建立互動式 PDF。本教學介紹如何新增指定目的地的書籤以增強 PDF 導航。
type: docs
weight: 10
url: /zh-hant/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## 介紹

瀏覽大型 PDF 檔案通常就像大海撈針一樣，尤其是當它們是從大量 Excel 電子表格產生時。 PDF 文件中的書籤提供了在文件相關部分之間跳轉的無縫方式，從而增強了使用者體驗。本詳細指南將引導您完成使用 Aspose.Cells for .NET 將帶有指定目標的書籤新增至從 Excel 檔案產生的 PDF 的過程。

## 使用 Aspose.Cells for .NET 的先決條件

在我們深入研究程式碼之前，必須確保您已設定成功實施所需的所有工具。以下是先決條件：

1. Visual Studio：推薦用於 .NET 開發的 IDE。確保它已在您的系統上安裝並正確配置。
2.  Aspose.Cells for .NET：以程式設計方式操作 Excel 檔案所需的核心程式庫。你可以[在這裡下載](https://releases.aspose.com/cells/net/)。如果您是 Aspose 新手，您可以從[免費試用](https://releases.aspose.com/).
3. .NET Framework：確保您使用的是相容版本的 .NET Framework。 Aspose.Cells 支援多個版本。
4. 基本 C# 知識：對 C# 的基本了解將有助於理解程式碼。

這些元件就位後，您就可以開始建立帶有書籤的 PDF 文件了！

## 設定您的項目

開發環境準備好後，您可以繼續在 Visual Studio 中建立新的 C# 專案。為了使用 Aspose.Cells 功能，您需要匯入所需的命名空間。

## 導入所需的命名空間

在 C# 文件的頂部添加以下內容`using`確保您的專案可以存取 Aspose.Cells for .NET 的語句：

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

這些命名空間提供對基本類別的訪問，這些類別將幫助您操作 Excel 資料並將其轉換為 PDF。

## 第 1 步：設定輸入和輸出檔案的目錄

第一步是定義輸入和輸出檔案目錄。這可確保來源 Excel 檔案和產生的 PDF 檔案正確定位。

```csharp
string sourceDir = "Your Document Directory";  // Excel 檔案的路徑
string outputDir = "Your Document Directory"; //輸出 PDF 的儲存路徑
```

這類似於在開始專案之前組織工作空間。

## 第 2 步：載入 Excel 工作簿

下一步是載入來源 Excel 檔案。 Aspose.Cells 讓您可以輕鬆地將 Excel 檔案載入到`Workbook`對象，提供對其所有工作表、儲存格和內容的存取。

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

這將打開工作簿並準備進行操作。現在您可以開始提取資料並將其格式化為 PDF。

## 第 3 步：訪問工作表

現在工作簿已加載，是時候存取書籤相關儲存格所在的工作表了。在此範例中，我們將使用第一個工作表：

```csharp
Worksheet ws = wb.Worksheets[0]; //訪問第一個工作表
```

此步驟將為您的書籤建立畫布。您為書籤引用的每個儲存格都將來自此工作表。

## 步驟 4：建立具有命名目的地的書籤

此時，我們就可以開始建立書籤了。書籤本質上是提供快速存取文件特定區域的連結。在此範例中，我們將為儲存格「C5」建立一個書籤。

### 為單一儲存格建立書籤

要建立書籤，您必須先造訪要連結到的儲存格。之後，您將建立一個`PdfBookmarkEntry`並將其與單元格的位置相關聯。

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; //書籤的文本
bookmarkEntry.Destination = cell;  //將書籤連結到單元格
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; //唯一的目的地名稱
```

將此視為在文件中標記一個點，只需單擊即可返回該點。您可以將任何文字指派給書籤（例如「C5 書籤」）並將其連結到特定儲存格。

### 新增子書籤以增強導航

您可以透過新增從主書籤分支出來的子書籤來增強使用者體驗。這些子書籤可以指向同一工作表中的不同區域或其他工作表。

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; //第一個子書籤的文本
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; //第二個子書籤的文本
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

這些子書籤充當文件導航的附加路標，就像書中的章節一樣。

### 將子書籤分組到主書籤下

若要建立層次結構，您可以在主書籤下方新增這些子書籤。這使用戶可以更輕鬆地導航到不同的部分。

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; //將子書籤加到主書籤
```

這將建立一個樹狀結構，其中每個書籤可以有多個子書籤。

## 第 5 步：使用書籤儲存 PDF

### 設定 PDF 儲存選項

在將文件儲存為 PDF 之前，我們需要指定儲存選項並確保包含書籤。我們將使用`PdfSaveOptions`為此目的。

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  //為 PDF 分配書籤
```

這告訴 Aspose.Cells 產生一個包含我們剛剛建立的書籤的 PDF。

### 儲存文件

現在書籤已設置，我們可以將工作簿另存為 PDF。

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

這將產生帶有可點擊書籤的最終 PDF，允許使用者快速跳到文件的特定部分。

## 結論

透過執行這些簡單的步驟，您已使用 Aspose.Cells for .NET 從 Excel 檔案成功建立了具有書籤和命名目標的 PDF。新增書籤的功能不僅增強了使用者體驗，還使大型文件中的導航更加有效率。無論您正在編寫報告、指南還是演示文稿，為關鍵部分添加書籤都將幫助您的讀者充分利用您的文件。

## 常見問題解答

### 什麼是 Aspose.Cells for .NET？
Aspose.Cells for .NET 是一個用於處理 Excel 檔案的強大 API，可讓您以程式設計方式建立、編輯和轉換 Excel 文件。您可以使用此工具輕鬆操作資料、圖表和格式。

### 如何獲得 Aspose.Cells for .NET 的免費試用版？
您可以從以下位置下載 Aspose.Cells for .NET 的免費試用版：[這裡](https://releases.aspose.com/).

### Aspose.Cells 可以使用哪些檔案格式？
Aspose.Cells 支援多種檔案格式，包括 XLSX、XLS、CSV、PDF 等。

### 我可以自動化在 PDF 中建立書籤的過程嗎？
是的！透過將 Aspose.Cells 整合到您的應用程式中，該流程可以完全自動化，讓您在工作流程中動態產生具有書籤的基於 Excel 的 PDF。

### 在哪裡可以獲得 Aspose.Cells for .NET 的支援？
您可以訪問[Aspose 論壇](https://forum.aspose.com/c/cells/9)提出問題或報告問題。