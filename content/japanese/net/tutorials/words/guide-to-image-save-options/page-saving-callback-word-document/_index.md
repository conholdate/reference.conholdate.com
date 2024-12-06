---
title: Word 文書でのページ保存コールバック
linktitle: Word 文書でのページ保存コールバック
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書の各ページを個別の PNG 画像に簡単に変換する方法を学びます。このガイドでは、コード例を含む手順を段階的に説明します。
type: docs
weight: 10
url: /ja/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## 導入

Word 文書の各ページを個別の画像に変換する必要があることはありませんか? プレビュー用のサムネイルを作成する場合でも、長いレポートをわかりやすいビジュアルに分割する場合でも、Aspose.Words for .NET を使用すると、このタスクが簡単かつ効率的になります。このガイドでは、ページ保存コールバックを設定して、文書の各ページを PNG 画像として保存する手順を説明します。さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: ダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
2. Visual Studio: どのバージョンでも動作しますが、このガイドでは Visual Studio 2019 を使用します。
3. 基本的な C# の知識: C# に精通していると、スムーズに理解できるようになります。

## ステップ1: 必要な名前空間をインポートする

まず、必要な名前空間をインポートする必要があります。これにより、毎回完全な名前空間を入力しなくても、必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ2: ドキュメントディレクトリを定義する

次に、ドキュメント ディレクトリへのパスを設定します。これは、入力 Word ドキュメントが保存される場所であり、出力画像が保存される場所です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ3: ドキュメントを読み込む

次に、処理するドキュメントを読み込みます。「Rendering.docx」という名前のドキュメントが指定されたディレクトリにあることを確認します。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ4: 画像保存オプションを設定する

ページを PNG ファイルとして保存することを指定して、画像を保存するためのオプションを設定します。

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

ここ、`PageSet`保存するページの範囲を定義し、`PageSavingCallback`カスタム コールバック クラスを指します。

## ステップ5: ページ保存コールバックを実装する

ここで、各ページの保存方法を処理するコールバック クラスを実装する必要があります。

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

このクラスは、`IPageSavingCallback`インターフェース。`PageSaving`メソッドでは、保存された各ページの命名パターンを指定します。

## ステップ6: ドキュメントを画像として保存する

最後に、設定されたオプションを使用してドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書の各ページを個別の PNG 画像として保存するためのページ保存コールバックを正常に設定しました。この手法は、ページ プレビューの作成からレポートの個別のページ画像の生成まで、さまざまなアプリケーションで非常に役立ちます。

## よくある質問

### PNG以外の形式でページを保存できますか?
はい！JPEG、BMP、TIFFなどの形式でページを保存できます。`SaveFormat`で`ImageSaveOptions`.

### 特定のページだけを保存するにはどうすればよいですか?
特定のページを保存するには、`PageSet`パラメータ`ImageSaveOptions`必要なページのみを含めます。

### 画質をカスタマイズすることは可能ですか？
もちろんです！次のようなプロパティを設定することで出力画像の品質を制御できます。`ImageSaveOptions.JpegQuality`.

### 大きな文書を効率的に処理するにはどうすればよいでしょうか?
大きなドキュメントの場合は、メモリ使用量を効率的に管理するために、ページをバッチで処理することを検討してください。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?
包括的なガイドと例については、[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/).