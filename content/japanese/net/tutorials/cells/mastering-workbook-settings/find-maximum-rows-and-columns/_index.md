---
title: XLS および XLSX 形式の最大行数と最大列数を見つける
linktitle: XLS および XLSX 形式の最大行数と最大列数を見つける
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET ライブラリを利用して、Excel で大規模なデータセットを効率的に管理する方法を学びます。このガイドでは、XLS および XLSX ファイル形式の両方でサポートされている行と列の最大数を識別するための手順を説明します。
type: docs
weight: 11
url: /ja/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## 導入

Excel で大規模なデータセットを管理するのは、特にさまざまなファイル形式の制限を考慮すると、困難な場合があります。このチュートリアルでは、Aspose.Cells for .NET ライブラリを使用して、XLS (Excel 97-2003) および XLSX (Excel 2007 以降) 形式でサポートされている行と列の最大数を判断する方法について説明します。最後には、Excel 関連のタスクを効率的に処理できるようになります。

## 前提条件

始める前に、以下のものを用意してください。

1. [.NET フレームワーク](https://dotnet.microsoft.com/en-us/download)または[.NET コア](https://dotnet.microsoft.com/en-us/download)システムにインストールされています。
2. [.NET 用 Aspose.Cells](https://releases.aspose.com/cells/net/)ライブラリをダウンロードしてプロジェクトで参照します（[ヌゲット](https://www.nuget.org/packages/Aspose.Cells/)）。

## 必要なパッケージのインポート

Aspose.Cells ライブラリから必要なパッケージをインポートするには、C# ファイルの先頭に次の using ステートメントを追加します。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## ステップ 1: XLS 形式の最大行数と最大列数

まず、XLS 形式でサポートされている最大行数と最大列数を調べてみましょう。

```csharp
// XLS 形式に関するメッセージを印刷します。
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// XLS 形式でワークブックを作成します。
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

//最大行数と最大列数を取得します。
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

//結果を表示します。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. XLS 形式で作業していることを示すメッセージを出力します。
2. 作成する`Workbook` XLS形式のインスタンス`FileFormatType.Excel97To2003`.
3. 最大の行と列を取得する`wb.Settings.MaxRow`そして`wb.Settings.MaxColumn`これらはゼロベースなので 1 を加算します。
4. 最大行数と最大列数をコンソールに出力します。

## ステップ 2: XLSX 形式の最大行数と最大列数

次に、XLSX 形式でサポートされる最大行数と最大列数について説明します。

```csharp
// XLSX 形式に関するメッセージを印刷します。
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// XLSX 形式でワークブックを作成します。
wb = new Workbook(FileFormatType.Xlsx);

//最大行数と最大列数を取得します。
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

//結果を表示します。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. XLSX 形式で作業していることを示すメッセージを出力します。
2. 作成する`Workbook` XLSX形式のインスタンス`FileFormatType.Xlsx`.
3. 前と同じように、最大の行と列を取得して出力します。

## ステップ3: 成功メッセージを表示する

手順を実行したら、成功を示しましょう。

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## 結論

このチュートリアルでは、Aspose.Cells for .NET ライブラリを使用して、XLS および XLSX ファイル形式でサポートされている行と列の最大数を調べる方法を学習しました。これらの制限を理解することは、データセットが形式の機能と一致するようにして Excel データを効果的に管理するために不可欠です。

## よくある質問

### XLS 形式でサポートされる行の最大数はいくつですか?
XLS 形式でサポートされる行の最大数は 65,536 です。

### XLS 形式でサポートされる列の最大数はいくつですか?
XLS 形式でサポートされる列の最大数は 256 です。

### XLSX 形式でサポートされる行の最大数はいくつですか?
XLSX 形式でサポートされる行の最大数は 1,048,576 です。

### XLSX 形式でサポートされる列の最大数はいくつですか?
XLSX 形式でサポートされる列の最大数は 16,384 です。

### Aspose.Cells for .NET ライブラリを他の Excel ファイル形式で使用できますか?
はい、Aspose.Cells for .NETはXLS、XLSX、ODSなど、さまざまなファイル形式をサポートしています。[ドキュメント](https://reference.aspose.com/cells/net/)サポートされている機能の詳細については、こちらをご覧ください。