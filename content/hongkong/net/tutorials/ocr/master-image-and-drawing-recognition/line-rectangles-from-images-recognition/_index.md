---
title: 從影像辨識中提取直線矩形
linktitle: 從影像辨識中提取直線矩形
second_title: Aspose.OCR .NET API
description: 了解如何使用 Aspose.OCR 在 .NET 應用程式中實現光學字元辨識 (OCR)。本綜合指南將引導您完成提取已識別線條的矩形的過程。
type: docs
weight: 10
url: /zh-hant/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## 介紹

歡迎來到 Aspose.OCR for .NET 的世界，這是一款令人印象深刻的工具，旨在將光學字元辨識 (OCR) 整合到您的 .NET 應用程式中。無論您是經驗豐富的開發人員還是好奇的新手，本指南都將引導您從圖像中識別的文本中獲取表示線條的矩形的步驟。

## 先決條件

在開始之前，請確保您已具備以下條件：

- C# 和 .NET 開發的基礎知識。
- 像 Visual Studio 這樣的整合開發環境 (IDE)。
- 安裝了 Aspose.OCR for .NET 函式庫。你可以下載它[這裡](https://releases.aspose.com/ocr/net/).
- 包含用於識別的文字的範例圖像。

## 所需的命名空間

首先，您需要將必要的命名空間新增到您的專案中。在 C# 檔案的頂部包含以下行：

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

請依照下列步驟擷取 OCR 影像中線條的矩形。

## 第 1 步：設定您的文件目錄

指定圖像檔案所在的目錄：

```csharp
//定義文檔目錄的路徑
string dataDir = "Your Document Directory";
```

確保更換`"Your Document Directory"`與實際路徑。

## 步驟2：初始化Aspose.OCR

建立一個實例`AsposeOcr`類別來存取其功能：

```csharp
//初始化Aspose.OCR API
AsposeOcr api = new AsposeOcr();
```

## 第三步：指定影像路徑

定義要處理的影像檔案的完整路徑：

```csharp
//指定影像的完整路徑
string fullPath = dataDir + "sample.png";
```

## 第四步：辨識影像並取得直線矩形

現在，您可以使用`GetRectangles`提取已識別文字行矩形的方法：

```csharp
//擷取指定影像中線條的矩形
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## 第五步：輸出結果

最後，將每個偵測到的線矩形的座標列印到控制台：

```csharp
//顯示檢測到的矩形的座標
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## 結論

恭喜！您已使用 Aspose.OCR for .NET 成功擷取 OCR 影像中線條的矩形。該技術為您的應用程式中的文字擷取和處理提供了多種可能性。

## 常見問題解答

### 我可以將 Aspose.OCR for .NET 與任何類型的映像一起使用嗎？

是的，Aspose.OCR 支援各種圖像格式，為您的 OCR 應用程式提供靈活性。

### OCR辨識的準確率是多少？

Aspose.OCR採用先進的演算法實現高精度的文字識別，適用於多種場景。

### 有試用版嗎？

是的，您可以透過下載 Aspose.OCR for .NET 來探索其功能[免費試用](https://releases.aspose.com/).

### 在哪裡可以找到詳細的文件？

可以找到全面的文檔[這裡](https://reference.aspose.com/ocr/net/)，提供深入的資訊和指南。

### 需要進一步幫助或有疑問嗎？

加入討論[Aspose.OCR 論壇](https://forum.aspose.com/c/ocr/16)以獲得社區支持。