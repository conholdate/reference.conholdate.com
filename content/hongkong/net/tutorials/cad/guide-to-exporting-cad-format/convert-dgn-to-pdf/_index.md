---
title: 在 Aspose.CAD for .NET 中將 DGN 轉換為 PDF
linktitle: 在 Aspose.CAD for .NET 中將 DGN 轉換為 PDF
second_title: Aspose.CAD .NET - CAD 和 BIM 檔案格式
description: 了解如何使用強大的 Aspose.CAD .NET 程式庫輕鬆將 DGN 檔案轉換為 PDF。本逐步指南是為各個層級的開發人員設計的。
type: docs
weight: 12
url: /zh-hant/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## 介紹

瀏覽 CAD 檔案世界可能具有挑戰性，但藉助 Aspose.CAD for .NET，開發人員可以輕鬆操作和轉換各種 CAD 格式。常見的需求是將 DGN 檔案轉換為 PDF，我們將在本教學中逐步探討這一點。

## 先決條件

若要繼續操作，請確保您具備以下條件：

- 基本精通 C# 和 .NET 框架。
- 安裝了 Aspose.CAD for .NET 函式庫。你可以下載它[這裡](https://releases.aspose.com/cad/net/).
- 範例 DGN 檔案（例如 Nikon_D90_Camera.dgn）。 

## 第 1 步：匯入所需的命名空間

首先在 C# 專案中匯入相關命名空間：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 步驟 2：載入 DGN 文件

指定 DGN 檔案的目錄並使用以下程式碼載入它：

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    //額外的處理將在此處進行...
}
```

## 步驟 3：配置光柵化選項

接下來，設定光柵化選項來定義 DGN 在 PDF 中的渲染方式：

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, //根據需要調整寬度
    PageHeight = 300, //根據需要調整高度
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## 第 4 步：建立 PDF 選項

定義 PDF 選項，整合先前配置的光柵化設定：

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 步驟 5：將 DGN 儲存為 PDF

最後，使用您配置的選項將 DGN 檔案另存為 PDF：

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## 結論

恭喜！您已使用 Aspose.CAD for .NET 成功將 DGN 檔案轉換為 PDF。這個簡單的教學將指導您載入 DGN 檔案、設定光柵化選項以及將輸出儲存為 PDF。

## 常見問題解答

### 我需要具備 CAD 知識才能使用 Aspose.CAD 嗎？  
絕對地！ Aspose.CAD 旨在簡化複雜的 CAD 任務，使所有開發人員都可以使用它，無論他們的 CAD 知識如何。

### 在哪裡可以找到有關 Aspose.CAD 的更多資源和文件？  
您可以在以下位置探索全面的指南和範例[Aspose.CAD 文檔](https://reference.aspose.com/cad/net/).

### Aspose.CAD 是否有免費試用版？  
是的，可以獲得免費試用[這裡](https://releases.aspose.com/).

### 如何取得 Aspose.CAD 的臨時授權？  
您可以申請臨時許可證[這裡](https://purchase.conholdate.com/temporary-license/).

### 需要協助或有疑問嗎？  
加入對話[Aspose.CAD論壇](https://forum.aspose.com/c/cad/19)以獲得社區支持和查詢。