---
title: 使用 Aspose.Drawing for .NET 進行局部轉換的指南
linktitle: 使用 Aspose.Drawing 進行局部轉換的指南
second_title: Aspose.Drawing .NET API - System.Drawing.Common 的替代方案
description: 使用 Aspose.Drawing 透過本地轉換提升 .NET 應用程式的視覺功能。這個綜合教程將引導您完成透過應用變換矩陣創建令人驚嘆的圖形的過程。
type: docs
weight: 11
url: /zh-hant/net/tutorials/drawing/transformations/guide-to-local-transformation/
---
## 介紹

Aspose.Drawing for .NET 使開發人員能夠透過本機轉換創建複雜的圖形。本簡短指南將引導您逐步設定本地轉換。

## 先決條件

1.  Aspose.Drawing for .NET：從以下位置下載並安裝它[這裡](https://releases.aspose.com/drawing/net/).
2. 文件目錄：選擇儲存影像的目錄。
3. 基本 .NET 知識：熟悉 C# 和圖形程式設計概念。

## 導入命名空間

首先將必要的命名空間匯入到您的 C# 專案中：

```csharp
using System.Drawing;
using System.Drawing.Drawing2D;
```

## 第 1 步：建立位圖

```csharp
Bitmap bitmap = new Bitmap(1000, 800, System.Drawing.Imaging.PixelFormat.Format32bppPArgb);
```

## 第 2 步：建立圖形對象

```csharp
Graphics graphics = Graphics.FromImage(bitmap);
graphics.Clear(Color.FromKnownColor(KnownColor.Gray));
```

### 第 3 步：建立 GraphicsPath

畫一個橢圓：

```csharp
GraphicsPath path = new GraphicsPath();
path.AddEllipse(300, 300, 400, 200);
```

### 第 4 步：應用局部轉換

設定旋轉變換矩陣：

```csharp
Matrix matrix = new Matrix();
matrix.RotateAt(45, new Point(500, 400));
path.Transform(matrix);
```

### 步驟5：繪製變換後的路徑

用筆在圖形物件上繪製路徑：

```csharp
Pen pen = new Pen(Color.Blue, 2);
graphics.DrawPath(pen, path);
```

### 步驟6：儲存轉換後的影像

```csharp
bitmap.Save(@"Your Document Directory\CoordinateSystemsTransformations\LocalTransformation_out.png");
```

## 結論

透過執行這些步驟，您可以輕鬆地使用 Aspose.Drawing 實現本機轉換，豐富 .NET 應用程式的視覺化功能。

## 常見問題解答

### 我可以按順序套用多個轉換嗎？  
是的，您可以使用矩陣進行鍊式變換。

### 它適合複雜的圖形應用程式嗎？  
確實！ Aspose.Drawing支援廣泛的圖形操作。

### 還有其他類型的轉換嗎？  
是的，它支援平移、縮放和傾斜。

### 異常狀況如何處理？  
實作錯誤處理並查閱[文件](https://reference.aspose.com/drawing/net/)以獲得指導。

### 我可以在購買前試用嗎？  
是的，探索一個[免費試用](https://releases.aspose.com/).