---
title: 使用 Aspose.Page for .NET 將 XPS 轉換為 PDF
linktitle: 將 XPS 轉換為 PDF
second_title: Aspose.Page .NET API
description: 了解如何使用強大的 Aspose.Page for .NET 程式庫將 XPS（XML 紙張規格）文件無縫轉換為 PDF（便攜式文件格式）。
type: docs
weight: 11
url: /zh-hant/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## 介紹

在本教學中，我們將探索如何使用多功能 Aspose.Page for .NET 程式庫將 XPS（XML 紙張規格）文件轉換為 PDF（便攜式文件格式）。這個強大的庫簡化了文件轉換並提供了各種自訂選項，使其成為開發人員的絕佳選擇。

## 先決條件

在我們開始之前，請確保您已具備以下條件：

-  Aspose.Page for .NET 函式庫：從下列位置下載並安裝 Aspose.Page for .NET 函式庫：[Aspose.Page 文檔](https://reference.aspose.com/page/net/).
  
- 開發環境：使用 Visual Studio 或其他相容 IDE 設定 .NET 開發環境。

- XPS 文件：準備好要轉換的 XPS 文件，並將其儲存在指定目錄中。

## 第 1 步：匯入所需的命名空間

首先匯入必要的命名空間以存取 Aspose.Page 功能：

```csharp
using Aspose.Page.XPS;
```

## 步驟2：初始化文檔目錄

定義儲存文件的目錄路徑：

```csharp
string dataDir = "Your Document Directory";
```

確保更換`"Your Document Directory"`包含 XPS 文件的目錄的實際路徑。

### 步驟 3：開啟 PDF 和 XPS Streams

接下來，初始化輸入 XPS 檔案和輸出 PDF 檔案的流：

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

確保您為文件設定了正確的路徑。

### 步驟 4：載入 XPS 文檔

現在，使用 Aspose.Page 庫載入 XPS 文件：

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### 步驟 5：設定 PDF 儲存選項

設定 PDF 的儲存選項，包括影像品質和壓縮參數：

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, //設定 JPEG 品質級別
    ImageCompression = PdfImageCompression.Jpeg, //對影像使用 JPEG 壓縮
    TextCompression = PdfTextCompression.Flate, //對文字套用 Flate 壓縮
    PageNumbers = new int[] { 1, 2, 6 } //指定要包含的頁碼
};
```

請根據您的要求隨意調整這些參數。

### 第6步：建立PDF渲染設備

建立PDF格式的渲染設備：

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### 步驟 7：將文件另存為 PDF

最後，使用指定的裝置和選項將 XPS 文件儲存為 PDF：

```csharp
document.Save(device, options);
```

## 結論

恭喜！您已使用 Aspose.Page for .NET 成功將 XPS 文件轉換為 PDF。該程式庫不僅簡化了文件轉換，還提供了處理各種格式的廣泛功能。

## 常見問題解答

### 我可以將多個 XPS 檔案轉換為單一 PDF 嗎？

絕對地！您可以迭代多個 XPS 文件，並按照相同的轉換步驟將它們合併到單一 PDF 文件中。

### Aspose.Page for .NET 支援哪些其他輸出格式？

除了 PDF 之外，Aspose.Page for .NET 還支援多種格式，包括 TIFF、JPEG 和 PNG。

### 如何自訂轉換後的 PDF 的外觀？

您可以調整其中的參數`PdfSaveOptions`對象，例如 JPEG 品質和壓縮設置，以獲得您想要的外觀。

### Aspose.Page for .NET 有試用版嗎？

是的，您可以免費試用 Aspose.Page for .NET[這裡](https://releases.aspose.com/).

### 在哪裡可以找到 Aspose.Page for .NET 的社群支援？

如需社區討論和支持，請訪問[Aspose.Page 論壇](https://forum.aspose.com/c/page/39).