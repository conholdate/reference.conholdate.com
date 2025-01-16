---
title: 使用 Aspose.Slides for .NET 繪製圖表中的趨勢線
linktitle: 使用 Aspose.Slides for .NET 繪製圖表中的趨勢線
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 了解如何使用 Aspose.Slides for .NET 在圖表中新增和自訂趨勢線。此綜合指南涵蓋指數、線性、對數、多項式和移動平均趨勢線，以增強您的資料視覺化。
type: docs
weight: 12
url: /zh-hant/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## 介紹  

在圖表中加入趨勢線是分析資料趨勢和預測未來值的關鍵技術。透過 Aspose.Slides for .NET，您可以無縫地向演示圖表添加和自訂趨勢線，從而增強資料視覺化。本指南提供了使用 Aspose.Slides for .NET 將趨勢線新增至 PowerPoint 簡報中的各種圖表類型的詳細演練。  

## 先決條件  

在我們深入實施之前，請確保您具有以下設定：  

1.  Aspose.Slides for .NET：從以下位置下載並安裝該程式庫[下載頁面](https://releases.aspose.com/slides/net/).  
2. 開發環境：使用Visual Studio等IDE進行編碼。  
3. 基本 C# 知識：需要熟悉 C# 程式設計才能學習本教學。  

## 導入所需的命名空間  

首先，將必要的命名空間匯入到您的專案中：  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 第 1 步：設定簡報  

首先，初始化一個空簡報。這將作為圖表的容器。  

```csharp
string dataDir = "Your/Documents/Directory";

//確保目錄存在
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

//建立新簡報
Presentation presentation = new Presentation();
```

## 第 2 步：將圖表新增至投影片  

現在，新增投影片並包含聚集長條圖以視覺化您的資料。  

```csharp
//新增空白投影片
ISlide slide = presentation.Slides[0];

//添加聚集長條圖
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## 第 3 步：填入圖表數據  

使用範例資料填入圖表。  

```csharp
//存取預設圖表資料工作簿
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

//更新預設類別和系列值
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## 第四步：新增趨勢線  

### 指數趨勢線  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### 線性趨勢線  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### 對數趨勢線  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### 移動平均趨勢線  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### 多項式趨勢線  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### 功率趨勢線  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## 第 5 步：儲存簡報  

最後，儲存演示文稿，並將所有趨勢線新增至圖表。  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## 結論  

使用 Aspose.Slides for .NET，在圖表中加入趨勢線成為一項簡單的任務。此功能使您能夠有效地呈現數據趨勢並為您的簡報添加專業風格。依照上述步驟合併各種趨勢線類型並提升資料視覺化效果。  

## 常見問題解答  

### 我可以自訂趨勢線的外觀嗎？  
是的，您可以使用以下命令自訂趨勢線的顏色、粗細和樣式`Format.Line`財產。  

### 是否支援其他圖表類型？  
是的，Aspose.Slides for .NET 支援各種圖表類型，包括長條圖、圓餅圖和折線圖。  

### 如何顯示方程式和 R 平方值？  
使能夠`DisplayEquation`和`DisplayRSquaredValue`趨勢線的屬性以在圖表上顯示這些值。  

### 我可以將 Aspose.Slides for .NET 與其他語言一起使用嗎？  
是的，該程式庫與任何 .NET 支援的語言相容，包括 VB.NET 和 F#。  

### 我可以在哪裡找到更多文件？  
參觀[Aspose.Slides for .NET 文檔](https://reference.aspose.com/slides/net/)了解更多。