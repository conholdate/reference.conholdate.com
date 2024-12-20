---
title: ブラッドリー二値化アルゴリズム
linktitle: ブラッドリー二値化アルゴリズム
second_title: Aspose.PDF for .NET API リファレンス
description: Aspose.PDF for .NET の Bradley バイナリ化アルゴリズムを使用して、PDF ページを高品質のバイナリ TIFF 画像に変換する方法を学びます。このステップ バイ ステップ ガイドにはコード例が含まれています。
type: docs
weight: 30
url: /ja/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## 導入

このチュートリアルでは、Bradley バイナリ化アルゴリズムを使用して PDF ページを TIFF 画像に変換するプロセスについて説明します。Aspose.PDF for .NET を使用すると、このタスクが簡素化され、ドキュメント ワークフローを簡単に自動化および合理化できます。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.PDF for .NET: ライブラリをダウンロード[ここ](https://releases.aspose.com/pdf/net/).
- Visual Studio (または任意の C# IDE)。
- C# の基礎知識。
- 有効な免許証または[一時ライセンス](https://purchase.aspose.com/temporary-license/)Aspose より。

## ステップ1: プロジェクトを設定する

まず、IDE で新しい C# プロジェクトを作成し、必要な名前空間をインポートします。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## ステップ2: ドキュメントディレクトリを定義する

PDF ドキュメントが保存されているディレクトリへのパスと、TIFF 画像の出力パスを指定します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // PDFファイルへのパス
```

このディレクトリには、ソース PDF ファイルと変換された TIFF ファイルの両方が保存されます。

## ステップ3: PDFドキュメントを読み込む

変換したい PDF ドキュメントを開きます。

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

交換する`PageToTIFF.pdf` PDF ファイルの名前を入力します。

## ステップ4: 出力パスを指定する

生成された TIFF ファイルの出力パスを定義します。

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## ステップ5: 画像の解像度を設定する

TIFF 画像の解像度を設定します。DPI が高いほど、画像の品質が向上します。

```csharp
Resolution resolution = new Resolution(300);
```

## ステップ6: TIFF設定を構成する

圧縮や色深度など、TIFF 画像の設定を構成します。

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

1bpp (ピクセルあたり 1 ビット) を使用すると、画像はバイナリ出力用に準備されます。

## ステップ7: TIFFデバイスを作成する

変換を処理する TIFF デバイスを作成します。

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## ステップ8: PDFページをTIFFに変換する

PDF の最初のページを TIFF 画像に変換します。

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## ステップ9: Bradley二値化アルゴリズムを適用する

次に、Bradley アルゴリズムを適用して、グレースケール TIFF 画像をバイナリ画像に変換します。

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

の`BinarizeBradley`このメソッドは、2 つのファイル ストリーム (入力と出力) としきい値を受け取ります。最適な結果を得るために、必要に応じてしきい値を調整します。

## ステップ10: 変換が成功したことを確認する

最後に、変換が成功したことを確認します。

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## 結論

おめでとうございます! Aspose.PDF for .NET を使用して PDF ページを TIFF 画像に変換し、Bradley 2 値化アルゴリズムを適用しました。このプロセスは、ドキュメントのアーカイブ、OCR、およびその他の専門的なアプリケーションに不可欠です。高品質の解像度と効率的な圧縮により、ドキュメント画像は鮮明になり、サイズも管理しやすくなります。

## よくある質問

### ブラッドリーアルゴリズムとは何ですか?
ブラッドリー アルゴリズムは、周囲の状況に基づいて各ピクセルの適応しきい値を決定することにより、グレースケール画像をバイナリ画像に変換するバイナリ化手法です。

### この方法を使用して複数の PDF ページを TIFF に変換できますか?
はい、変更できます`Process`ドキュメント内のすべてのページをループして変換するメソッド。

### PDF を TIFF に変換する場合の最適な解像度は何ですか?
高品質の画像の場合は通常 300 DPI の解像度が推奨されますが、特定のニーズに応じて調整できます。

### 色深度における 1bpp とはどういう意味ですか?
1bpp (ピクセルあたり 1 ビット) は、画像が白黒になり、各ピクセルが完全に黒か完全に白になることを示します。

### Bradley アルゴリズムは OCR に適していますか?
はい、Bradley アルゴリズムは、スキャンされたドキュメント内のテキストのコントラストを強調し、認識精度を向上させるため、OCR の前処理でよく使用されます。