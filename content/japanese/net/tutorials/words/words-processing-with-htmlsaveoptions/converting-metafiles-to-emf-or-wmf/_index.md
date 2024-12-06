---
title: メタファイルを EMF または WMF に変換する
linktitle: メタファイルを EMF または WMF に変換する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書内の SVG イメージを EMF または WMF 形式にシームレスに変換する方法を学びます。正確で互換性のある結果を得るためのコード例を含むステップバイステップ ガイドです。
type: docs
weight: 10
url: /ja/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## 導入

画像形式を効率的に管理および変換することは、プロフェッショナルな Word 文書を作成する上で非常に重要です。このガイドでは、Aspose.Words for .NET を使用して SVG 画像を EMF (拡張メタファイル) または WMF (Windows メタファイル) 形式に変換し、シームレスに統合する方法について詳しく説明します。このチュートリアルでは、開発者が変換を簡単に実装できるように、わかりやすい手順を説明します。

## SVG を EMF または WMF に変換するための前提条件

スムーズな開発エクスペリエンスを確保するには、次の前提条件が満たされていることを確認してください。

- Aspose.Words for .NET: 最新バージョンを以下から入手してください。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
- .NET Framework: .NET Framework (または環境に応じて .NET Core/5/6) のインストールを確認します。
- 開発環境: 強力な機能を備えた Visual Studio が推奨されます。
- C# の熟練度: C# プログラミングに関する基本的な知識が必須です。

## 必要な名前空間のインポート

プロジェクトで、Aspose.Words 機能にアクセスするために必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを定義する

Word 文書を保存するディレクトリ パスを設定します。これは、出力ファイルを効率的に管理するために不可欠です。

```csharp
string dataDir = @"C:\MyDocuments\";
```

交換する`@"C:\MyDocuments\"`ご希望のパスで。

## ステップ2: SVGを含むHTML文字列を準備する

SVG コンテンツを埋め込む HTML 文字列を作成します。これにより、Aspose.Words は SVG をレンダリングおよび処理できるようになります。

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' 幅='300' 高さ='100' ビューボックス='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## ステップ3: HTML読み込みオプションを構成する

 SVG変換を適切に処理するには、`HtmlLoadOptions`と`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## ステップ4: HTMLをWord文書に読み込む

設定されたロードオプションを使用して、`Document` HTML 文字列からのオブジェクト。

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## ステップ5: EMF/WMFの保存オプションを設定する

保存オプションをカスタマイズして、希望するメタファイル形式を定義します。ここでは、`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## ステップ6: ドキュメントを保存する

指定された保存オプションを使用してドキュメントを保存します。

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

結果のファイルには、EMF 形式に変換された SVG コンテンツが含まれます。

## 結論

このチュートリアルでは、Aspose.Words for .NET を使用して SVG 画像を EMF または WMF 形式に変換する方法について説明しました。これらの手順に従うことで、Word 文書の互換性と視覚的な忠実度を高めることができます。文書作成を自動化する場合でも、高品質のレポートを準備する場合でも、この方法によりシームレスな結果が保証されます。

## よくある質問

### この方法を使用して複数の SVG をバッチ処理できますか?
はい、SVG を含む複数の HTML ファイルを反復処理し、ループで同じプロセスを適用できます。

### EMF と WMF の違いは何ですか?
EMF は WMF の拡張バージョンであり、複雑なグラフィックスと大きなデータ サイズをより適切にサポートします。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Core と .NET 5/6 をサポートしているため、最新のクロスプラットフォーム アプリケーションに適しています。

### 出力で元の SVG 形式を保持できますか?
いいえ、この方法では SVG を EMF/WMF に変換します。ただし、変換せずにドキュメントに直接埋め込むことで、元の SVG を保持できます。

### Aspose.Words の無料試用版はどこからダウンロードできますか?
無料トライアルは以下からダウンロードできます。[Aspose リリース ページ](https://releases.aspose.com/).