---
title: Aspose.Cells を使用して Excel ワークブック間でワークシートをコピーする
linktitle: Aspose.Cells を使用して Excel ワークブック間でワークシートをコピーする
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells を使用して、.NET アプリケーション内の Excel ブック間でデータをシームレスに転送する方法を学びます。この包括的なチュートリアルでは、ワークシートのコピーの各手順について説明します。
type: docs
weight: 13
url: /ja/net/tutorials/cells/mastering-worksheet-value-operations/copy-worksheet-between-workbooks/
---
## 導入

Excel ブック間でデータを転送することは、.NET アプリケーションでは一般的なタスクであり、特にレポートの生成やテンプレートの管理でよく行われます。幸い、Aspose.Cells for .NET を使用すると、このプロセスが簡単かつ効率的になります。このチュートリアルでは、ワークシートを 1 つのワークブックから別のワークブックにコピーする手順を説明し、データ管理を強力に制御できるようにします。

## 前提条件

始める前に、次のツールがあることを確認してください。

1.  Aspose.Cells for .NET ライブラリ: ライブラリをダウンロードする[ここ](https://releases.aspose.com/cells/net/).
2. Visual Studio または同様の IDE: これを使用して .NET コードを記述および実行します。
3.  Asposeライセンス: 評価制限を回避するには、[無料トライアルを申し込む](https://releases.aspose.com/)または取得する[一時ライセンス](https://purchase.aspose.com/temporary-license/).

## パッケージのインポート

まず、必要な名前空間をプロジェクトにインポートします。

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

これらの名前空間を使用すると、Excel ブックとワークシートを効果的に操作するために必要なクラスにアクセスできるようになります。

## ステップ1: ディレクトリパスを設定する

まず、Excel ブックを保存するディレクトリを定義します。これにより、後でファイルへのアクセスが簡単になります。

```csharp
//ドキュメント ディレクトリへのパスを設定します。
string dataDir = "Your Document Directory";
```
交換する`"Your Document Directory"`実際のパスを使用します。

## ステップ2: 最初のワークブックを作成する

新しいワークブックを作成し、そこにワークシートを追加してみましょう。

```csharp
//新しいワークブックを作成します。
Workbook excelWorkbook0 = new Workbook();
//ワークブックの最初のワークシートにアクセスします。
Worksheet ws0 = excelWorkbook0.Worksheets[0];
```

## ステップ3: ヘッダーデータを追加する

データセットを明確に表すために、ワークシートにヘッダー行を入力します。

```csharp
//ヘッダー行 (A1:A4) を入力します。
for (int i = 0; i < 5; i++)
{
    ws0.Cells[i, 0].PutValue($"Header Row {i}");
}
```

## ステップ4: 詳細データ行を入力する

ワークシートのコンテキストを提供するために詳細なコンテンツを追加します。

```csharp
//詳細行 (A5:A999) を入力します。
for (int i = 5; i < 1000; i++)
{
    ws0.Cells[i, 0].PutValue($"Detail Row {i}");
}
```

## ステップ5: 印刷設定を構成する

ページ構成を設定して、印刷されたページでヘッダー行を繰り返すようにします。これは、大きなレポートの場合に特に便利です。

```csharp
//各ページでヘッダー行を繰り返すようにページ設定を構成します。
PageSetup pageSetup = ws0.PageSetup;
pageSetup.PrintTitleRows = "$1:$5";
```

## ステップ6: 2番目のワークブックを作成する

次に、コピーしたワークシートを受け取る 2 番目のワークブックを作成します。

```csharp
//別のワークブックを作成します。
Workbook excelWorkbook1 = new Workbook();
//ワークブックの最初のワークシートにアクセスします。
Worksheet ws1 = excelWorkbook1.Worksheets[0];
```

## ステップ7: 宛先ワークシートの名前を変更する

簡単に識別できるように、2 番目のワークブックのワークシートの名前を変更します。

```csharp
//ワークシートの名前を変更します。
ws1.Name = "MySheet";
```

## ステップ8: データを宛先ワークシートにコピーする

活用する`Copy`最初のワークブックから 2 番目のワークブックにワークシート全体を転送する方法。

```csharp
//最初のワークブックの最初のワークシートから 2 番目のワークブックの最初のワークシートにデータをコピーします。
ws1.Copy(ws0);
```

## ステップ9: 最終的なワークブックを保存する

最後に、変更したブックを保存します。

```csharp
// 2 番目のワークブックを保存します。
excelWorkbook1.Save(dataDir + "CopyWorksheetFromWorkbookToOther_out.xls");
```

## 結論

これで完了です。Aspose.Cells for .NET を使用すると、ワークシートを 1 つのワークブックから別のワークブックに簡単にコピーできます。この方法は、大規模なデータセット、テンプレートの作成、レポートの生成に最適です。 

## よくある質問

### 複数のワークシートを一度にコピーできますか?  
はい、複数のワークシートを反復処理し、個別に別のワークブックにコピーすることができます。

### Aspose.Cells はコピー中に書式を保持しますか?  
絶対に！`Copy`このメソッドはすべての書式とスタイルを保持します。

### コピーしたワークシート内の特定のセルにアクセスするにはどうすればよいですか?  
特定のセルにアクセスするには、`Cells`ワークシート内のプロパティ。

### 書式設定せずに値のみをコピーしたい場合はどうすればよいでしょうか?  
必要に応じて、セルごとに値をコピーするカスタム メソッドを実装できます。

### ライセンスなしでこの機能をテストできますか?  
はい、Asposeは[無料トライアル](https://releases.aspose.com/)その特徴を探ります。