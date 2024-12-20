---
title: Aspose.PDF for .NET を使用して PDF から強調表示されたテキストを抽出する
linktitle: Aspose.PDF for .NET を使用して PDF から強調表示されたテキストを抽出する
second_title: Aspose.PDF for .NET API リファレンス
description: Aspose.PDF for .NET を使用して強調表示されたテキストを抽出する方法を学習して、PDF ドキュメントの可能性を最大限に引き出します。この包括的なガイドでは、セットアップから実装までの各手順について説明します。
type: docs
weight: 60
url: /ja/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## 導入

PDF ファイルで作業する場合、強調表示されたテキストの抽出は、データ分析、コンテンツのレビュー、メモの整理に不可欠です。Aspose.PDF for .NET を使用している場合は、ラッキーです。このチュートリアルでは、PDF ドキュメントから強調表示されたテキストを効率的に抽出する方法について、わかりやすい手順を説明します。

## 前提条件

始める前に、次のものを用意してください。

-  Aspose.PDF for .NETライブラリ:ライブラリを以下からダウンロードしてください。[リリースページ](https://releases.aspose.com/pdf/net/).
- 開発環境: Visual Studio のような作業環境。
- C# の基礎知識: C# とオブジェクト指向プログラミングに精通している必要があります。
-  Asposeライセンス: 無料トライアルから始めることもできますが、[一時ライセンス](https://purchase.aspose.com/temporary-license/)またはフルライセンス[ここ](https://purchase.aspose.com/buy)無制限のアクセスを提供します。

## 必要な名前空間をインポートする

まず、C# プロジェクトに必要な名前空間をインポートします。

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

これらの名前空間は、PDF ドキュメントと注釈の処理に必要なクラスとメソッドへのアクセスを提供します。

## ステップ1: プロジェクトディレクトリを設定する

PDF ファイルが保存されているディレクトリを指定します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

パスを PDF ファイルの実際のディレクトリに置き換えてください。

## ステップ2: PDFドキュメントを読み込む

次のコードを使用して PDF ドキュメントを読み込みます。

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

指定されたファイルが指定されたディレクトリに存在することを確認します。

## ステップ3: ページ上の注釈にアクセスする

注釈にアクセスするには、目的のページ (この場合は最初のページ) の注釈をループします。

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

このコードは、`TextMarkupAnnotation`ハイライトを表すタイプ。

## ステップ4: 強調表示されたテキストを抽出する

次に、強調表示された注釈からテキストを抽出して表示します。

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

これにより、ハイライトに関連付けられたすべてのマークされたテキスト フラグメントが取得され、コンソールに出力されます。

## 結論

Aspose.PDF for .NET を使用して PDF から強調表示されたテキストを抽出するのは簡単で、ドキュメント処理プロセスを大幅に強化できます。上記の手順に従うことで、レポートの準備やデータ分析など、さまざまなアプリケーションで強調表示されたテキストを効率的に収集できます。

## よくある質問

### 他の種類の注釈を抽出できますか?
はい、調整するだけで`if`異なる注釈タイプを含める条件`TextAnnotation`または`StampAnnotation`.

### すべての PDF ページから強調表示されたテキストを抽出するにはどうすればよいですか?
次のコマンドを使用して、すべてのページをループできます。
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Aspose.PDF for .NET にはライセンスが必要ですか?
無料トライアルもご利用いただけますが、[一時ライセンス](https://purchase.aspose.com/temporary-license/)または完全なアクセスのためのフルライセンス。

### 抽出したテキストをファイルに保存できますか?
もちろんです! コードを変更して、抽出したテキストをテキスト ファイルに書き込むことができます。

### Aspose.PDF は他のプラットフォームもサポートしていますか?
はい、Aspose.PDF は Java やその他のプラットフォームもサポートしており、同様の機能を提供します。