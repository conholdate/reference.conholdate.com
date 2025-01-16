---
title: Aspose.Slides .NET のデータ ポイントのグラフ マーカー オプション
linktitle: Aspose.Slides .NET のデータ ポイントのグラフ マーカー オプション
second_title: Aspose.Slides .NET PowerPoint 処理 API
description: Aspose.Slides for .NET を使用して、カスタマイズされたマーカー オプションで PowerPoint グラフを強化する方法を学びます。このステップ バイ ステップ ガイドでは、前提条件、グラフの作成、データ ポイントの書式設定などについて説明します。
type: docs
weight: 11
url: /ja/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## 導入

プレゼンテーションに視覚的な補助を組み込むことは、効果的なコミュニケーションに不可欠です。Aspose.Slides for .NET は、グラフを作成およびカスタマイズするための強力なツールを提供し、開発者がデータ プレゼンテーションを強化できるようにします。際立った機能の 1 つは、データ ポイントでグラフ マーカー オプションを使用できることです。これにより、プロフェッショナルな外観のグラフを正確にカスタマイズできます。この記事では、これを実現するために必要なすべての手順について説明します。

## 前提条件

続行する前に、次の点を確認してください。

-  Aspose.Slides for .NET インストール済み: ダウンロードはこちら[ここ](https://releases.aspose.com/slides/net/).
- 基本設定: 作業ディレクトリ内の「Test.pptx」などのプレゼンテーション ファイル。
- 開発環境: .NET 用に構成された Visual Studio または同等のもの。

## 必要な名前空間のインポート

シームレスな開発のために、プロジェクトに必要な名前空間を追加します。

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## ステップ1: プレゼンテーションにグラフを作成する

まず、プレゼンテーションの最初のスライドにデフォルトのグラフを作成します。

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

これにより、`LineWithMarkers`指定された寸法でスライドにグラフを追加します。

## ステップ2: グラフデータワークシートインデックスを取得する

デフォルトのグラフ データ ワークシート インデックスは、さらにカスタマイズするために不可欠です。

```csharp
int defaultWorksheetIndex = 0;
```

## ステップ3: チャートデータワークブックにアクセスする

グラフ データを操作するには、関連付けられているワークブックを取得します。

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## ステップ4: チャートシリーズを構成し、データポイントを追加する

デフォルトのシリーズをクリアし、シリーズに新しいデータ ポイントを追加します。

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

//シリーズにデータポイントを追加する
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## ステップ5: データポイントマーカーに画像の塗りつぶしを適用する

カスタム画像を使用すると、データ マーカーを視覚的に魅力的にすることができます。

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

//マーカーのカスタム画像を設定する
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## ステップ6: マーカーのサイズをカスタマイズする

視認性を高めるためにマーカーのサイズを変更します。

```csharp
series.Marker.Size = 20;
```

## ステップ7: 更新したプレゼンテーションを保存する

カスタマイズしたプレゼンテーションを希望の場所に保存します。

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## 結論

Aspose.Slides for .NET は、豊富なカスタマイズ オプションを備えたプロフェッショナルなグラフを作成するためのツールを開発者に提供します。グラフ マーカー オプションを活用することで、プレゼンテーションの視覚的な魅力と明瞭さを大幅に向上できます。このステップ バイ ステップ ガイドにより、複雑なカスタマイズも簡単に実装できます。

## よくある質問

### マーカーのカスタマイズには任意の画像形式を使用できますか?
はい、Aspose.Slides はマーカーのカスタマイズ用に JPEG、PNG、BMP などのさまざまな画像形式をサポートしています。

### 作成後にグラフの種類を変更するにはどうすればよいですか?
チャートの種類を変更するには、`chart.Type`プロパティと異なる`ChartType`.

### Aspose.Slides for .NET は古いバージョンの PowerPoint と互換性がありますか?
はい、古い PowerPoint 形式との下位互換性をサポートしており、汎用性が確保されています。

### チャートデータを動的に更新できますか?
もちろんです。`IChartDataWorkbook`プログラムでグラフデータを更新します。

### さらにリソースはどこで見つかりますか?
探索する[Aspose.Slides ドキュメント](https://reference.aspose.com/slides/net/)または参加する[コミュニティフォーラム](https://forum.aspose.com/)サポートのため。