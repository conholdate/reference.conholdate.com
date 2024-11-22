---
title: Aspose.PSD for .NET で Bradley しきい値処理を適用する
linktitle: ブラッドリー閾値を適用する
second_title: Aspose.PSD .NET API
description: PSD ファイルを読み込み、しきい値設定手法を適用し、結果をさまざまな形式で保存して、さまざまなアプリケーションの画像セグメンテーション タスクを強化する方法を段階的に学習します。
type: docs
weight: 15
url: /ja/net/tutorials/psd/guide-image-processing/apply-bradley-thresholding/
---
## 導入

Aspose.PSD for .NET を使用して Bradley しきい値手法を適用するチュートリアルへようこそ。この強力なライブラリを使用すると、.NET アプリケーション内で Photoshop ファイルをシームレスに操作できます。Bradley しきい値化は、画像を 2 値化する効果的な方法で、オブジェクトを背景から区別するのに役立ちます。

## 前提条件

プロセスに進む前に、次の前提条件を満たしていることを確認してください。

-  Aspose.PSD for .NETライブラリ: 最新バージョンをダウンロードしてインストールしてください。[ドキュメント](https://reference.aspose.com/psd/net/).
- ドキュメント ディレクトリ: ソース PSD ファイルと出力されたバイナリ化された画像を保存するための作業ディレクトリを作成します。

## 必要な名前空間をインポートする

Aspose.PSD 機能にアクセスするために、関連する名前空間をインポートしてプロジェクトを開始します。

```csharp
// Aspose.PSD 名前空間をインポートする
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## ステップ1: ソースイメージを読み込む

ソース PSD ファイルと出力ファイルの名前とともに、ドキュメント ディレクトリへのパスを定義します。

```csharp
//ドキュメントディレクトリへのパスを指定します
string dataDir = "Your Document Directory";

string sourceFile = Path.Combine(dataDir, "sample.psd");
string outputFile = Path.Combine(dataDir, "binarized_out.png");
```

## ステップ2: ブラッドリーしきい値を適用する

次に、PSD イメージを読み込み、しきい値を選択し、Bradely しきい値を適用して、結果を保存します。

```csharp
// PSD画像を読み込む
using (PsdImage image = (PsdImage)Image.Load(sourceFile))
{
    //しきい値を設定します（必要に応じてこの値を試してみてください）
    double threshold = 0.15;

    //ブラッドリー法を使用して画像を2値化する
    image.BinarizeBradley(threshold);

    //2値化した画像をPNG形式で保存する
    image.Save(outputFile, new PngOptions());
}
```

## 結論

おめでとうございます! Aspose.PSD for .NET を使用して Bradley Threshold テクニックを実装できました。この方法により、ドキュメント分析からグラフィック デザインまで、さまざまなアプリケーションの画像セグメンテーションを大幅に改善できます。

## よくある質問

### Bradley Threshold はどんな種類の画像にも適用できますか?

もちろんです! Bradley しきい値化は汎用性が高く、ほとんどの画像タイプに適用してセグメンテーションを強化できます。

### Aspose.PSD の詳細情報はどこで入手できますか?

詳細なドキュメントとリソースについては、[Aspose.PSD ドキュメント](https://reference.aspose.com/psd/net/).

### 試用版はありますか？

はい！Aspose.PSD for .NETを無料トライアルで試すことができます。[ここ](https://releases.aspose.com/).

### Aspose.PSD のサポートを受けるにはどうすればよいですか?

コミュニティのサポートとディスカッションについては、[Aspose.PSD フォーラム](https://forum.aspose.com/c/psd/34).

### Aspose.PSD のライセンスを購入するにはどうすればよいですか?

ライセンスは直接購入できます[ここ](https://purchase.conholdate.com/buy).