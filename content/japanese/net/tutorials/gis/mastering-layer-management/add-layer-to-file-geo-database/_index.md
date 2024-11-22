---
title: Aspose.GIS for .NET を使用してファイル ジオデータベースにレイヤーを追加する
linktitle: ファイルジオデータベースにレイヤーを追加する
second_title: Aspose.GIS .NET API
description: Aspose.GIS for .NET を使用して、ファイル ジオデータベース (GDB) に新しいレイヤーを追加する方法を学びます。この包括的なガイドでは、GIS データセットでレイヤーを作成および検証するための前提条件、名前空間のインポート、詳細な手順について説明します。
type: docs
weight: 16
url: /ja/net/tutorials/gis/mastering-layer-management/add-layer-to-file-geo-database/
---
## 導入

地理情報システム (GIS) テクノロジは、現代のデータ分析と視覚化において極めて重要な役割を果たしています。Aspose.GIS for .NET は、開発者が地理データを効率的に操作できるようにする優れたライブラリです。この詳細なガイドでは、Aspose.GIS for .NET を使用して、ファイル ジオデータベース (GDB) データセットに新しいレイヤーを追加する方法について説明します。これらの包括的な手順に従って、レイヤーをシームレスに統合し、GIS 機能を強化します。

## ファイル GDB にレイヤーを追加するための前提条件

先に進む前に、以下のものを用意してください。

1. Aspose.GIS for .NET ライブラリ  
   ライブラリをダウンロードしてインストールするには、[Aspose.GIS for .NET ページ](https://reference.aspose.com/gis/net/).

2. ファイルジオデータベース (GDB) データセット  
   操作用の GDB データセットが存在していることを確認してください。

3. 開発環境  
   .NET をサポートする好みの IDE (Visual Studio など) をインストールして構成します。

4. 一時ライセンス（オプション）  
   フル機能の評価については、[一時ライセンス](https://purchase.conholdate.com/temporary-license/).

5. データディレクトリ  
   入力データセットと出力データセットを管理するためのディレクトリを準備します。

## 必要な名前空間のインポート

コーディングする前に、Aspose.GIS 機能にアクセスするための重要な名前空間を含めます。プロジェクトの先頭に次のコード スニペットを追加します。

```csharp
using Aspose.Gis;
using Aspose.Gis.Geometries;
using Aspose.Gis.SpatialReferencing;
using System;
```

## ステップ1: GDBデータセットを複製する

元のデータセットの整合性を保つには、複製を作成します。データセットを新しい場所にコピーするには、次のコードを使用します。

```csharp
string dataDir = "C:\\GISData\\"; //データセットを含むディレクトリ
string originalPath = dataDir + "ExistingDataset.gdb";
string newDatasetPath = dataDir + "ModifiedDataset.gdb";

//ディレクトリを複製する機能
RunExamples.CopyDirectory(originalPath, newDatasetPath);
```

## ステップ2: データセットを開いて作成機能を確認する

Aspose.GIS を使用すると、開発者はデータセットを開いて、新しいレイヤーを追加できるかどうかを確認できます。データセットの作成機能を確認するには、次のスニペットを使用します。

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    Console.WriteLine($"Can Create Layers: {dataset.CanCreateLayers}"); // Trueを返す必要があります
}
```

## ステップ3: データセットに新しいレイヤーを作成する

レイヤーを追加するには、空間参照システムと属性を定義する必要があります。サンプル データを使用してレイヤーを作成し、設定する方法は次のとおりです。

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    // WGS 84空間参照システムで新しいレイヤーを作成する
    using (var layer = dataset.CreateLayer("NewLayer", SpatialReferenceSystem.Wgs84))
    {
        //属性スキーマを追加する
        layer.Attributes.Add(new FeatureAttribute("LocationName", AttributeDataType.String));

        //機能を作成して追加する
        var feature = layer.ConstructFeature();
        feature.SetValue("LocationName", "Sample Point");
        feature.Geometry = new Point(34.0522, -118.2437); //経度と緯度
        layer.Add(feature);
    }
}
```

## ステップ4: 新しいレイヤーを開いて検証する

レイヤーを作成したら、その内容を検証して正確性を確認します。次のコード スニペットを使用します。

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    using (var layer = dataset.OpenLayer("NewLayer"))
    {
        Console.WriteLine($"Feature Count: {layer.Count}");
        Console.WriteLine($"Attribute Value: {layer[0].GetValue<string>("LocationName")}");
    }
}
```

## 結論

Aspose.GIS for .NET を使用してファイル ジオデータベース データセットにレイヤーを追加するのは、次の手順に従うと簡単なプロセスです。データセットの複製からレイヤーの作成と検証まで、ライブラリは GIS データを管理するための強力なツールを提供します。これらのテクニックを習得することで、GIS ワークフローを強化し、効率的な地理データ操作を実現できます。

## よくある質問

### Aspose.GIS for .NET は何に使用されますか?
Aspose.GIS for .NET は、シェープファイル、GDB などのさまざまなファイル形式をサポートし、地理データを処理および操作するために設計されたライブラリです。

### 1 回の操作で複数のレイヤーを追加できますか?
はい、Aspose.GIS ではデータセット内で複数のレイヤーを作成および管理できます。

### どのような空間参照システムがサポートされていますか?
このライブラリは、WGS 84、NAD 83、カスタム CRS など、多数の空間参照システムをサポートしています。

### サポートはどこで受けられますか?
訪問する[Aspose.GIS フォーラム](https://forum.aspose.com/c/gis/33)コミュニティの議論とサポートのため。

### 無料トライアルはありますか？
はい、[無料トライアル](https://releases.aspose.com/)ライブラリの機能をテストするために利用できます。