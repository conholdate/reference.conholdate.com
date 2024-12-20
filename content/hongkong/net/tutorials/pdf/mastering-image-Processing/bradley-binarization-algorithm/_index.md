---
title: Bradley 二值化演算法
linktitle: Bradley 二值化演算法
second_title: Aspose.PDF for .NET API 參考
description: 了解如何使用 Aspose.PDF for .NET 中的 Bradley 二值化演算法將 PDF 頁面轉換為高品質的二進位 TIFF 影像。本逐步指南包括程式碼範例。
type: docs
weight: 30
url: /zh-hant/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## 介紹

在本教學中，我們將引導您完成使用 Bradley 二值化演算法將 PDF 頁面轉換為 TIFF 影像的過程。 Aspose.PDF for .NET 簡化了此任務，讓您可以輕鬆自動化和簡化文件工作流程。

## 先決條件

在我們開始之前，請確保您具備以下條件：

-  Aspose.PDF for .NET：從下列位置下載資料庫[這裡](https://releases.aspose.com/pdf/net/).
- Visual Studio（或任何 C# IDE）。
- C# 基礎知識。
- 有效的許可證或[臨時執照](https://purchase.aspose.com/temporary-license/)來自阿斯珀斯。

## 第 1 步：設定您的項目

首先，在 IDE 中建立一個新的 C# 專案並匯入必要的命名空間：

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## 第 2 步：定義文檔目錄

指定 PDF 文件所在目錄的路徑以及 TIFF 影像的輸出路徑：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // PDF 檔案的路徑
```

該目錄將儲存來源 PDF 和轉換後的 TIFF 檔案。

## 第 3 步：載入 PDF 文檔

開啟您要轉換的PDF文件：

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

代替`PageToTIFF.pdf`與您的 PDF 檔案的名稱。

## 步驟 4：指定輸出路徑

定義產生的 TIFF 檔案的輸出路徑：

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## 第5步：設定影像解析度

設定 TIFF 影像的解析度。較高的 DPI 將產生更好的影像品質：

```csharp
Resolution resolution = new Resolution(300);
```

## 步驟 6：設定 TIFF 設定

配置 TIFF 影像的設置，包括壓縮和色彩深度：

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

使用 1bpp（每像素 1 位元）準備影像以進行二進位輸出。

## 步驟 7：建立 TIFF 設備

建立一個將處理轉換的 TIFF 設備：

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## 步驟 8：將 PDF 頁面轉換為 TIFF

將 PDF 的第一頁轉換為 TIFF 影像：

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## 步驟 9：應用 Bradley 二值化演算法

現在，應用 Bradley 演算法將灰階 TIFF 影像轉換為二值影像：

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

這`BinarizeBradley`方法採用兩個文件流（輸入和輸出）和一個閾值。根據需要調整閾值以獲得最佳結果。

## 第10步：確認轉換成功

最後確認轉換成功：

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## 結論

恭喜！您已成功將 PDF 頁面轉換為 TIFF 影像，並使用 Aspose.PDF for .NET 套用 Bradley 二值化演算法。此過程對於文件歸檔、OCR 和其他專業應用程式至關重要。憑藉高品質的解析度和高效的壓縮，您的文件影像將清晰且尺寸易於管理。

## 常見問題解答

### 什麼是布拉德利演算法？
Bradley 演算法是一種二值化技術，透過根據周圍環境確定每個像素的自適應閾值，將灰階影像轉換為二值影像。

### 我可以使用此方法將多個 PDF 頁面轉換為 TIFF 嗎？
是的，您可以修改`Process`方法會循環遍歷文件中的所有頁面進行轉換。

### 將 PDF 轉換為 TIFF 的最佳解析度是多少？
對於高品質影像，通常建議使用 300 DPI 的分辨率，但您可以根據您的特定需求進行調整。

### 顏色深度中的 1bpp 意味著什麼？
1bpp（每像素 1 位元）表示影像將是黑白的，每個像素要麼全黑，要麼全白。

### Bradley演算法適合OCR嗎？
是的，Bradley 演算法經常用於 OCR 預處理，因為它可以增強掃描文件中文字的對比度，從而提高識別準確性。