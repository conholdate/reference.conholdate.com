---
title: Word 文書のブックマークの表示を管理する
linktitle: Word 文書のブックマークの表示を管理する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書内のコンテンツの表示を巧みに制御する方法を学びます。このステップ バイ ステップ ガイドをご覧ください。
type: docs
weight: 10
url: /ja/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## 導入

Aspose.Words for .NET を使用してドキュメント操作スキルを向上させる準備はできていますか? ドキュメント タスクを自動化する熟練した開発者でも、Word ファイルのプログラムによる制御を探求している好奇心旺盛な個人でも、このガイドはあなたにぴったりです。今日は、Word ドキュメントのブックマークに基づいてコンテンツを表示および非表示にする方法について詳しく説明します。さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1. Visual Studio: .NET と互換性のある任意のバージョン。
2.  Aspose.Words for .NET: ダウンロード[ここ](https://releases.aspose.com/words/net/).
3. 基本的な C# の知識: 簡単な C# プログラムの記述に関する知識があれば十分です。
4. サンプル Word 文書: このチュートリアル用のブックマークを含む Word 文書 (例: 「Bookmarks.docx」) を準備します。

### 新しいプロジェクトを作成する

1. Visual Studio を開き、新しいコンソール アプリ (.NET Core) プロジェクトを作成します。「BookmarkVisibilityManager」のような名前を付けます。

### Aspose.Words for .NET をインストールする

NuGet パッケージ マネージャーを使用して Aspose.Words をプロジェクトに追加します。

1. [ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理] に移動します。
2. 「Aspose.Words」を検索します。
3. パッケージをインストールします。

プロジェクトの設定が完了したら、ドキュメントの読み込みに進みます。

## 名前空間のインポート

まず、必須の名前空間をインポートします。これらは、Aspose.Words を使用して Word 文書を操作するために必要なクラスとメソッドを提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## ステップ1: ドキュメントの読み込み

Word 文書を操作するには、まずそれを読み込む必要があります。その方法は次のとおりです。

```csharp
//ドキュメント ディレクトリへのパスを定義します。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

このスニペットはドキュメントディレクトリへのパスを設定し、ドキュメントを`Document`物体。

## ステップ2: ブックマークしたコンテンツを表示/非表示にする

さて、ブックマークに基づいてコンテンツの表示を切り替えるメソッドを作成しましょう。このメソッドを次のように呼びます。`ShowHideBookmarkedContent`.

メソッドの実装は次のとおりです。

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

- ブックマークの取得:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];`指定されたブックマークを取得します。
- ノードトラバーサル: ブックマーク内のノードを反復処理します。
- 表示切り替え: それぞれ`Run`ノード（テキストのセグメントを表す）では、その`Hidden`に基づくプロパティ`isHidden`パラメータ。

## ステップ3: メソッドの適用

メソッドの準備ができたので、これを使用して特定のブックマーク内のコンテンツを表示または非表示にしてみましょう。

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // 「MyBookmark1」内のコンテンツを非表示にする
```

この行は、「MyBookmark1」という名前のブックマークに関連付けられたコンテンツを非表示にします。

## ステップ4: ドキュメントを保存する

変更を加えたら、変更したドキュメントを保存することを忘れないでください。

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

これにより、更新された表示設定でドキュメントが保存されます。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書内のブックマークされたコンテンツを表示および非表示にする方法を学習しました。この強力なライブラリは、ドキュメントの操作を簡素化し、レポートの自動化、テンプレートの作成、または Word ファイルの実験に最適です。コーディングを楽しんでください!

## よくある質問

### 複数のブックマークを一度に切り替えることはできますか?
はい、お電話ください`ShowHideBookmarkedContent`切り替えるブックマークごとにメソッドを使用します。

### コンテンツを非表示にするとドキュメントの構造に影響しますか?
いいえ、コンテンツを非表示にすると、そのコンテンツの可視性のみに影響し、ドキュメント内のコンテンツはそのまま残ります。

### この方法を他の種類のコンテンツにも使用できますか?
このメソッドは、テキスト実行用に特別に設計されています。他のコンテンツ タイプの場合は、それに応じてノード トラバーサル ロジックを調整する必要があります。

### Aspose.Words for .NET は無料ですか?
 Aspose.Wordsは無料トライアルを提供しています[ここ](https://releases.aspose.com/)ただし、本番環境での使用にはフルライセンスが必要です。[ここ](https://purchase.aspose.com/buy).

### 問題が発生した場合、どうすればサポートを受けることができますか?
サポートについては、Aspose コミュニティ フォーラムをご覧ください。[ここ](https://forum.aspose.com/c/words/8).