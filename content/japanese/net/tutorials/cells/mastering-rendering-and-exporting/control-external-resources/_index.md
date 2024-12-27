---
title: Aspose.Cells for .NET で外部リソースを制御する
linktitle: Aspose.Cells for .NET で外部リソースを制御する
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET を使用すると、Excel から PDF への変換の可能性を最大限に引き出すことができます。この包括的なガイドでは、画像などの外部リソースを管理して、PDF が正確な書式設定要件を反映するようにする方法を学習します。
type: docs
weight: 12
url: /ja/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## 導入

今日のデジタル環境では、Excel スプレッドシートを PDF ドキュメントに変換することは一般的かつ不可欠なタスクです。レポート、財務データ、プレゼンテーション資料のいずれを準備する場合でも、PDF が意図した形式を反映していることを確認することが重要です。Aspose.Cells for .NET は、特に画像などの外部リソースを処理する場合に、この変換プロセスを詳細に制御できる強力なライブラリを提供します。このガイドでは、Aspose.Cells を使用して Excel から PDF への変換プロセス中に外部リソースを効果的に管理する方法を説明します。さっそく始めましょう。

## 前提条件

始める前に、以下のものを準備しておいてください。

1. Visual Studio または任意の .NET 互換 IDE: これが開発環境になります。
2.  Aspose.Cells for .NET: まだインストールしていない場合は、[Aspose ダウンロード](https://releases.aspose.com/cells/net/)最新バージョンを入手するには、ページをご覧ください。
3. C# の基礎知識: C# に精通していると有利です。概念について明確にする必要がある場合は、遠慮なく調べてください。
4. サンプル Excel ファイル: 変換する外部リソースを含む Excel ファイル (「samplePdfSaveOptions_StreamProvider.xlsx」など) を準備します。
5. テスト用の画像ファイル: 変換中に「newPdfSaveOptions_StreamProvider.png」のような画像ファイルを外部リソースとして使用します。

## 必要なパッケージをインポートする

まず、Aspose.Cells ライブラリから必要な名前空間をインポートする必要があります。C# ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

これらの名前空間は、タスクに不可欠なクラスとメソッドを提供します。

## ステップ1: ストリームプロバイダークラスを作成する

まず、ストリームプロバイダクラスを作成し、`IStreamProvider`インターフェース。このクラスを使用すると、外部リソースの読み込み方法を制御できます。

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        //画像をメモリストリームにロードする
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: このメソッドは、ストリームが閉じられ、現在デバッグ メッセージがログに記録されているときに呼び出されます。
- InitStream: このメソッドは、外部画像ファイルをバイト配列として読み込み、それをメモリストリームに変換し、`options.Stream`財産。

## ステップ2: ソースディレクトリと出力ディレクトリを設定する

次に、Excel ファイルと出力 PDF のディレクトリを定義します。

```csharp
//ソースディレクトリ
string sourceDir = "Your Document Directory";
//出力ディレクトリ
string outputDir = "Your Document Directory";
```

交換する`"Your Document Directory"`ファイルが配置されているシステム上の実際のパスを入力します。

## ステップ3: Excelファイルを読み込む

次に、PDF を作成する Excel ファイルを読み込みます。

```csharp
//外部画像を含むソースExcelファイルを読み込む
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

の`Workbook`Aspose.Cells のクラスは、画像などのさまざまな外部リソースが含まれる可能性がある Excel ファイルを表します。

## ステップ4: PDF保存オプションを設定する

ワークブックを PDF として保存する前に、必要な保存オプションを指定します。

```csharp
// PDF 保存オプションの指定 - ストリーム プロバイダー
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true //各シートを新しいページに保存する
};
```

これにより、`PdfSaveOptions` PDF形式をカスタマイズできます。`OnePagePerSheet`このオプションにより、各 Excel シートが最終的な PDF の別々のページに表示されるようになります。

## ステップ5: ストリームプロバイダーを割り当てる

接続する`Workbook`インスタンス`MyStreamProvider`先ほど作成したクラス。

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

この行により、変換中に外部リソースが検出されるたびに、カスタム プロバイダーがそれに応じて管理するようになります。

## ステップ6: ワークブックをPDFとして保存する

次に、Excel ブックを PDF として保存します。

```csharp
//ワークブックをPDFに保存する
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

電話をかけることで`Save`メソッドをワークブック オブジェクトに適用し、出力ディレクトリと PDF オプションを渡すことで、Excel ファイルを適切にフォーマットされた PDF に変換できます。

## ステップ7: 実行が成功したことを確認する

最後に、プロセスが正常に完了したことを確認することをお勧めします。

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

このメッセージは、操作のステータスを通知し、役立つフィードバックを提供します。

## 結論

これで、Aspose.Cells を使用して Excel から PDF への変換中に外部リソースを制御するプロセスを習得できました。これらの手順に従うことで、ドキュメントに画像やその他の外部要素が正確に含まれていることを保証し、毎回洗練された最終製品を作成できます。

## よくある質問

### Aspose.Cells とは何ですか?
Aspose.Cells は、さまざまな形式の Excel ファイルの作成、操作、変換、レンダリングを可能にする、.NET 開発者向けの強力なライブラリです。

### Aspose.Cells をダウンロードするにはどうすればいいですか?
最新バージョンは以下からダウンロードできます。[ダウンロードリンク](https://releases.aspose.com/cells/net/).

### Aspose.Cells を無料で試すことはできますか?
はい！無料トライアルは、[無料トライアルページ](https://releases.aspose.com/).

### Aspose.Cells のサポートはどこで見つかりますか?
サポート関連のお問い合わせについては、[Aspose サポートフォーラム](https://forum.aspose.com/c/cells/9).

### Aspose.Cells の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスを申請することができます[ここ](https://purchase.aspose.com/temporary-license/).
