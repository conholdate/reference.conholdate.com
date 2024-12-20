---
title: 在.NET中使用Aspose.BarCode自訂條碼高度
linktitle: 自訂條碼高度
second_title: Aspose.BarCode .NET API
description: 了解如何使用 Aspose.BarCode 在 .NET 應用程式中有效調整一維條碼的高度。這個綜合教程提供了清晰的範例。
type: docs
weight: 13
url: /zh-hant/net/tutorials/barcode/guide-one-dimensional-barcode-types/customizing-barcode-height/
---
## 介紹

在建立需要產生條碼屬性的 .NET 應用程式（例如用於庫存管理或零售）時，對條碼屬性的精確控制至關重要。 Aspose.BarCode for .NET 是一個強大的工具包，可讓您輕鬆自訂條碼，包括調整其高度的能力。在本指南中，我們將為您提供使用 Aspose.BarCode 修改一維條碼高度的逐步過程。

## 先決條件

在開始之前，請確保您具備以下先決條件：

- 具有 .NET Framework 或 .NET Core 的開發環境。
-  Aspose.BarCode for .NET 函式庫，可以下載[這裡](https://releases.aspose.com/barcode/net/).
- 您選擇的程式碼編輯器用於編寫和運行您的程式碼。

## 入門

我們將首先導入使用 Aspose.BarCode 所需的必要命名空間。

### 導入命名空間

將以下 using 指令加入您的程式碼檔案：

```csharp
using Aspose.BarCode.Generation;
```

## 第 1 步：定義您的目錄路徑

建立要儲存產生的條碼影像的目錄路徑。確保將“您的目錄路徑”替換為系統上的實際路徑：

```csharp
string path = @"C:\YourDirectoryPath\"; //確保末端包含反斜杠
```

## 第 2 步：建立條碼產生器

建立一個實例`BarcodeGenerator`班級。在這裡，我們將使用`Code128`條碼類型並將值設為“ASPOSE”：

```csharp
BarcodeGenerator barcodeGen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
```

## 第三步：調整條碼高度

此步驟涉及使用以下命令修改條碼的高度`BarHeight`財產。我們將示範如何建立兩個具有不同高度（40 像素和 80 像素）的條碼影像。

```csharp
//將高度調整為 40 像素
barcodeGen.Parameters.Barcode.BarHeight.Pixels = 40;
barcodeGen.Save($"{path}BarHeight40Code128.png", BarCodeImageFormat.Png);

//將高度調整為80像素
barcodeGen.Parameters.Barcode.BarHeight.Pixels = 80;
barcodeGen.Save($"{path}BarHeight80Code128.png", BarCodeImageFormat.Png);
```

## 結論

在本教學中，您學習如何使用 Aspose.BarCode for .NET 調整一維條碼的高度。透過自訂各種條碼屬性的能力，您可以建立客製化的條碼影像來滿足您的特定應用要求。

## 常見問題解答

### Aspose.BarCode for .NET 支援哪些條碼類型？
 Aspose.BarCode 支援廣泛的條碼類型，包括 Code128、QR 碼、DataMatrix 等。您可以在以下位置找到完整的清單：[文件](https://reference.aspose.com/barcode/net/).

### 我還可以調整條碼的寬度嗎？
絕對地！您可以使用與調整高度類似的方法來修改一維條碼的寬度。

### Aspose.BarCode for .NET 有免費試用版嗎？
是的！您可以免費試用以探索 Aspose.BarCode for .NET。下載它[這裡](https://releases.aspose.com/barcode/net/).

### 我可以產生各種圖像格式的條碼嗎？
Aspose.BarCode for .NET 支援多種影像格式，例如 PNG、JPEG 和 TIFF，讓您可以選擇適合您需求的圖片。

### 在哪裡可以找到詳細的文件？
有關如何在專案中使用 Aspose.BarCode 的深入信息，請參閱[文件](https://reference.aspose.com/barcode/net/).