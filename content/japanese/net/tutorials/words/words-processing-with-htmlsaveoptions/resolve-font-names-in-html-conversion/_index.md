---
title: HTML変換でフォント名を解決する
linktitle: HTML変換でフォント名を解決する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書を HTML に変換するときにフォントの問題を効果的に解決する方法を学びます。このステップ バイ ステップ ガイドでは、エクスポートされた HTML 形式でフォントが正しく表示されるように保存オプションを構成する方法について明確な手順を説明します。
type: docs
weight: 10
url: /ja/net/tutorials/words/words-processing-with-htmlsaveoptions/resolve-font-names-in-html-conversion/
---
## 導入

こんにちは、プログラマーの皆さん! Word 文書を HTML として保存するときにフォントの問題に悩まされたことがある人は、あなただけではありません。フォントは扱いにくいものですが、心配はいりません。このガイドは、Aspose.Words for .NET を使用して Word 文書のフォント名を解決するのに役立ちます。HTML 形式でフォントが適切に表示されるように、手順を追って説明しましょう。

## 前提条件

始める前に、必要なものがすべて揃っていることを確認してください。

1. Aspose.Words for .NET: ダウンロード[ここ](https://releases.aspose.com/words/net/).
2. 有効なライセンス: ライセンスを購入する[ここ](https://purchase.aspose.com/buy)または一時免許を取得する[ここ](https://purchase.aspose.com/temporary-license/).
3. C# と .NET の基礎知識: C# の基本的なプログラミング概念を理解していることが前提となります。
4. Visual Studio: .NET フレームワークをサポートするどのバージョンでも動作します。

前提条件が整ったので、早速行動に移しましょう。

## 必要な名前空間のインポート

コーディングする前に、必要な名前空間がプロジェクトにインポートされていることを確認してください。これは、Aspose.Words の機能にアクセスするために重要です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリの設定

まず、Word 文書が保存され、出力が保存されるドキュメント ディレクトリへのパスを設定しましょう。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

ここ、`dataDir`ドキュメントディレクトリへのパスを保持します。`"YOUR_DOCUMENT_DIRECTORY"`システム上の実際のパスを使用します。

## ステップ2: Word文書の読み込み

次に、処理する Word 文書を読み込む必要があります。この文書には、解決するフォントが含まれている必要があります。

```csharp
Document doc = new Document(dataDir + "MissingFont.docx");
```

私たちは`Document`オブジェクトを作成し、「MissingFont.docx」という名前のWord文書を読み込み、`dataDir`.

## ステップ3: HTML保存オプションの設定

ここで、フォント名が正しく解決されるように、ドキュメントを HTML として保存するためのオプションを設定しましょう。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

インスタンスを作成します`HtmlSaveOptions`と`SaveFormat.Html`。`PrettyFormat`オプションによりHTML出力がより読みやすくなり、`ResolveFontNames`フォント名が解決されることを保証します。

## ステップ4: ドキュメントをHTMLとして保存する

最後に、設定された保存オプションを使用してドキュメントを HTML ファイルとして保存します。

```csharp
doc.Save(dataDir + "ResolvedFontNames.html", saveOptions);
```

私たちは`Save`方法`Document`オブジェクトに、出力パスと設定した保存オプションを指定します。これにより、フォント名が解決された HTML ファイルが生成されます。

## 結論

これで完了です。これらの手順に従うことで、Aspose.Words for .NET を使用して Word 文書を HTML に変換するときにフォント名を正常に解決できました。これにより、フォントが正しく表示されるだけでなく、HTML 出力が洗練されてプロフェッショナルに見えるようになります。コーディングをお楽しみください。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによって Word 文書を作成、変更、変換できるようにする強力なライブラリです。

### Aspose.Words for .NET をインストールするにはどうすればよいですか?
 Aspose.Words for .NETは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/net/)ドキュメントに記載されているインストール手順に従ってください。

### ライセンスなしで Aspose.Words for .NET を使用できますか?
はい、ただし制限があります。フル機能を利用するにはライセンスを購入してください。[ここ](https://purchase.aspose.com/buy)または一時免許を取得する[ここ](https://purchase.aspose.com/temporary-license/).

### フォントが HTML で正しく表示されないのはなぜですか?
この問題は、変換中にフォントが適切に解決されない場合に発生する可能性があります。設定`ResolveFontNames = true`で`HtmlSaveOptions`これを修正するのに役立ちます。

### Aspose.Words for .NET のサポートはどこで受けられますか?
サポートを受けるには[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8).