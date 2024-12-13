---
title: 調整工作簿中的壓縮等級
linktitle: 調整工作簿中的壓縮等級
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何使用 Aspose.Cells for .NET 調整壓縮等級來有效管理大型 Excel 檔案。本逐步指南涵蓋了從設定目錄到測量壓縮時間的所有內容，可協助您優化檔案大小並提高效能。
type: docs
weight: 14
url: /zh-hant/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## 介紹

管理大型 Excel 檔案可能是一項挑戰，尤其是在儲存和傳輸效率方面。幸運的是，檔案壓縮可以顯著減小這些檔案的大小，使它們更易於處理。如果您使用 Aspose.Cells for .NET，您可以輕鬆調整工作簿的壓縮等級。本指南將逐步引導您完成整個過程，並為程式碼的每個部分提供清晰的解釋。

## 先決條件

在我們深入研究程式碼之前，請確保您滿足以下先決條件：

1. C# 基礎知識：熟悉 C# 程式設計將有助於您更好地理解程式碼片段。
2.  Aspose.Cells 庫：從以下位置下載並安裝 Aspose.Cells 庫：[這裡](https://releases.aspose.com/cells/net/).
3. Visual Studio：執行程式碼需要像 Visual Studio 這樣的開發環境。
4. .NET Framework：確保您的專案設定了相容版本的 .NET Framework。

## 導入必要的套件

首先，您需要在 C# 專案中匯入必要的套件。在程式碼檔案的頂部新增以下行：

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

這些套件對於使用 Aspose.Cells 庫處理 Excel 檔案至關重要。這`Aspose.Cells`命名空間包含操作 Excel 檔案所需的所有類，而`Aspose.Cells.Xlsb`提供以 XLSB 格式儲存檔案的選項。

## 第 1 步：定義來源目錄和輸出目錄

首先，設定原始檔案所在的目錄以及要儲存輸出檔案的目錄：

```csharp
//定義來源目錄和輸出目錄
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

確保更換`"Your Document Directory\\"`與目錄的實際路徑。這確保您的程式可以找到它需要使用的檔案。

## 第 2 步：載入工作簿

接下來，載入要壓縮的工作簿：

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

在這裡，我們建立一個新的實例`Workbook`類別並載入現有的 Excel 文件。確保檔案名稱與來源目錄中的檔案名稱相符。

## 第 3 步：設定儲存選項

現在，配置工作簿的儲存選項：

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

這`XlsbSaveOptions`類別可讓您在以 XLSB 格式儲存工作簿時指定各種選項，包括壓縮等級。

## 步驟 4：測量 1 級壓縮時間

從第一個壓縮等級開始，測量保存工作簿所需的時間：

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此程式碼片段將壓縮類型設為等級 1，儲存工作簿並測量經過的時間。

## 第 5 步：測量 6 級的壓縮時間

接下來，測試 6 級壓縮的效能：

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此步驟與上一步類似，但壓縮等級更高。

## 第 6 步：測量 9 級的壓縮時間

最後，評估最高壓縮等級的性能：

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

此步驟將壓縮等級設為等級 9，您可能會看到檔案大小顯著減少，但處理時間可能會更長。

## 第7步：最終輸出

完成所有壓縮等級後，輸出一則訊息，表示該過程已成功完成：

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

這個簡單的行確認您的程式已正常執行。

## 結論

使用 Aspose.Cells for .NET 調整工作簿的壓縮等級是一個簡單的過程，可以顯著改善檔案大小和效能。透過遵循本指南中概述的步驟，您可以在應用程式中有效地實施壓縮，從而增強 Excel 文件管理功能。

## 常見問題解答

### 什麼是 Aspose.Cells？  
Aspose.Cells 是一個強大的 .NET 程式庫，可讓開發人員建立、操作和轉換 Excel 文件，而無需 Microsoft Excel。

### 如何安裝 Aspose.Cells？  
您可以從以下位置下載並安裝 Aspose.Cells：[阿斯普斯網站](https://releases.aspose.com/cells/net/).

### 有哪些可用的壓縮等級？  
Aspose.Cells 支援多種壓縮級別，範圍從 1 級（最低壓縮）到 9 級（最高壓縮）。

### 我可以免費測試 Aspose.Cells 嗎？  
是的！您可以免費試用 Aspose.Cells[這裡](https://releases.aspose.com/).

### 在哪裡可以找到對 Aspose.Cells 的支援？  
如有任何疑問或支持，請造訪 Aspose 支援論壇[這裡](https://forum.aspose.com/c/cells/9).