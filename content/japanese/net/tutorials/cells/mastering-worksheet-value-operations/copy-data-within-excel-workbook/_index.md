---
title: Aspose.Cells for .NET を使用して Excel ブック内のデータをコピーする
linktitle: Aspose.Cells for .NET を使用して Excel ブック内のデータをコピーする
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET を使用して、Excel ブック内のデータを効率的にコピーする方法を学びます。このステップ バイ ステップ ガイドに従って、シートを簡単に複製し、データを転送し、Excel ファイルを簡単に管理します。
type: docs
weight: 12
url: /ja/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## 導入

この詳細なガイドでは、Aspose.Cells for .NET を使用して同じブック内でデータをコピーする方法を説明します。以下に概説するステップバイステップの指示に従うことで、シートの内容と書式を保持しながら、プログラムでシートを複製する方法を学習できます。

## Aspose.Cells を使用して Excel でデータをコピーするための前提条件

コーディング プロセスに進む前に、すべてが整っていることを確認しましょう。

1. Aspose.Cells for .NET ライブラリ: Aspose.Cells for .NET ライブラリがインストールされている必要があります。最新バージョンは、[Aspose.Cells for .NET のダウンロード ページ](https://releases.aspose.com/cells/net/).
2. 開発環境: コードを記述して実行するには、Visual Studio などの .NET 互換 IDE が必要です。
3.  Aspose ライセンス: 無料トライアルまたは購入ライセンスのいずれかを使用できます。詳細については、[ここ](https://purchase.aspose.com/temporary-license/).

前提条件が設定されると、ライブラリの使用を開始する準備が整います。

## 必要なパッケージのインポート

まず、Aspose.Cells から関連する名前空間をインポートする必要があります。これにより、Aspose.Cells が提供するクラスとメソッドを使用して Excel ファイルを操作できるようになります。

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

これらの名前空間により、`Workbook`クラス（Excelファイルを操作するため）と`WorksheetCollection`(ワークブック内の複数のシートにアクセスするため)。

## ステップ 1: ワークブックのファイル パスを初期化する

コードを整理するには、ワークブックが配置されているファイル パスと、変更したファイルを保存する場所を定義することが重要です。パスを指定する方法は次のとおりです。

```csharp
// Excel ファイルが配置されているディレクトリ パスを定義します。
string dataDir = "Your Directory Path";

//入力ワークブックへの完全なパスを定義します。
string inputPath = dataDir + "book1.xls";
```

交換する`"Your Directory Path"`ワークブックを含むディレクトリへの実際のパスを使用します。これにより、コードの柔軟性が確保され、パスを効率的に管理できるようになります。

## ステップ2: ワークブックを開いてデータにアクセスする

ファイルパスが設定されたら、次のステップはExcelブックを`Workbook`オブジェクト。これにより、その内容にアクセスして操作できるようになります。

```csharp
// Excel ファイルを Workbook オブジェクトに読み込みます。
Workbook wb = new Workbook(inputPath);
```

この行で、正常にロードされました`book1.xls`に`wb`オブジェクトを作成し、そのデータにアクセスできるようにします。

## ステップ3: ワークシートコレクションにアクセスする

ワークブックが読み込まれると、その中のシートにアクセスできるようになります。Aspose.Cellsは、`Worksheets`コレクションでは、ワークブック内の各ワークシートを操作できます。

```csharp
//ワークブックからワークシート コレクションを取得します。
WorksheetCollection sheets = wb.Worksheets;
```

の`sheets`オブジェクトを使用すると、すべてのワークシートにアクセスできるようになります。`book1.xls`、あるシートから別のシートにデータをコピーするなど、さまざまな操作を実行できます。

## ステップ4: あるシートから別のシートにデータをコピーする

同じワークブック内の1つのワークシートから別のワークシートにデータをコピーするには、Aspose.Cellsは、`AddCopy`このメソッドは、指定されたワークシートの複製を作成し、それをブックに追加します。

```csharp
// 「Sheet1」からワークブック内の新しいシートにデータをコピーします。
sheets.AddCopy("Sheet1");
```

この例では、「Sheet1」から新しいシートにデータをコピーしています。`AddCopy`この方法は、数式、書式、値など、シートの内容をすべて保持しながらシート全体を複製します。

## ステップ5: 変更したワークブックを保存する

データをコピーした後、変更したワークブックを新しい名前または場所で保存できます。これは、`Save`方法`Workbook`物体。

```csharp
//変更したブックを新しい名前で保存します。
wb.Save(dataDir + "book1_copy.xls");
```

これにより、コピーされたシートを含むワークブックが次のように保存されます。`book1_copy.xls`指定されたディレクトリに保存されます。ファイル名とパスは必要に応じて変更できます。

## 結論

Aspose.Cells for .NET を使用して Excel ブック内のデータをコピーするのは簡単な作業です。このガイドでは、効率的に行うために必要な手順を説明します。シート全体を複製する場合でも、特定のデータ範囲を複製する場合でも、Aspose.Cells は Excel の自動化をシンプルかつ効果的にする強力で柔軟な API を提供します。

## よくある質問

### 一度に複数のシートをコピーできますか?

Aspose.Cells は、1 回の呼び出しで複数のシートのコピーをサポートしていません。ただし、コピーするシートをループして個別にコピーすることはできます。

### コピーしたシートの名前を変更するにはどうすればよいですか?

シートをコピーした後、次のように名前を変更できます。

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells は .NET Core と互換性がありますか?

はい、Aspose.Cells は .NET Framework 環境と .NET Core 環境の両方と完全に互換性があります。

### Aspose.Cells はコピー中に書式をどのように処理しますか?

の`AddCopy`この方法では、シートをコピーするときにすべてのコンテンツと書式が保持され、コピーされたデータが元のデータと同一になることが保証されます。

### シートを別のワークブックにコピーできますか?

はい、シートを別のブックにコピーするには、`Copy`対象のブックへの参照を持つメソッド。

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```