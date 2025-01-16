---
title: 使用 Aspose.Slides for .NET 進行高級圖表定制
linktitle: 使用 Aspose.Slides for .NET 進行高級圖表定制
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 透過掌握先進的圖表自訂技術，釋放 Aspose.Slides for .NET 的全部潛力。本逐步指南涵蓋了從基本圖表創建到網格線、軸標題和自訂顏色等複雜細節的所有內容。
type: docs
weight: 10
url: /zh-hant/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## 介紹

創建具有視覺吸引力且資訊豐富的圖表對於有效的數據呈現至關重要。 Aspose.Slides for .NET 提供了強大的圖表自訂工具，使您能夠自訂圖表的各個方面。在本教程中，我們將探索使用 Aspose.Slides for .NET 進行圖表自訂的進階技術。

## 先決條件

在我們開始之前，請確保您符合以下先決條件：

1.  Aspose.Slides for .NET Library：從下列位置下載並安裝 Aspose.Slides 函式庫[這裡](https://releases.aspose.com/slides/net/).
2. .NET開發環境：設定.NET開發環境，例如Visual Studio。
3. C# 基礎知識：熟悉 C# 程式設計將會很有幫助，因為我們將編寫 C# 程式碼。

現在，讓我們將高級圖表定製過程分解為清晰的步驟。

## 第 1 步：建立新簡報

首先建立一個新的簡報來保存您的圖表。

```csharp
//文檔目錄的路徑。
string dataDir = "Your Document Directory";

//如果目錄不存在，則建立該目錄。
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

//實例化簡報
Presentation pres = new Presentation();
```

## 第 2 步：存取第一張投影片

接下來，造訪要新增圖表的第一張投影片。

```csharp
//存取第一張投影片
ISlide slide = pres.Slides[0];
```

## 第 3 步：新增範例圖表

現在，讓我們為投影片添加帶有標記的折線圖。

```csharp
//新增範例圖表
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## 第四步：設定圖表標題

為圖表設定標題可以提供必要的背景資訊。

```csharp
//設定圖表標題
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 第 5 步：自訂主要網格線

您可以增強值軸的網格線以獲得更好的可讀性。

```csharp
//自訂值軸的主要網格線
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## 第 6 步：自訂次網格線

同樣，自訂值軸的次網格線。

```csharp
//自訂值軸的次網格線
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 步驟 7：定義值軸編號格式

您可以設定數值軸上顯示的數字的格式。

```csharp
//設定值軸編號格式
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## 步驟 8：設定最大值和最小值

定義圖表的最大值和最小值。

```csharp
//設定圖表最大值和最小值
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## 第 9 步：自訂值軸文字屬性

增強值軸的文字屬性可提高可讀性。

```csharp
//自訂值軸文字屬性
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## 第10步：新增值軸標題

在值軸上新增標題可以闡明資料代表的內容。

```csharp
//設定數值軸標題
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 步驟 11：自訂類別軸的主要網格線

現在，讓我們增強類別軸的主要網格線。

```csharp
//自訂類別軸的主要網格線
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## 第12步：為類別軸自訂次網格線

同樣，自訂類別軸的次網格線。

```csharp
//自訂類別軸的次網格線
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 步驟 13：自訂類別軸文字屬性

改進類別軸標籤的字體樣式和外觀。

```csharp
//自訂類別軸文字屬性
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## 第14步：新增類別軸標題

如果需要，您也可以為類別軸新增標題。

```csharp
//設定類別軸標題
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 第 15 步：額外的定制

透過其他自訂（例如圖例、牆壁顏色和繪圖區域設定）進一步增強您的圖表。

```csharp
//額外的定制（可選）

//自訂圖例文字屬性
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

//顯示圖表圖例而不重疊圖表
chart.Legend.Overlay = true;

//設定圖表後牆顏色
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

//設定圖表底板顏色
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

//設定繪圖區域顏色
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

//儲存簡報
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## 結論

在本綜合指南中，我們介紹了使用 Aspose.Slides for .NET 的進階圖表自訂技術。您學習如何建立簡報、新增圖表、優化其外觀以及自訂各種圖表元素，例如網格線、軸標籤和圖例。 

## 常見問題解答

### Aspose.Slides for .NET 支援哪些版本的 .NET？
Aspose.Slides for .NET支援各種.NET版本，包括.NET Framework和.NET Core。請參閱文件以取得受支援版本的完整清單。

### 我可以從 Excel 檔案等資料來源建立圖表嗎？
是的，Aspose.Slides 允許您從外部資料來源（例如 Excel 電子表格）建立圖表。有關詳細範例，請參閱文件。

### 如何為我的圖表系列新增自訂資料標籤？
若要新增自訂資料標籤，請訪問`DataLabels`該系列的屬性並根據需要自訂標籤。您可以在文件中找到程式碼範例。

### 是否可以將圖表匯出為不同的格式，例如 PDF 或圖像？
絕對地！ Aspose.Slides 可讓您將帶有圖表的簡報匯出為各種格式，包括 PDF 和圖像格式。

### 在哪裡可以找到有關 Aspose.Slides for .NET 的更多教學和範例？
請造訪 Aspose.Slides[網站](https://reference.aspose.com/slides/net/)取得大量教學課程、程式碼範例和文件。