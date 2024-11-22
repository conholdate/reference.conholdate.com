---
title: Aspose.Page for .NET を使用して XPS を PDF に変換する
linktitle: XPS から PDF への変換
second_title: Aspose.Page .NET API
description: 強力な Aspose.Page for .NET ライブラリを使用して、XPS (XML Paper Specific) ドキュメントを PDF (Portable Document Format) にシームレスに変換する方法を説明します。
type: docs
weight: 11
url: /ja/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## 導入

このチュートリアルでは、多機能な Aspose.Page for .NET ライブラリを使用して、XPS (XML Paper Specific) ドキュメントを PDF (Portable Document Format) に変換する方法について説明します。この強力なライブラリは、ドキュメント変換を簡素化し、さまざまなカスタマイズ オプションを提供するため、開発者にとって最適な選択肢となります。

## 前提条件

始める前に、以下のものを用意しておいてください。

-  Aspose.Page for .NETライブラリ: Aspose.Page for .NETライブラリを以下のサイトからダウンロードしてインストールします。[Aspose.Page ドキュメント](https://reference.aspose.com/page/net/).
  
- 開発環境: Visual Studio または互換性のある他の IDE を使用して .NET 開発環境をセットアップします。

- XPS ドキュメント: 変換する XPS ファイルを準備し、指定されたディレクトリに保存します。

## ステップ1: 必要な名前空間をインポートする

まず、Aspose.Page 機能にアクセスするために必要な名前空間をインポートします。

```csharp
using Aspose.Page.XPS;
```

## ステップ2: ドキュメントディレクトリを初期化する

ドキュメントが保存されるディレクトリ パスを定義します。

```csharp
string dataDir = "Your Document Directory";
```

必ず交換してください`"Your Document Directory"` XPS ドキュメントを含むディレクトリへの実際のパスを入力します。

### ステップ3: PDFおよびXPSストリームを開く

次に、入力 XPS ファイルと出力 PDF ファイルの両方のストリームを初期化します。

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

ファイルに正しいパスが設定されていることを確認してください。

### ステップ4: XPSドキュメントを読み込む

次に、Aspose.Page ライブラリを使用して XPS ドキュメントを読み込みます。

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### ステップ5: PDF保存オプションを設定する

画像の品質や圧縮パラメータなど、PDF の保存オプションを設定します。

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // JPEG品質レベルを設定する
    ImageCompression = PdfImageCompression.Jpeg, //画像にはJPEG圧縮を使用する
    TextCompression = PdfTextCompression.Flate, //テキストにFlate圧縮を適用する
    PageNumbers = new int[] { 1, 2, 6 } //含めるページ番号を指定する
};
```

必要に応じてこれらのパラメータを自由に調整してください。

### ステップ6: PDFレンダリングデバイスを作成する

PDF 形式のレンダリング デバイスを作成します。

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### ステップ7: ドキュメントをPDFとして保存する

最後に、指定したデバイスとオプションを使用して XPS ドキュメントを PDF に保存します。

```csharp
document.Save(device, options);
```

## 結論

おめでとうございます! Aspose.Page for .NET を使用して XPS ドキュメントを PDF に正常に変換できました。このライブラリはドキュメント変換を簡素化するだけでなく、さまざまな形式を処理するための広範な機能も提供します。

## よくある質問

### 複数の XPS ファイルを 1 つの PDF に変換できますか?

もちろんです! 同じ変換手順に従って、複数の XPS ファイルを反復処理し、それらを 1 つの PDF ドキュメントに結合することができます。

### Aspose.Page for .NET は他にどのような出力形式をサポートしていますか?

Aspose.Page for .NET は、PDF に加えて、TIFF、JPEG、PNG などのさまざまな形式をサポートしています。

### 変換された PDF の外観をカスタマイズするにはどうすればよいですか?

パラメータを調整することができます`PdfSaveOptions`JPEG 品質や圧縮設定など、オブジェクトを調整して、希望する外観を実現します。

### Aspose.Page for .NET の試用版はありますか?

はい、Aspose.Page for .NET を無料トライアルで試すことができます。[ここ](https://releases.aspose.com/).

### Aspose.Page for .NET のコミュニティ サポートはどこで見つかりますか?

コミュニティの議論やサポートについては、[Aspose.Page フォーラム](https://forum.aspose.com/c/page/39).