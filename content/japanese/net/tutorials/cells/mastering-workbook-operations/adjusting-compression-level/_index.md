---
title: ワークブックの圧縮レベルの調整
linktitle: ワークブックの圧縮レベルの調整
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET を使用して圧縮レベルを調整し、大きな Excel ファイルを効率的に管理する方法を学びます。このステップ バイ ステップ ガイドでは、ディレクトリの設定から圧縮時間の測定まですべてをカバーし、ファイル サイズの最適化とパフォーマンスの向上に役立ちます。
type: docs
weight: 14
url: /ja/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## 導入

大きな Excel ファイルの管理は、特に保存と転送の効率性に関して難しい場合があります。幸いなことに、ファイル圧縮によりこれらのファイルのサイズを大幅に削減できるため、扱いやすくなります。Aspose.Cells for .NET を使用している場合は、ワークブックの圧縮レベルを簡単に調整できます。このガイドでは、コードの各部分をわかりやすく説明しながら、プロセスを段階的に説明します。

## 前提条件

コードに進む前に、次の前提条件を満たしていることを確認してください。

1. C# の基礎知識: C# プログラミングに精通していると、コード スニペットをよりよく理解できるようになります。
2.  Aspose.Cellsライブラリ: Aspose.Cellsライブラリを以下からダウンロードしてインストールします。[ここ](https://releases.aspose.com/cells/net/).
3. Visual Studio: コードを実行するには、Visual Studio のような開発環境が必要です。
4. .NET Framework: プロジェクトが互換性のあるバージョンの .NET Framework を使用して設定されていることを確認します。

## 必要なパッケージのインポート

まず、C# プロジェクトに必要なパッケージをインポートする必要があります。コード ファイルの先頭に次の行を追加します。

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

これらのパッケージは、Aspose.Cellsライブラリを使用してExcelファイルを操作するために不可欠です。`Aspose.Cells`名前空間にはExcelファイルを操作するために必要なすべてのクラスが含まれていますが、`Aspose.Cells.Xlsb` XLSB 形式でファイルを保存するためのオプションを提供します。

## ステップ1: ソースディレクトリと出力ディレクトリを定義する

まず、ソース ファイルが配置されているディレクトリと出力ファイルを保存するディレクトリを設定します。

```csharp
//ソースディレクトリと出力ディレクトリを定義する
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

必ず交換してください`"Your Document Directory\\"`ディレクトリへの実際のパスを使用します。これにより、プログラムは作業に必要なファイルを確実に見つけることができます。

## ステップ2: ワークブックを読み込む

次に、圧縮するワークブックを読み込みます。

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

ここで、新しいインスタンスを作成します。`Workbook`クラスを作成し、既存の Excel ファイルをロードします。ファイル名がソース ディレクトリ内のファイル名と一致していることを確認します。

## ステップ3: 保存オプションを設定する

次に、ワークブックの保存オプションを設定します。

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

の`XlsbSaveOptions`クラスを使用すると、ワークブックを XLSB 形式で保存するときに、圧縮レベルなどのさまざまなオプションを指定できます。

## ステップ4: レベル1の圧縮時間を測定する

最初の圧縮レベルから始めて、ワークブックの保存にかかる時間を測定します。

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

このスニペットは、圧縮タイプをレベル 1 に設定し、ワークブックを保存し、経過時間を測定します。

## ステップ5: レベル6の圧縮時間を測定する

次に、レベル 6 の圧縮でパフォーマンスをテストします。

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

この手順は前の手順と似ていますが、圧縮レベルが高くなります。

## ステップ6: レベル9の圧縮時間を測定する

最後に、最高の圧縮レベルでパフォーマンスを評価します。

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

この手順では、圧縮レベルをレベル 9 に設定します。このレベルでは、処理に時間がかかる可能性がありますが、ファイル サイズが最も大幅に削減される可能性があります。

## ステップ7: 最終出力

すべての圧縮レベルを完了したら、プロセスが正常に終了したことを示すメッセージを出力します。

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

この単純な行は、プログラムが問題なく実行されたことを確認します。

## 結論

Aspose.Cells for .NET を使用してワークブックの圧縮レベルを調整することは、ファイル サイズとパフォーマンスを大幅に改善できる簡単なプロセスです。このガイドで説明されている手順に従うことで、アプリケーションに効率的に圧縮を実装し、Excel ファイルの管理機能を強化できます。

## よくある質問

### Aspose.Cells とは何ですか?  
Aspose.Cells は、開発者が Microsoft Excel を必要とせずに Excel ファイルを作成、操作、変換できるようにする強力な .NET ライブラリです。

### Aspose.Cells をインストールするにはどうすればよいですか?  
 Aspose.Cellsは以下からダウンロードしてインストールできます。[Aspose ウェブサイト](https://releases.aspose.com/cells/net/).

### どのような圧縮レベルが利用可能ですか?  
Aspose.Cells は、レベル 1 (最低圧縮) からレベル 9 (最高圧縮) までの複数の圧縮レベルをサポートします。

### Aspose.Cells を無料でテストできますか?  
はい！Aspose.Cellsの無料トライアルを入手できます[ここ](https://releases.aspose.com/).

### Aspose.Cells のサポートはどこで見つかりますか?  
ご質問やサポートについては、Aspose サポートフォーラムをご覧ください。[ここ](https://forum.aspose.com/c/cells/9).