---
title: Aspose.CAD for .NET で DGN を PDF に変換する
linktitle: Aspose.CAD for .NET で DGN を PDF に変換する
second_title: Aspose.CAD .NET - CAD および BIM ファイル形式
description: 強力な .NET 用 Aspose.CAD ライブラリを使用して、DGN ファイルを PDF に簡単に変換する方法を学びます。このステップ バイ ステップ ガイドは、あらゆるレベルの開発者向けに設計されています。
type: docs
weight: 12
url: /ja/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## 導入

CAD ファイルの世界をナビゲートするのは難しい場合がありますが、Aspose.CAD for .NET を使用すると、開発者はさまざまな CAD 形式を簡単に操作および変換できます。一般的なニーズの 1 つは、DGN ファイルを PDF に変換することです。このチュートリアルでは、これを手順ごとに説明します。

## 前提条件

この手順を実行するには、次のものを用意してください。

- C# および .NET フレームワークの基本的な能力。
-  Aspose.CAD for .NETライブラリがインストールされています。ダウンロードできます。[ここ](https://releases.aspose.com/cad/net/).
- サンプル DGN ファイル (例: Nikon_D90_Camera.dgn)。 

## ステップ1: 必要な名前空間をインポートする

まず、C# プロジェクトに関連する名前空間をインポートします。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## ステップ2: DGNファイルを読み込む

DGN ファイルのディレクトリを指定し、次のコードを使用してロードします。

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    //追加の処理はここで行われます...
}
```

## ステップ3: ラスタライズオプションを構成する

次に、ラスタライズ オプションを設定して、DGN を PDF でどのようにレンダリングするかを定義します。

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, //必要に応じて幅を調整します
    PageHeight = 300, //必要に応じて高さを調整します
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## ステップ4: PDFオプションを作成する

以前に構成したラスタライズ設定を統合して、PDF オプションを定義します。

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## ステップ5: DGNをPDFとして保存する

最後に、設定したオプションを使用して DGN ファイルを PDF として保存します。

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## 結論

おめでとうございます! Aspose.CAD for .NET を使用して、DGN ファイルを PDF に正常に変換できました。このわかりやすいチュートリアルでは、DGN ファイルの読み込み、ラスタライズ オプションの設定、出力の PDF としての保存について説明しました。

## よくある質問

### Aspose.CAD を使用するには、事前に CAD の知識が必要ですか?  
もちろんです! Aspose.CAD は、複雑な CAD タスクを簡素化するように設計されており、CAD の知識に関係なく、すべての開発者が利用できます。

### Aspose.CAD のその他のリソースやドキュメントはどこで入手できますか?  
包括的なガイドと例については、[Aspose.CAD ドキュメント](https://reference.aspose.com/cad/net/).

### Aspose.CAD の無料試用版はありますか?  
はい、無料トライアルをご利用いただけます[ここ](https://releases.aspose.com/).

### Aspose.CAD の一時ライセンスを取得するにはどうすればよいですか?  
一時ライセンスを申請できます[ここ](https://purchase.conholdate.com/temporary-license/).

### サポートが必要ですか、または質問がありますか?  
会話に参加してください[Aspose.CAD フォーラム](https://forum.aspose.com/c/cad/19)コミュニティのサポートとお問い合わせ。