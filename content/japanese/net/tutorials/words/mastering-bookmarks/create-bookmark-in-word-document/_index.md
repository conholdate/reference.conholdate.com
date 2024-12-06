---
title: Aspose.Words for .NET を使用して Word 文書にブックマークを作成する
linktitle: Aspose.Words for .NET を使用して Word 文書にブックマークを作成する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用してブックマークを作成および管理することで、Word 文書を強化する方法を学びます。このステップ バイ ステップのチュートリアル ガイド。
type: docs
weight: 10
url: /ja/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## 導入

大きなドキュメントをナビゲートするのは難しい場合がありますが、ブックマークを使用すると簡単です。このチュートリアルでは、Aspose.Words for .NET を使用して Word ドキュメントにブックマークを作成する方法について説明します。ドキュメントの設定方法、ブックマークの追加方法、PDF として保存する方法をステップごとに学習します。さあ、始めましょう。

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NETライブラリ: ダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio または任意の .NET 互換 IDE を使用します。
3. 基本的な C# の知識: C# プログラミングの概念を理解していると役立ちます。

## 名前空間のインポート

まず、Aspose.Words を操作するために必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ 1: ドキュメントと DocumentBuilder を設定する

新しいドキュメントを作成し、`DocumentBuilder`コンテンツやブックマークを追加できます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: メインブックマークを作成する

ブックマークを作成するには、開始点と終了点を指定する必要があります。「My Bookmark」という名前のブックマークを作成する方法は次のとおりです。

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`: ブックマークの開始をマークします。
- `Writeln`: ブックマーク内にテキストを追加します。

## ステップ3: ネストされたブックマークを作成する

整理しやすくするためにブックマークをネストすることができます。「マイブックマーク」内に「ネストされたブックマーク」を追加する方法は次のとおりです。

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- ネストにより階層構造を作成できます。 
- `EndBookmark`: 現在のブックマークを閉じます。

## ステップ4: ネストされたブックマークの外側にテキストを追加する

ネストされたブックマークを作成したら、メインのブックマーク内にコンテンツを追加し続けます。

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
これにより、メインのブックマークにネストされたブックマークと追加のテキストの両方が含まれるようになります。

## ステップ5: PDF保存オプションを設定する

PDF にブックマークを含めるには、保存オプションを設定します。

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`: ドキュメントを PDF として保存する方法を定義します。
- `BookmarksOutlineLevels`: PDF 内のブックマークの階層を設定します。

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
の`Save`メソッドは、ブックマークを含め、指定された形式と場所にドキュメントを保存します。

## 結論

Aspose.Words for .NET を使用すると、Word 文書にブックマークを簡単に作成でき、文書のナビゲーションが強化されます。レポートや電子書籍を生成する場合や、膨大な文書を管理する場合、ブックマークは非常に重要です。このチュートリアルに従えば、すぐに整理されたブックマーク付きの PDF を作成できます。

## よくある質問

### 異なるレベルで複数のブックマークを作成できますか?
はい。PDF として保存するときに、複数のブックマークを作成し、その階層を定義できます。

### ブックマークのテキストを更新するにはどうすればよいですか?
使用`DocumentBuilder.MoveToBookmark`ブックマークに移動してテキストを更新します。

### ブックマークを削除することは可能ですか?
もちろんです！`Bookmarks.Remove`ブックマークの名前を指定してメソッドを実行します。

### PDF 以外の形式でブックマークを作成できますか?
はい、Aspose.Words は DOCX、HTML、EPUB などの形式のブックマークをサポートしています。

### ブックマークが PDF に正しく表示されるようにするにはどうすればよいですか?
定義する`BookmarksOutlineLevels`適切に`PdfSaveOptions`ブックマークが PDF アウトラインに含まれるようにします。