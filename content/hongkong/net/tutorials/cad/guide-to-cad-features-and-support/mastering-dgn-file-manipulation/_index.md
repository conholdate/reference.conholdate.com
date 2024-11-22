---
title: 在 .NET 中使用 Aspose.CAD 掌握 DGN 檔案操作
linktitle: 掌握 DGN 文件操作
second_title: Aspose.CAD .NET - CAD 和 BIM 檔案格式
description: 了解如何載入 DGN 檔案、迭代其元素、管理 2D 和 3D 實體以及將其匯出為光柵圖像，同時利用 Aspose.CAD 庫的強大功能。
type: docs
weight: 18
url: /zh-hant/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## 介紹

您是一位渴望將 DGN 檔案整合到您的應用程式中的 .NET 開發人員嗎？ Aspose.CAD for .NET 提供了專為處理 DGN 檔案格式而設計的強大程式庫。在本教程中，我們將探討如何有效處理 DGN 文件，包括支援的元素以及如何在 .NET 專案中操作它們。

## 先決條件

在開始之前，請確保您已進行以下設定：

- .NET 程式設計的基礎：熟悉 C# 或 VB.NET 將很有幫助。
- Visual Studio：安裝在您的電腦上用於專案開發。
-  CAD軟體 for .NET 函式庫：從下列位置下載[Aspose.CAD](https://releases.aspose.com/cad/net/).

## 步驟1：導入必要的命名空間

若要利用 Aspose.CAD 的功能，請先將所需的命名空間匯入到您的專案中。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## 步驟 2：載入 DGN 文件

首先將現有的 DGN 檔案載入到您的應用程式中。這是透過實例化一個來完成的`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    //在這裡繼續你的邏輯
}
```

## 步驟 3：迭代 DGN 元素

載入 DGN 檔案後，您可以迭代其元素。 Aspose.CAD 提供了多種 DGN 元素類型供您操作。

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    //處理每個元素
}
```

## 步驟 4：處理 2D 和 3D 實體

您可以區分 2D 和 3D DGN 元素。以下是如何有效地處理它們：

### 處理 2D 實體

您可以使用 switch-case 區塊管理先前支援的 2D 實體。

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        //在這裡添加您的處理邏輯
        break;
}
```

### 處理 3D 實體

同樣，依下列方式處理 3D 實體：

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        //在這裡添加您的處理邏輯
        break;
}
```

## 步驟 5：匯出 DGN 文件

操作 DGN 元素後，您可能想要將檔案匯出為光柵影像。這可以透過 Aspose.CAD 輕鬆完成。

```csharp
string outputFilePath = myDir + "Exported_Image.png"; //定義你的輸出路徑
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## 結論

在本教程中，我們學習如何使用 Aspose.CAD for .NET 來有效管理 DGN 檔案。透過遵循概述的步驟，您可以輕鬆處理 2D 和 3D DGN 元素並將它們匯出為光柵影像。這個功能強大的程式庫可以將 DGN 處理無縫整合到您的 .NET 應用程式中，從而增強您的專案能力。

## 常見問題解答

### 在哪裡可以找到 Aspose.CAD for .NET 的文檔？

提供全面的文檔[這裡](https://reference.aspose.com/cad/net/).

### 如何下載 Aspose.CAD for .NET？

您可以下載最新版本的庫[這裡](https://releases.aspose.com/cad/net/).

### Aspose.CAD for .NET 是否有免費試用版？

是的，可以免費試用[這裡](https://releases.aspose.com/).

### 如何取得 Aspose.CAD for .NET 的臨時授權？

您可以申請臨時許可證[這裡](https://purchase.conholdate.com/temporary-license/).

### 需要協助或有疑問嗎？

如需支援或提問，請造訪 Aspose.CAD 社區[支援論壇](https://forum.aspose.com/c/cad/19).