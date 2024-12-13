---
title: Aspose.Cells でスレッドコメントの作成時間を読み取る
linktitle: Aspose.Cells でスレッドコメントの作成時間を読み取る
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET を使用して、Excel ワークシート内のスレッド化されたコメントの作成時間を簡単に読み取る方法を学びます。ステップバイステップの手順が記載された詳細なガイドに従ってください。
type: docs
weight: 21
url: /ja/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## 導入

Excel ファイルで作業する場合、コメントの管理は共同作業やフィードバックの追跡に不可欠です。このガイドでは、Aspose.Cells for .NET を使用して、Excel ワークシート内のスレッド化されたコメントの作成時刻を読み取るプロセスについて説明します。この強力なツールは、Excel ファイルと対話する効率的な方法を提供し、開発者がコメントから詳細な情報を抽出できるようにします。これは、共同作業のシナリオでフィードバックのタイミングを追跡するのに特に役立ちます。

## 前提条件

始める前に、Aspose.Cells for .NET を使用するために開発環境が適切に設定されていることを確認することが重要です。必要なものは次のとおりです。

1.  Aspose.Cells for .NET: Aspose.Cellsライブラリをインストールする必要があります。最新バージョンは以下から入手できます。[Aspose ウェブサイト](https://releases.aspose.com/cells/net/).
2. IDE: コードを記述して実行するための Visual Studio (または任意の .NET IDE)。
3. 基本的な C# の知識: C# プログラミングに精通していると、例を理解しやすくなります。
4.  Excelファイル: このチュートリアルでは、次のExcelファイルを使用します。`ThreadedCommentsSample.xlsx`、スレッド化されたコメントがいくつか含まれています。ファイルに、フォローするためのコメントが含まれていることを確認してください。

## 必要なパッケージのインポート

まず、Aspose.Cells を操作するために必要な名前空間をインポートする必要があります。C# プロジェクトを開き、コード ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

の`Aspose.Cells`名前空間を使用すると、Excelファイルの操作に必要なすべてのクラスとメソッドにアクセスできます。`System`出力や例外処理などの一般的な機能に必要です。

## ステップ1: Excelファイルのディレクトリを指定する

最初のステップは、Excel ファイルが保存されているパスを定義することです。このパスは、プログラムでファイルを検索するために使用されます。

```csharp
// Excelファイルのディレクトリを定義する
string sourceDir = "Your Document Directory";
```

交換する`"C:\\YourDirectory\\"`実際のファイルへのパスを入力します。これにより、プログラムはファイルの場所を把握できます。`ThreadedCommentsSample.xlsx`.

## ステップ2: ワークブックを読み込む

ディレクトリを設定したら、Excelブックを読み込むことができます。これは、新しい`Workbook`オブジェクトを作成し、そのファイル パスを渡します。

```csharp
// Excelワークブックを読み込む
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

指定されたパスにファイルが見つからない場合は例外がスローされるため、続行する前にファイル パスが正しいことを確認してください。

## ステップ3: 目的のワークシートにアクセスする

ワークブックが読み込まれたら、スレッド化されたコメントを含むワークシートにアクセスする必要があります。この例では、ワークブックの最初のワークシートを取得します。

```csharp
//ワークブックの最初のワークシートにアクセスする
Worksheet worksheet = workbook.Worksheets[0];
```

コメントが別のワークシートにある場合は、それに応じてインデックスを変更します。たとえば、`Worksheets[1]` 2 番目のワークシートの場合も同様です。

## ステップ4: スレッド化されたコメントを取得する

スレッド化されたコメントを取得するには、コメントを含むセルを指定する必要があります。この場合、セルに焦点を当てます。`A1`方法`GetThreadedComments`特定のセルに関連付けられているすべてのコメントを取得するために使用されます。

```csharp
//セル A1 からスレッド化されたコメントを取得する
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

これにより、セル A1 のスレッド化されたコメントのコレクションが返されます。指定されたセルにコメントが存在しない場合、コレクションは空になります。

## ステップ5: コメントを反復処理して作成時間を抽出する

スレッド化されたコメントを取得したら、次のステップはコレクションを反復処理して、各コメントの作成時間などの関連詳細を抽出することです。これは、`ThreadedCommentCollection`.

```csharp
//各スレッドコメントをループして詳細を表示します
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

このコードはコメントの内容、投稿者名、コメントが作成された時間を出力します。`CreatedTime`プロパティは、コメントが最初に作成されたときのタイムスタンプを返します。

## ステップ6: 確認メッセージを表示する

スレッド化されたコメントを正常に読み取り、情報を表示した後は、コードに確認メッセージを含めることをお勧めします。これにより、プロセスが正しく実行されたことを確認できます。

```csharp
//確認メッセージ
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

コードの実行が完了すると、このメッセージがコンソールに出力され、プロセスがエラーなしで実行されたことが確認されます。

## 結論

Aspose.Cells for .NET を使用して、Excel ワークシート内のスレッド化されたコメントの作成時間を簡単に読み取る方法を学習しました。この機能は、共同作業環境でコメントやフィードバックを追跡するのに非常に役立ち、ドキュメント レビュー プロセスに不可欠なタイムスタンプを提供します。このガイドに従うことで、.NET アプリケーションでコメント データを効率的に抽出して活用し、ワークフローを強化してチーム メンバーとのコラボレーションを向上させることができます。

## よくある質問

### Aspose.Cells for .NET とは何ですか?

Aspose.Cells for .NET は、開発者が .NET アプリケーションで Excel ファイルを作成、操作、管理できるようにする包括的なライブラリです。プログラムによって Excel ファイルを読み取り、書き込み、変更するための強力なツールを提供します。

### Aspose.Cells for .NET をダウンロードするにはどうすればいいですか?

 Aspose.Cells for .NETの最新バージョンは、以下からダウンロードできます。[Aspose ウェブサイト](https://releases.aspose.com/cells/net/).

### 無料トライアルはありますか？

はい、AsposeはAspose.Cells for .NETの無料トライアルを提供しています。トライアル版は以下からダウンロードできます。[無料トライアルページ](https://releases.aspose.com/).

### 他のセルからコメントにアクセスできますか?

はい、ワークシート内のどのセルからでも、セル参照を変更することでスレッドコメントにアクセスできます。`GetThreadedComments`方法。変更するだけで`"A1"`目的のセルへの参照。

### Aspose.Cells のサポートはどこで受けられますか?

サポートが必要な場合やご質問がある場合は、[Aspose フォーラム](https://forum.aspose.com/c/cells/9)では、回答を見つけたり、コミュニティから助けを求めたりすることができます。