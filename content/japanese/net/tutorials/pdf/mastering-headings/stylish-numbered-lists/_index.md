---
title: Aspose.PDF for .NET を使用したスタイリッシュな番号付きリスト
linktitle: Aspose.PDF for .NET を使用したスタイリッシュな番号付きリスト
second_title: Aspose.PDF for .NET API リファレンス
description: Aspose.PDF for .NET を使用して、PDF ドキュメントに美しい番号付きリストを作成する方法を学びます。このガイドでは、ローマ数字などのさまざまな番号スタイルを適用する手順を説明します。
type: docs
weight: 10
url: /ja/net/programming-with-headings/stylish-numbered-lists/
---
## 導入

PDF ドキュメントに、構造化された番号付きリストを作成する必要があったことはありませんか? 法律文書、レポート、プレゼンテーションなど、コンテンツを整理するには、効果的な番号付けスタイルが不可欠です。Aspose.PDF for .NET を使用すると、さまざまな番号付けスタイルを PDF の見出しに簡単に適用でき、洗練されたプロフェッショナルなドキュメントを作成できます。

## 前提条件

コーディングを始める前に、以下のものが準備されていることを確認してください。

1.  Aspose.PDF for .NET: 最新バージョンをダウンロードするには、[ここ](https://releases.aspose.com/pdf/net/).
2. 開発環境: Visual Studio または .NET 互換の IDE が必要です。
3. .NET Framework: .NET Framework 4.0 以降がインストールされていることを確認してください。
4. ライセンス: 一時ライセンスは、[ここ](https://purchase.aspose.com/temporary-license/)または探索する[無料トライアル](https://releases.aspose.com/)オプション。

## 必要なパッケージのインポート

まず、プロジェクトに必要な名前空間をインポートします。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## ステップ1: ドキュメントの設定

まず、新しい PDF ドキュメントを作成し、ページ サイズや余白などのレイアウトを構成します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

//ページのサイズと余白を設定する
pdfDoc.PageInfo.Width = 612.0; //8.5インチ
pdfDoc.PageInfo.Height = 792.0; //11インチ
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); //1インチの余白
```

この設定により、ドキュメントはすべての辺に 1 インチの余白がある標準のレター サイズになります。

## ステップ2: PDFにページを追加する

次に、PDF ドキュメントに空白ページを追加し、後で番号付けスタイルを適用します。

```csharp
// PDF文書に新しいページを追加する
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; //ドキュメントと同じ設定を使用する
```

## ステップ3: フローティングボックスを作成する

FloatingBox を使用すると、ページのフローとは独立してコンテンツを配置できるため、レイアウトをより細かく制御できます。

```csharp
//構造化コンテンツ用のフローティングボックスを作成する
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## ステップ4: ローマ数字で見出しを追加する

ここで、小文字のローマ数字の番号を使用して最初の見出しを追加しましょう。

```csharp
//最初の見出しをローマ数字で作成する
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## ステップ 5: カスタム開始番号で 2 番目の見出しを追加する

次に、ローマ数字 13 から始まる 2 番目の見出しを追加します。

```csharp
//ローマ数字13から始まる2番目の見出しを作成します
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## ステップ6: アルファベット番号の見出しを追加する

変化をつけるために、小文字のアルファベット番号を使用して 3 番目の見出しを追加しましょう。

```csharp
//アルファベット番号の見出しを作成する
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## ステップ7: PDFを保存する

最後に、PDF ファイルを目的のディレクトリに保存します。

```csharp
// PDF文書を保存する
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## 結論

おめでとうございます! Aspose.PDF for .NET を使用して、PDF ファイルの見出しにさまざまな番号スタイル (ローマ数字とアルファベット) を適用できました。Aspose.PDF の柔軟性により、ページ レイアウト、番号スタイル、コンテンツの配置を制御できるため、整理されたプロフェッショナルな PDF ドキュメントを作成できます。

## よくある質問

### 同じ PDF ドキュメントに異なる番号スタイルを適用できますか?  
はい、ローマ数字、アラビア数字、アルファベット番号など、異なる番号スタイルを同じドキュメント内で混在させることができます。

### 見出しの開始番号をカスタマイズするにはどうすればいいですか?  
見出しの開始番号を設定するには、`StartNumber`財産。

### 番号順序をリセットする方法はありますか?  
はい、番号をリセットするには、`StartNumber`各見出しのプロパティ。

### 見出しに番号付けに加えて太字や斜体のスタイルを適用できますか?  
もちろんです！フォント、サイズ、太字、斜体などのプロパティを変更することで、見出しのスタイルをカスタマイズできます。`TextState`物体。

### Aspose.PDF の一時ライセンスを取得するにはどうすればよいですか?  
一時ライセンスは以下から取得できます。[ここ](https://purchase.aspose.com/temporary-license/)Aspose.PDF を制限なしでテストします。