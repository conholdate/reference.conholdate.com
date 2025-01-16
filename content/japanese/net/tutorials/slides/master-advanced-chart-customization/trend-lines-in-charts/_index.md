---
title: Aspose.Slides for .NET を使用したチャートのトレンド ライン
linktitle: Aspose.Slides for .NET を使用したチャートのトレンド ライン
second_title: Aspose.Slides .NET PowerPoint 処理 API
description: Aspose.Slides for .NET を使用して、グラフにトレンド ラインを追加およびカスタマイズする方法を学びます。この包括的なガイドでは、指数、線形、対数、多項式、移動平均のトレンド ラインを取り上げ、データの視覚化を強化します。
type: docs
weight: 12
url: /ja/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## 導入  

トレンド ラインをグラフに追加することは、データの傾向を分析し、将来の値を予測するための重要な手法です。Aspose.Slides for .NET を使用すると、プレゼンテーション グラフにトレンド ラインをシームレスに追加してカスタマイズし、データの視覚化を強化できます。このガイドでは、Aspose.Slides for .NET を使用して PowerPoint プレゼンテーションのさまざまなグラフ タイプにトレンド ラインを追加する詳細な手順を説明します。  

## 前提条件  

実装に進む前に、次の設定がされていることを確認してください。  

1.  Aspose.Slides for .NET: ライブラリをダウンロードしてインストールします。[ダウンロードページ](https://releases.aspose.com/slides/net/).  
2. 開発環境: コーディングには Visual Studio などの IDE を使用します。  
3. 基本的な C# の知識: このチュートリアルを実行するには、C# プログラミングの知識が必要です。  

## 必要な名前空間のインポート  

まず、重要な名前空間をプロジェクトにインポートします。  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## ステップ1: プレゼンテーションの設定  

まず、空のプレゼンテーションを初期化します。これがチャートのコンテナとして機能します。  

```csharp
string dataDir = "Your/Documents/Directory";

//ディレクトリが存在することを確認する
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

//新しいプレゼンテーションを作成する
Presentation presentation = new Presentation();
```

## ステップ 2: スライドにグラフを追加する  

次に、スライドを追加し、集合縦棒グラフを含めてデータを視覚化します。  

```csharp
//空白のスライドを追加する
ISlide slide = presentation.Slides[0];

//集合縦棒グラフを追加する
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## ステップ3: チャートデータを入力する  

サンプルデータをグラフに入力します。  

```csharp
//デフォルトのグラフデータワークブックにアクセスする
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

//デフォルトのカテゴリとシリーズの値を更新する
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## ステップ4: トレンドラインの追加  

### 指数トレンドライン  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### 線形トレンドライン  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### 対数トレンドライン  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### 移動平均トレンドライン  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### 多項式トレンドライン  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### パワートレンドライン  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## ステップ5: プレゼンテーションを保存する  

最後に、すべてのトレンド ラインをチャートに追加してプレゼンテーションを保存します。  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## 結論  

Aspose.Slides for .NET を使用すると、チャートにトレンド ラインを追加するのが簡単になります。この機能を使用すると、データのトレンドを効果的に表示し、プレゼンテーションにプロフェッショナルなタッチを加えることができます。上記の手順に従って、さまざまなトレンド ライン タイプを組み込み、データの視覚化を向上させます。  

## よくある質問  

### トレンドラインの外観をカスタマイズできますか?  
はい、トレンドラインの色、太さ、スタイルをカスタマイズできます。`Format.Line`財産。  

### 他の種類のグラフはサポートされていますか?  
はい、Aspose.Slides for .NET は、棒グラフ、円グラフ、折れ線グラフなど、さまざまな種類のグラフをサポートしています。  

### 方程式と R 二乗値を表示するにはどうすればよいですか?  
有効にする`DisplayEquation`そして`DisplayRSquaredValue`これらの値をグラフに表示するには、トレンド ラインのプロパティを設定します。  

### Aspose.Slides for .NET を他の言語で使用できますか?  
はい、ライブラリは VB.NET や F# を含む、.NET がサポートするすべての言語と互換性があります。  

### さらに詳しい資料はどこで見つかりますか?  
訪問する[Aspose.Slides for .NET ドキュメント](https://reference.aspose.com/slides/net/)詳細についてはこちらをご覧ください。