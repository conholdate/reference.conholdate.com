---
title: Aspose.Slides .NET 中資料點上的圖表標記選項
linktitle: Aspose.Slides .NET 中資料點上的圖表標記選項
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 了解如何使用 Aspose.Slides for .NET 透過自訂標記選項來增強 PowerPoint 圖表。本逐步指南涵蓋先決條件、圖表建立、資料點格式設定等。
type: docs
weight: 11
url: /zh-hant/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## 介紹

將視覺輔助工具納入簡報對於有效的溝通至關重要。 Aspose.Slides for .NET 提供了用於建立和自訂圖表的強大工具，使開發人員能夠增強其資料演示。其中一項突出的功能是能夠在數據點上使用圖表標記選項，從而可以精確自訂具有專業外觀的圖表。本文將引導您完成實現此目標所需的每個步驟。

## 先決條件

在繼續之前，請確保滿足以下條件：

-  Aspose.Slides for .NET 已安裝：從下列位置下載[這裡](https://releases.aspose.com/slides/net/).
- 基本設定：工作目錄中的示範文件，例如「Test.pptx」。
- 開發環境：Visual Studio 或同等環境，針對 .NET 進行配置。

## 導入所需的命名空間

將必要的命名空間添加到您的專案中以實現無縫開發：

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 第 1 步：在簡報中建立圖表

首先在簡報的第一張投影片上建立預設圖表：

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

這增加了一個`LineWithMarkers`將圖表新增到具有指定尺寸的投影片。

## 步驟 2：檢索圖表資料工作表索引

預設圖表資料工作表索引對於進一步自訂至關重要：

```csharp
int defaultWorksheetIndex = 0;
```

## 第 3 步：存取圖表資料工作簿

若要操作圖表數據，請擷取關聯的工作簿：

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## 步驟 4：配置圖表系列並新增資料點

清除預設系列並為您的系列新增資料點：

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

//將資料點加入系列中
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## 步驟 5：將圖片填充應用於資料點標記

自訂圖像可以使資料標記在視覺上更具吸引力：

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

//為標記設定自訂影像
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## 第 6 步：自訂標記尺寸

修改標記的大小以增強可見性：

```csharp
series.Marker.Size = 20;
```

## 步驟 7：儲存更新的簡報

將自訂簡報儲存到您所需的位置：

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## 結論

Aspose.Slides for .NET 為開發人員提供了創建具有豐富自訂選項的專業圖表的工具。透過利用圖表標記選項，您可以顯著增強簡報的視覺吸引力和清晰度。本逐步指南確保即使是複雜的自訂也可以輕鬆實施。

## 常見問題解答

### 我可以使用任何圖像格式進行標記自訂嗎？
是的，Aspose.Slides 支援各種圖片格式，包括 JPEG、PNG 和 BMP，用於標記自訂。

### 創建後如何更改圖表類型？
若要變更圖表類型，請訪問`chart.Type`屬性並分配不同的`ChartType`.

### Aspose.Slides for .NET 與舊版 PowerPoint 相容嗎？
是的，它支援向後相容舊的 PowerPoint 格式，確保多功能性。

### 我可以動態更新圖表資料嗎？
絕對地。使用`IChartDataWorkbook`以程式設計方式更新圖表資料。

### 我可以在哪裡找到更多資源？
探索[Aspose.Slides 文檔](https://reference.aspose.com/slides/net/)或加入[社群論壇](https://forum.aspose.com/)尋求支持。