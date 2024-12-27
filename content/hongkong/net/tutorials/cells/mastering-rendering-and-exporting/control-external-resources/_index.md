---
title: 使用 Aspose.Cells for .NET 控制外部資源
linktitle: 使用 Aspose.Cells for .NET 控制外部資源
second_title: Aspose.Cells .NET Excel 處理 API
description: 使用 Aspose.Cells for .NET 釋放 Excel 到 PDF 轉換的全部潛力。在這份綜合指南中，了解如何管理影像等外部資源，確保您的 PDF 準確反映您的格式要求。
type: docs
weight: 12
url: /zh-hant/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## 介紹

在當今的數位環境中，將 Excel 電子表格轉換為 PDF 文件是一項常見且重要的任務。無論您是在準備報告、財務資料或簡報資料，確保您的 PDF 反映您想要的格式至關重要。 Aspose.Cells for .NET 提供了一個功能強大的程式庫，可讓您詳細控制此轉換過程，特別是在處理映像等外部資源時。在本指南中，我們將探討如何在使用 Aspose.Cells 將 Excel 轉換為 PDF 的過程中有效管理外部資源。讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您已準備好以下內容：

1. Visual Studio 或任何與 .NET 相容的 IDE：這將是您的開發環境。
2.  Aspose.Cells for .NET：如果您尚未安裝，請造訪[Aspose下載](https://releases.aspose.com/cells/net/)頁面取得最新版本。
3. C# 基礎知識：熟悉 C# 將很有幫助。如果您需要澄清任何概念，請隨時查找。
4. 範例 Excel 檔案：準備一個 Excel 文件，例如“samplePdfSaveOptions_StreamProvider.xlsx”，其中包含您要轉換的外部資源。
5. 用於測試的映像檔：在轉換過程中使用「newPdfSaveOptions_StreamProvider.png」等映像檔作為外部資源。

## 導入必要的套件

首先，您需要從 Aspose.Cells 庫匯入所需的命名空間。在 C# 檔案頂部新增以下 using 指令：

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

這些命名空間為您的任務提供了必要的類別和方法。

## 第 1 步：建立流程提供者類

首先，建立一個流提供者類別來實現`IStreamProvider`介面.該類別將使您能夠控制外部資源的載入方式。

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        //將圖像載入到記憶體流中
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream：當流關閉時呼叫此方法，目前正在記錄偵錯訊息。
- InitStream：此方法以位元組數組的形式讀取外部映像文件，將其轉換為記憶體流，並將其分配給`options.Stream`財產。

## 第 2 步：設定來源目錄和輸出目錄

接下來，定義 Excel 檔案和輸出 PDF 的目錄。

```csharp
//原始碼目錄
string sourceDir = "Your Document Directory";
//輸出目錄
string outputDir = "Your Document Directory";
```

代替`"Your Document Directory"`與您的系統上文件所在的實際路徑。

## 第 3 步：載入 Excel 文件

現在，載入要從中建立 PDF 的 Excel 檔案。

```csharp
//載入包含外部映像的來源 Excel 文件
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

這`Workbook`Aspose.Cells 中的類別代表您的 Excel 文件，其中可能包含各種外部資源，例如圖片。

## 步驟 4：設定 PDF 儲存選項

將工作簿儲存為 PDF 之前，請指定所需的儲存選項。

```csharp
//指定 PDF 儲存選項 - Stream Provider
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true //將每張紙保存在新頁面上
};
```

這將創建一個實例`PdfSaveOptions`，允許您自訂 PDF 格式。這`OnePagePerSheet`選項可確保每個 Excel 工作表顯示在最終 PDF 中的單獨頁面上。

## 第 5 步：分配您的串流媒體供應商

連接您的`Workbook`實例與`MyStreamProvider`您之前建立的類別。

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

此行可確保每當轉換過程中遇到外部資源時，您的自訂提供者都會相應地管理它們。

## 步驟 6：將工作簿另存為 PDF

現在，將 Excel 工作簿儲存為 PDF。

```csharp
//將工作簿儲存為 PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

透過致電`Save`工作簿物件上的方法並傳遞輸出目錄和 PDF 選項，您可以將 Excel 檔案轉換為格式良好的 PDF。

## 第七步：確認執行成功

最後，確認該過程已成功完成是一個很好的做法。

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

此訊息將通知您有關操作的狀態，並提供有用的回饋。

## 結論

您現在已經掌握了使用 Aspose.Cells 在 Excel 到 PDF 轉換過程中控制外部資源的流程！透過執行這些步驟，您可以確保文件準確地包含圖像和其他外部元素，從而每次都能獲得精美的最終產品。

## 常見問題解答

### 什麼是 Aspose.Cells？
Aspose.Cells 是一個針對 .NET 開發人員的強大函式庫，可建立、操作、轉換和呈現各種格式的 Excel 檔案。

### 如何下載 Aspose.Cells？
您可以從以下位置下載最新版本[下載連結](https://releases.aspose.com/cells/net/).

### 可以免費試用 Aspose.Cells 嗎？
是的！您可以存取免費試用版[免費試用頁面](https://releases.aspose.com/).

### 在哪裡可以找到對 Aspose.Cells 的支援？
對於與支援相關的查詢，請訪問[Aspose 支援論壇](https://forum.aspose.com/c/cells/9).

### 我如何獲得 Aspose.Cells 的臨時許可證？
您可以申請臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).
