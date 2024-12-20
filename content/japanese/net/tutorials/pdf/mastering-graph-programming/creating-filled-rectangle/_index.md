---
title: 塗りつぶされた四角形の作成
linktitle: 塗りつぶされた四角形の作成
second_title: Aspose.PDF for .NET API リファレンス
description: このステップバイステップのチュートリアルで、Aspose.PDF for .NET を使用した PDF 操作のパワーを解き放ちましょう。塗りつぶされた四角形を描画して、視覚的に魅力的な PDF ドキュメントをプログラムで作成する方法を学びます。
type: docs
weight: 50
url: /ja/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## 導入

視覚的に美しい PDF をプログラムで作成したいと思ったことはありませんか? もしそうなら、ここが最適な場所です! このチュートリアルでは、PDF ドキュメントの操作を簡素化する強力なライブラリである Aspose.PDF for .NET について説明します。今日は、PDF ファイル内に塗りつぶされた四角形を作成することに焦点を当てます。経験豊富な開発者でも、初心者でも、このガイドでは、わかりやすく魅力的な方法で各手順を順を追って説明します。さあ、コーディングの帽子をかぶって、始めましょう!

## 前提条件

コードに進む前に、次のものを用意してください。

1. Visual Studio: Visual Studio は .NET 開発に最適な IDE なので、お使いのマシンにインストールしてください。
2. Aspose.PDF for .NET: Aspose.PDFライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.aspose.com/pdf/net/).
3. C# の基礎知識: C# プログラミングに精通していると、コード スニペットをよりよく理解できるようになります。

## ステップ1: 新しいプロジェクトを作成する

1. Visual Studio を開き、新しいコンソール アプリケーション プロジェクトを作成します。
2. プロジェクトに適切な名前を付けます。

## ステップ2: Aspose.PDF参照を追加する

1. ソリューション エクスプローラーでプロジェクトを右クリックします。
2. NuGet パッケージの管理を選択します。
3. Aspose.PDF を検索し、最新バージョンをインストールします。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

すべてが準備できたので、コードを見ていきましょう。

## ステップ3: ドキュメントディレクトリを設定する

PDF を保存するパスを指定します:

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"` PDF を保存するマシン上の実際のパスを入力します。

## ステップ4: ドキュメントインスタンスを作成する

新しい PDF ドキュメントを初期化します。

```csharp
//ドキュメントインスタンスを作成する
Document doc = new Document();
```

## ステップ5: ドキュメントにページを追加する

すべての PDF には少なくとも 1 ページが必要です。1 ページ追加してみましょう。

```csharp
// PDFファイルのページコレクションにページを追加する
Page page = doc.Pages.Add();
```

## ステップ6: グラフインスタンスを作成する

あ`Graph`インスタンスは図形を描画するためのキャンバスとして機能します。

```csharp
//グラフインスタンスを作成する
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## ステップ7: ページにグラフを追加する

グラフをページに添付します。

```csharp
//ページインスタンスの段落コレクションにグラフオブジェクトを追加する
page.Paragraphs.Add(graph);
```

## ステップ8: 長方形インスタンスを作成する

長方形の位置とサイズを定義します。

```csharp
//長方形インスタンスを作成する
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## ステップ9: 塗りつぶしの色を指定する

四角形の色を選択します。この例では、赤を使用します。

```csharp
//グラフオブジェクトの塗りつぶし色を指定する
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## ステップ10: グラフに四角形を追加する

グラフに四角形を追加します。

```csharp
//グラフオブジェクトの図形コレクションに長方形オブジェクトを追加します。
graph.Shapes.Add(rect);
```

## ステップ11: PDFドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// PDFファイルを保存
doc.Save(dataDir);
```

## ステップ12: 確認メッセージ

成功を示す確認メッセージを出力します。

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## 結論

おめでとうございます! Aspose.PDF for .NET を使用して、PDF ドキュメントに塗りつぶされた四角形を正常に作成できました。この強力なライブラリは、PDF 操作の可能性を広げ、プログラムで魅力的なドキュメントを生成できるようにします。レポート、請求書、またはその他の種類の PDF を作成する場合でも、Aspose.PDF が役立ちます。

## よくある質問

### Aspose.PDF for .NET とは何ですか?
Aspose.PDF for .NET は、開発者がプログラムによって PDF ドキュメントを作成、操作、変換できるようにするライブラリです。

### Aspose.PDF を無料で使用できますか?
はい、Asposeはライブラリの機能を試すために使用できる無料試用版を提供しています。ダウンロードできます。[ここ](https://releases.aspose.com/).

### Aspose.PDF のサポートを受ける方法はありますか?
もちろんです！Asposeフォーラムを通じてサポートを受けることができます[ここ](https://forum.aspose.com/c/pdf/10).

### Aspose.PDF を購入するにはどうすればよいですか?
 Aspose.PDFは購入ページから購入できます。[ここ](https://purchase.aspose.com/buy).

### Aspose.PDF ではどのような種類の図形を作成できますか?
Aspose.PDF ライブラリを使用すると、長方形、円、線など、さまざまな図形を作成できます。