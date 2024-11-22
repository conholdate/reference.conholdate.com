---
title: PDF ドキュメントに目次を追加する
linktitle: PDF ドキュメントに目次を追加する
second_title: Aspose.PDF for .NET API リファレンス
description: このチュートリアルでは、Aspose.Pdf for .NET を使用して PDF ドキュメントに目次 (TOC) を追加する方法を説明します。
type: docs
weight: 40
url: /ja/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## 導入

PDF ドキュメントに目次 (TOC) を作成すると、ナビゲーションとアクセシビリティが大幅に向上します。このガイドでは、Aspose.Pdf for .NET を使用して PDF ファイルに TOC を追加する方法を説明します。

## 前提条件

始める前に、以下のものを用意してください。

1.   Aspose.PDF for .NET: 最新バージョンをダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/pdf/net/).
2.  開発環境: Visual Studio などの .NET 開発環境をセットアップします。
3.  ライセンス: 必要な場合は一時ライセンスを申請してください。[Aspose.Pdf ライセンス ページ](https://asposepdf.com/developers)詳細についてはこちらをご覧ください。

必要なライブラリのインポート

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## ステップ1: PDFドキュメントを読み込む

TOC を追加する既存の PDF ファイルを読み込みます。ドキュメント ディレクトリへのパスを指定します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## ステップ2: TOC用の新しいページを挿入する

PDF ドキュメントの先頭に新しいページを挿入します。このページは目次 (TOC) として機能します。

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## ステップ3: TOC情報オブジェクトを作成する

TOC 情報を表すオブジェクトを作成します。ナビゲーションを容易にするために、タイトルとリンクを追加します。

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## ステップ4: TOC要素を定義する

TOC に表示される要素 (または見出し) を定義します。これらの要素は、読者がドキュメントの特定のセクションに移動するのに役立ちます。

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## ステップ5: 目次の見出しを作成する

目次の最初の 2 つの要素に見出しを作成します。これらの見出しは、それぞれのページにリンクします。

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## ステップ6: TOC付きのPDFを保存する

最後に、更新された PDF ファイルを保存します。

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## 確認メッセージ

プロセスが完了したことをユーザーに知らせるための確認メッセージを表示します。

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## 結論

Aspose.PDF for .NET を使用すると、PDF に目次を追加するのが簡単であるだけでなく、カスタマイズも可能です。シンプルなナビゲーション リンクを作成する必要がある場合でも、複雑な構造を作成する必要がある場合でも、このツールが対応します。次に長い PDF を作成するときは、プロフェッショナルなタッチのために目次を追加することを忘れないでください。

## よくある質問

### Aspose.PDF で TOC の外観をカスタマイズできますか?

はい、フォント スタイル、サイズ、配置など、目次の外観を完全にカスタマイズできます。

### 目次にサブ見出しを追加するにはどうすればよいですか?

サブ見出しを追加するには、`Heading`レベル（例：`Heading(2)`）。

### ドキュメントが変更された場合に目次を自動的に更新することは可能ですか?

いいえ、目次は自動的に更新されません。ドキュメント構造が変更された場合は、目次を再作成する必要があります。

### TOC エントリを外部ドキュメントにリンクできますか?

はい、ハイパーリンクを使用して TOC エントリを外部の PDF または URL にリンクできます。

### Aspose.PDF は複数レベルの目次をサポートしていますか?

はい、Aspose.PDF はサブセクションを含む複雑なドキュメントの複数レベルの目次をサポートしています。
