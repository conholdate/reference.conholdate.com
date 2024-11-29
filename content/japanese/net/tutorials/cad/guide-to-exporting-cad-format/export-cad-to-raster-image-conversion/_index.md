---
title: Aspose.CAD for .NET を使用した CAD からラスター イメージへの変換のエクスポート
linktitle: CADからラスターイメージへの変換エクスポート
second_title: Aspose.CAD .NET - CAD および BIM ファイル形式
description: Aspose.CAD for .NET を使用して、CAD レイアウトをさまざまなラスター イメージ形式に効率的に変換する方法を学びます。この包括的なガイドでは、明確なコードを使用してプロセスを順を追って説明します。
type: docs
weight: 10
url: /ja/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## 導入

Aspose.CAD for .NET を使用して、CAD レイアウトをラスター イメージ形式に簡単に変換したいとお考えですか? このステップ バイ ステップ ガイドは、プロセスをスムーズに進めるための簡潔なコード スニペットを完備しています。経験豊富な開発者でも、初心者でも、このチュートリアルはあらゆるスキル レベルに役立つ情報を提供します。

## 前提条件

始める前に、次のものがあることを確認してください。

- Aspose.CAD for .NETライブラリ: ライブラリを以下のサイトからダウンロードしてインストールします。[Aspose.CAD ウェブサイト](https://releases.aspose.com/cad/net/).
- CAD図面ファイル: CAD図面ファイル（例：`conic_pyramid.dxf`）変換の準備ができました。

## 必要な名前空間をインポートする

.NET プロジェクトでは、Aspose.CAD 関数を利用するために必要な名前空間をインポートする必要があります。コードの先頭に次のコードを追加します。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## ステップ1: CAD図面を読み込む

まず、ディレクトリを指定して、CAD ファイルをイメージ インスタンスに読み込みます。

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// CAD図面を読み込む
using (var image = Image.Load(sourceFilePath))
{
    //次のステップに進む
}
```

## ステップ2: ラスタライズオプションを作成する

次に、ラスタライズ オプションを設定し、出力イメージの希望する寸法を定義します。

```csharp
// CadRasterizationOptions を初期化する
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## ステップ3: 変換するレイヤーを指定する

特定のレイヤーを変換する場合は、ラスタライズ オプションに追加します。

```csharp
//変換するレイヤーを指定
rasterizationOptions.Layers = new [] { "LayerA" };
```

## ステップ4: JPEGエクスポートオプションを設定する

次に、エクスポートする画像形式 (この場合は JPEG) のオプションを作成します。

```csharp
//エクスポート用のJpegOptionsを作成する
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## ステップ5: JPEG形式にエクスポート

最後に、変換した画像を保存します。

```csharp
//出力ファイルのパスを定義して画像を保存する
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## 追加機能: すべてのレイヤーを変換

CAD 図面内のすべてのレイヤーを変換するには、次のようなメソッドを実装できます。

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    //レイヤーを反復処理し、それぞれを個別のJPEGファイルとして保存します。
    //実装コードをここに入力
}
```

## 結論

おめでとうございます。Aspose.CAD for .NET を使用して、CAD レイアウトをラスター イメージ形式に効果的に変換する方法を学習しました。このガイドでは、効率的な CAD 変換を目指す開発者に適した簡単なアプローチを紹介します。

## よくある質問

### 異なる画像形式にエクスポートできますか?

もちろんです！`JpegOptions`他のフォーマットオプション、例えば`PngOptions`または`BmpOptions`ニーズに応じてお選びいただけます。

### 試用版はありますか？

はい、以下の手順で試用版をダウンロードして機能を試してみることができます。[リンク](https://releases.aspose.com/cad/net/).

### Aspose.CAD のサポートはどこで受けられますか?

コミュニティサポートについては、Aspose.CADをご覧ください。[フォーラム](https://forum.aspose.com/c/cad/19)、またはより専門的なサポートが必要な場合はライセンスの購入を検討してください。

### 一時ライセンスは可能ですか?

はい、一時ライセンスは利用可能です。リクエストすることができます。[ここ](https://purchase.conholdate.com/temporary-license/).

### 詳細なドキュメントにはどこでアクセスできますか?

包括的なドキュメントをご覧ください[ここ](https://reference.aspose.com/cad/net/)詳細についてはこちらをご覧ください。