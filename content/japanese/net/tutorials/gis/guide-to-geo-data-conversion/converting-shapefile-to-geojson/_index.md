---
title: Aspose.GIS for .NET を使用した Shapefiles から GeoJSON への変換
linktitle: シェイプファイルを GeoJSON に変換する
second_title: Aspose.GIS .NET API
description: 強力な Aspose.GIS for .NET ライブラリを使用して、Shapefiles を GeoJSON 形式に簡単に変換する方法を学びます。この包括的なチュートリアルでは、必須の前提条件とステップバイステップのコード例について説明します。
type: docs
weight: 15
url: /ja/net/tutorials/gis/guide-to-geo-data-conversion/converting-shapefile-to-geojson/
---
## 導入

地理情報システム (GIS) の世界では、データの相互運用性は、効果的な分析と統合に不可欠です。一般的なタスクは、Shapefiles (一般的な地理空間ベクター データ形式) を GeoJSON (地理空間データ用の軽量形式) に変換することです。このチュートリアルでは、Aspose.GIS for .NET ライブラリを使用して Shapefiles を GeoJSON に簡単に変換するプロセスについて説明します。

## 前提条件
変換プロセスを開始する前に、次のものを用意してください。

1. Aspose.GIS for .NET ライブラリがインストールされている  
   Aspose.GIS for .NETライブラリのインストール手順については、[ドキュメント](https://reference.aspose.com/gis/net/).

2. 入力シェープファイル  
   変換用の Shapefile を用意します。Shapefile は、オープン データ ポータルや政府機関からダウンロードすることも、QGIS や ArcGIS などの GIS ソフトウェアを使用して作成することもできます。

3. C#の基礎知識  
   C# の基礎を理解しておくと、このチュートリアルに含まれるコード例を理解するのに役立ちます。

## 必要な名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
```csharp
using Aspose.Gis;
using System;
```

## ステップ1: 入力パスと出力パスを定義する
まず、入力 Shapefile と目的の出力 GeoJSON ファイルのパスを設定します。
```csharp
string dataDir = @"C:\Your\Document\Directory\";
string shapefilePath = System.IO.Path.Combine(dataDir, "InputShapeFile.shp");
string jsonPath = System.IO.Path.Combine(dataDir, "output_out.json");
```
必ず交換してください`@"C:\Your\Document\Directory\"`ファイルが配置されている実際のパスを入力します。

## ステップ2: 変換を実行する
活用する`VectorLayer.Convert`変換を実行する方法:
```csharp
VectorLayer.Convert(shapefilePath, Drivers.Shapefile, jsonPath, Drivers.GeoJson);
```
このコードは入力Shapefile（`shapefilePath` ）をGeoJSON形式に変換し、指定された場所に保存します。`jsonPath`.

## 結論
シェープファイルを GeoJSON に変換することは、GIS データ処理における基本的な操作です。Aspose.GIS for .NET ライブラリは、このタスクを簡素化し、開発者が地理空間データをアプリケーションに簡単に統合できるようにします。このチュートリアルで説明する手順に従うことで、変換を効率的に実行し、GIS データの相互運用性と分析機能を向上させることができます。

## よくある質問

### 複数のシェープファイルを一度に変換できますか?
はい。Shapefiles のディレクトリをループし、サンプル コードを少し調整するだけでまとめて変換できます。

### Aspose.GIS for .NET はすべての .NET Framework バージョンと互換性がありますか?
Aspose.GIS for .NET は、.NET Framework 4.5 以降をサポートしています。

### ライブラリは他の地理空間形式をサポートしていますか?
もちろんです! ライブラリは、GeoTIFF、KML、GML など、さまざまな地理空間形式をサポートしています。

### 変換プロセスをカスタマイズできますか?
はい、Aspose.GIS for .NET では広範なカスタマイズ オプションが使用できるため、必要に応じて座標系や属性マッピングを指定できます。

### 試用版はありますか?
はい、Aspose.GIS for .NETの無料試用版をこちらからダウンロードできます。[Aspose ウェブサイト](https://releases.aspose.com/).