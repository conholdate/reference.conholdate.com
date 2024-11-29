---
title: GroupDocs.Annotation for .NET を使用したボタン コンポーネントの追加
linktitle: ボタンコンポーネントの追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してインタラクティブなボタン コンポーネントを追加し、PDF ドキュメントを向上させる方法を説明します。このステップ バイ ステップのチュートリアルをご覧ください。
type: docs
weight: 10
url: /ja/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## 導入

このチュートリアルでは、.NET 用の GroupDocs.Annotation ライブラリを使用して PDF ドキュメントにボタン コンポーネントを追加する簡単な手順を説明します。このガイドを読み終えると、インタラクティブな機能を使用して PDF ドキュメントを強化できるようになります。

## 前提条件

始める前に、次のものを用意してください。

1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. 開発環境: .NET フレームワークがインストールされた適切な開発環境をセットアップします。

## ステップ1: 必要な名前空間をインポートする

まず、必要な名前空間をプロジェクトにインポートします。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## ステップ2: 出力パスを初期化する

変更された PDF を保存する出力パスを定義します。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ3: ボタンコンポーネントを追加する

次に、ボタン コンポーネントを作成して PDF に追加します。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), //ボタンの位置とサイズ
        PenColor = 65535,                       //ボタンの境界線の色
        Style = BorderStyle.Dashed,             //境界線のスタイル
        BorderWidth = 0,                        //境界線の幅
        BorderColor = 0,                        //境界線の色
        AlternateName = "Name",                 //ボタンの別名
        PartialName = "Partial Name",           //ボタンの部分的な名前
        NormalCaption = "Caption",               //ボタンに表示されるテキスト
        ButtonColor = 16761035,                 //ボタンの背景色
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); //アノテーターにボタンを追加する
    annotator.Save("result.pdf"); //変更したPDFを保存する
}
```

## ステップ4: 出力パスを表示する

最後に、出力ファイルが保存される場所をユーザーに通知します。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

おめでとうございます! GroupDocs.Annotation for .NET を使用して、ボタン コンポーネントを PDF ドキュメントに正常に追加しました。

## 結論

このチュートリアルでは、GroupDocs.Annotation for .NET を使用してボタン コンポーネントを PDF ドキュメントに組み込む方法を説明しました。これらの手順に従うことで、PDF ドキュメントのインタラクティブ性を大幅に向上できます。

## よくある質問

### ボタンの外観をカスタマイズできますか?

もちろんです! サイズ、色、スタイルなどのさまざまなプロパティを、要件に合わせて変更できます。

### GroupDocs.Annotation for .NET はすべての PDF バージョンと互換性がありますか?

はい、GroupDocs.Annotation for .NET は幅広い PDF バージョンをサポートしており、ほとんどのドキュメントとの互換性が保証されています。

### つの PDF ドキュメントに複数のボタン コンポーネントを追加できますか?

はい、PDF ドキュメントに必要な数のボタン コンポーネントを追加できます。

### GroupDocs.Annotation for .NET は他のファイル形式をサポートしていますか?

はい、PDF に加えて、DOCX、PPTX、XLSX など、さまざまなドキュメント形式をサポートしています。

### テスト用に試用版はありますか?

はい、GroupDocs.Annotation for .NETの無料トライアルはこちらからご利用いただけます。[ここ](https://releases.groupdocs.com/).
