---
title: Word 文書のブックマークされたセクションからテキストを追加する
linktitle: Word 文書のブックマークされたセクションからテキストを追加する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書のブックマークされたセクションからテキストをシームレスに追加する方法を学びます。このステップバイステップのチュートリアル。
type: docs
weight: 10
url: /ja/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## 導入

Word 文書のブックマークされたセクションからテキストを追加するのが難しいと感じたことはありませんか? 適切な場所に来ています! このチュートリアルでは、Aspose.Words for .NET を使用して、プロセスをステップごとに説明します。最後には、ブックマークされたテキストをプロのように追加できるようになります。さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意しておいてください。

-  Aspose.Words for .NET: まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio のような .NET 開発環境。
- C# の基礎知識: 基本的な C# プログラミングの概念を理解していると有利です。
- ブックマーク付きの Word 文書: テキストを追加するために使用するブックマークを含む Word 文書。

## 必要な名前空間をインポートする

まず、Aspose.Words 機能にアクセスするために必要な名前空間をインポートする必要があります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## ステップ1: ドキュメントを読み込み、変数を初期化する

まず、ソースと宛先の Word 文書を読み込み、必要な変数を初期化します。

```csharp
//ソースドキュメントと宛先ドキュメントを読み込みます。
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

//ドキュメントインポーターを初期化します。
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

//ソース ドキュメント内のブックマークを見つけます。
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## ステップ2: 開始段落と終了段落を特定する

次に、ブックマークの開始と終了の段落を見つける必要があります。これは、正しいテキストを抽出するために不可欠です。

```csharp
//ブックマークの先頭と末尾の段落を識別します。
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

//段落を検証します。
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## ステップ3: 段落の親を検証する

開始段落と終了段落の両方が同じ親ノードを共有するようにする必要があります。これは、複雑さを回避するための簡略化されたアプローチです。

```csharp
//開始段落と終了段落の親が同じかどうかを確認します。
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## ステップ4: 停止するノードを特定する

ここで、テキストのコピーを停止する場所を決定する必要があります。これは、終了段落の直後のノードになります。

```csharp
//最後の段落の直後のノードを識別します。
Node endNode = endPara.NextSibling;
```

## ステップ5: ブックマークしたテキストを宛先ドキュメントに追加する

最後に、開始段落から終了段落の後のノードまでのノードをループし、それらを宛先ドキュメントに追加します。

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    //現在のノードを宛先ドキュメントにインポートします。
    Node newNode = importer.ImportNode(curNode, true);

    //インポートしたノードを宛先ドキュメントに追加します。
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

//更新された宛先ドキュメントを保存します。
dstDoc.Save("appended_document.docx");
```

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書のブックマークされたセクションからテキストを正常に追加できました。この強力なライブラリにより、文書の操作が簡単になり、ツールキットに便利なスキルがもう 1 つ加わりました。コーディングを楽しんでください!

## よくある質問

### 複数のブックマークからテキストを一度に追加できますか?
はい、ブックマークごとにこのプロセスを繰り返し、必要に応じてテキストを追加できます。

### 開始段落と終了段落の親が異なる場合はどうなりますか?
現在の例では、同じ親を持つことを前提としています。そうでない場合は、より複雑な処理を実装する必要があります。

### 追加されたテキストの元の書式は保持されますか?
絶対に！使用`ImportFormatMode.KeepSourceFormatting`元の書式が維持されます。

### 宛先ドキュメント内の特定の位置にテキストを追加することは可能ですか?
はい、宛先ドキュメント内の適切なノードに移動することで、任意の位置にテキストを追加できます。

### ブックマークのテキストを新しいセクションに追加できますか?
はい、宛先ドキュメントに新しいセクションを作成し、そこにテキストを追加できます。