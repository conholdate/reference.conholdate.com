---
title: .NET で Aspose.CAD を使用して DGN ファイル操作をマスターする
linktitle: DGN ファイル操作の習得
second_title: Aspose.CAD .NET - CAD および BIM ファイル形式
description: Aspose.CAD ライブラリの強力な機能を活用しながら、DGN ファイルを読み込み、その要素を反復処理し、2D エンティティと 3D エンティティの両方を管理し、ラスター イメージとしてエクスポートする方法を学習します。
type: docs
weight: 18
url: /ja/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## 導入

DGN ファイルをアプリケーションに統合したい .NET 開発者ですか? Aspose.CAD for .NET は、DGN ファイル形式を扱うために特別に設計された強力なライブラリを提供します。このチュートリアルでは、サポートされている要素や .NET プロジェクトでの操作方法など、DGN ファイルを効率的に処理する方法を説明します。

## 前提条件

始める前に、次の設定がされていることを確認してください。

- .NET プログラミングの基礎知識: C# または VB.NET に精通していると有利です。
- Visual Studio: プロジェクト開発用にマシンにインストールされます。
-  アポーズ for .NETライブラリ: ダウンロードはこちらから[Aspose.CAD](https://releases.aspose.com/cad/net/).

## ステップ1: 必要な名前空間をインポートする

Aspose.CAD の機能を活用するには、まず必要な名前空間をプロジェクトにインポートします。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## ステップ2: DGNファイルを読み込む

まず、既存のDGNファイルをアプリケーションに読み込みます。これは、`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    //ここで論理を進めてください
}
```

## ステップ3: DGN要素を反復処理する

DGN ファイルが読み込まれると、その要素を反復処理できます。Aspose.CAD では、操作用にさまざまな DGN 要素タイプが提供されています。

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    //各要素を処理する
}
```

## ステップ4: 2Dおよび3Dエンティティの処理

2D と 3D の DGN 要素を区別できます。これらを効率的に処理する方法は次のとおりです。

### 2Dエンティティの処理

以前サポートされていた 2D エンティティを switch-case ブロックで管理できます。

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        //ここに処理ロジックを追加します
        break;
}
```

### 3Dエンティティの処理

同様に、3D エンティティを次のように処理します。

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        //ここに処理ロジックを追加します
        break;
}
```

## ステップ5: DGNファイルをエクスポートする

DGN 要素を操作した後、ファイルをラスター イメージとしてエクスポートする必要がある場合があります。これは、Aspose.CAD を使用すると簡単に実行できます。

```csharp
string outputFilePath = myDir + "Exported_Image.png"; //出力パスを定義する
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## 結論

このチュートリアルでは、Aspose.CAD for .NET を使用して DGN ファイルを効果的に管理する方法を学びました。概要の手順に従うことで、2D と 3D の両方の DGN 要素を簡単に処理し、ラスター イメージとしてエクスポートできます。この強力なライブラリにより、DGN 処理を .NET アプリケーションにシームレスに統合し、プロジェクト機能を強化することができます。

## よくある質問

### Aspose.CAD for .NET のドキュメントはどこにありますか?

包括的なドキュメントが利用可能[ここ](https://reference.aspose.com/cad/net/).

### Aspose.CAD for .NET をダウンロードするにはどうすればいいですか?

ライブラリの最新バージョンをダウンロードできます[ここ](https://releases.aspose.com/cad/net/).

### Aspose.CAD for .NET の無料試用版はありますか?

はい、無料トライアルをご利用いただけます[ここ](https://releases.aspose.com/).

### Aspose.CAD for .NET の一時ライセンスを取得するにはどうすればよいですか?

一時ライセンスを申請できます[ここ](https://purchase.conholdate.com/temporary-license/).

### ヘルプが必要ですか、または質問がありますか?

サポートや質問については、Aspose.CAD コミュニティにアクセスしてください。[サポートフォーラム](https://forum.aspose.com/c/cad/19).