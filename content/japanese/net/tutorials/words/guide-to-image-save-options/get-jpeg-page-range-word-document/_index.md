---
title: Word 文書の Jpeg ページ範囲を取得する
linktitle: Word 文書の Jpeg ページ範囲を取得する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書の特定のページを JPEG 画像に簡単に変換する方法を学びます。この包括的なガイドでは、文書の読み込み、画像設定の構成から JPEG として保存するまでのすべてを網羅しています。
type: docs
weight: 10
url: /ja/net/tutorials/words/guide-to-image-save-options/get-jpeg-page-range-word-document/
---
## 導入

Word 文書を画像に変換すると、オンライン プレビュー用のサムネイルを作成したり、よりアクセスしやすい形式でコンテンツを共有したりするなど、さまざまなアプリケーションで特に役立ちます。Aspose.Words for .NET を使用すると、明るさ、コントラスト、解像度などの設定をカスタマイズしながら、Word 文書の特定のページを JPEG 形式に簡単に変換できます。これを段階的に行う方法を見てみましょう。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.Words for .NET: ライブラリをダウンロード[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの C# IDE。
- サンプル文書: A`.docx`このチュートリアルで使用するファイル（例：`Rendering.docx`）。
- 基本的な C# の知識: C# プログラミングの概念に精通していること。

準備が整ったら、始めましょう!

## ステップ1: 必要な名前空間をインポートする

Aspose.Words の機能を使用するには、まずコード ファイルの先頭に必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ2: ドキュメントを読み込む

次に、変換する Word 文書を読み込みます。次のコードを調整して、文書へのパスを指定します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //実際のディレクトリパスに置き換えます
Document doc = new Document(dataDir + "Rendering.docx");
```

このコードスニペットはドキュメントパスを初期化し、それをAspose.Wordsに読み込みます。`Document`操作対象オブジェクト。

## ステップ3: 画像保存オプションを設定する

さて、設定しましょう`ImageSaveOptions`ページの選択、画像の明るさ、コントラスト、解像度など、JPEG の生成方法をカスタマイズします。

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); //最初のページのみ変換する
options.ImageBrightness = 0.3f;    //明るさを調整する
options.ImageContrast = 0.7f;      //コントラストを調整する
options.HorizontalResolution = 72f; //水平解像度を設定する
```

## ステップ4: ドキュメントをJPEGとして保存する

オプションを設定したら、指定した設定でドキュメントを JPEG 画像として保存します。

```csharp
doc.Save(dataDir + "ConvertedImage.jpeg", options);
```

この行は、選択したページを保存します`Rendering.docx`選択した明るさ、コントラスト、解像度を適用して JPEG ファイルに変換します。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書の特定のページを JPEG 画像に正常に変換できました。この方法は、Web サイトのサムネイルを作成したり、共有を容易にするためのドキュメント プレビューを生成したりするなど、さまざまなニーズに合わせて調整できます。

## よくある質問

### 複数のページを一度に変換できますか?  
もちろんです！ページの範囲を指定するには、`PageSet`不動産の`ImageSaveOptions`.

### 画質を調整するにはどうすればよいですか?  
 JPEG画質を向上させるには、`JpegQuality`不動産の`ImageSaveOptions`値の範囲は 0 (最低品質) から 100 (最高品質) です。

### 他の画像形式で保存できますか?  
はい、Aspose.WordsはPNG、BMP、TIFFなど、いくつかの画像形式をサポートしています。`SaveFormat`で`ImageSaveOptions`希望の形式に変更します。

### 保存する前に画像をプレビューする方法はありますか?  
Aspose.Words には組み込みのプレビュー機能は含まれていませんが、Windows フォームまたは WPF アプリケーションを使用してカスタム プレビュー メカニズムを構築できます。

### Aspose.Words の一時ライセンスを取得するにはどうすればよいですか?  
リクエストすることができます[一時ライセンスはこちら](https://purchase.aspose.com/temporary-license/)評価目的のため。