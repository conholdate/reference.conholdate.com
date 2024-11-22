---
title: PDF ドキュメントに JavaScript を追加する
linktitle: PDF ドキュメントに JavaScript を追加する
second_title: Aspose.PDF for .NET API リファレンス
description: この包括的なガイドでは、カスタム動作を追加し、計算や検証を動的に実行し、他のソフトウェア アプリケーションと統合する方法を説明します。
type: docs
weight: 30
url: /ja/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## 導入

この包括的なガイドでは、Aspose.PDF for .NET の世界を詳しく調べ、その潜在能力を最大限に引き出して PDF ドキュメントにカスタム JavaScript 機能を追加します。この強力な機能により、動的な要素を組み込み、ユーザー エクスペリエンスを強化し、ワークフローを合理化できます。

## 前提条件

この手順を実行するには、次のものが必要です。

1. プロジェクトにAspose.PDF for .NETがインストールされていること（ダウンロード先：[Aspose.PDF for .NET ダウンロード ページ](https://releases.aspose.com/pdf/net/）)
2. ライブラリを使用するための有効なライセンス
3. C# IDE またはテキストエディタ

## パッケージのインポート

まず、必要な名前空間をプロジェクトにインポートします。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## ステップ1: 新しいPDFドキュメントを初期化する

新しい PDF ドキュメントを作成し、キャンバスに追加します。

```csharp
Document doc = new Document();
doc.Pages.Add();
```

ここから、JavaScript を多用した PDF の構築を開始します。

## ステップ2: PDFにJavaScriptを追加する

JavaScript関数をドキュメントに挿入するには、`doc.JavaScript`コレクション。次に例を示します。

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## ステップ3: JavaScriptを使用してPDFを保存する

更新したドキュメントをディスクに保存します。

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

これで、既存の PDF 内の JavaScript コードにアクセスして変更できるようになりました。

## ステップ4: 既存のPDFにJavaScriptを読み込んで表示する

JavaScriptを含むPDFファイルを読み込み、`Keys`財産：

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## ステップ5: JavaScript関数を表示する

JavaScript キーを反復処理し、対応するコードをコンソールに出力します。

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

これは、現在どの JavaScript 関数が存在するかを確認する方法を示しています。

## ステップ6: PDFからJavaScriptを削除する

名前を使用して目的の JavaScript 関数を見つけて削除します。

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

残りの関数を再印刷して、関数が正常に削除されたことを確認します。

## 結論

この包括的なガイドでは、Aspose.PDF for .NET のカスタマイズ可能な JavaScript 機能のパワーを解き放つ方法を学びました。この機能を使用すると、動的な PDF を作成し、ユーザー エクスペリエンスを強化し、ワークフローを合理化できます。これらの手順を習得し、ライブラリの機能をさらに探索することで、アプリケーションの新しい可能性を解き放つ準備が整います。

## よくある質問

### 1 つの PDF に複数の JavaScript 関数を追加できますか?
はい！JavaScript関数を必要なだけ追加できます。`doc.JavaScript`コレクション。

### 存在しない JavaScript 関数を削除しようとするとどうなりますか?
関数が存在しない場合は、`Remove`メソッドはエラーをスローしませんが、何も削除しません。存在しない関数を処理するには、追加のエラー処理を追加するか、コードを変更してそれらを無視することができます。

### PDF を開いたらすぐに JavaScript を実行することは可能ですか?
はい。ドキュメントを開いたり、ボタンをクリックしたりするなど、特定のトリガーで JavaScript が実行されるように構成できます。

### PDF に追加した後で JavaScript を編集できますか?
はい、既存の PDF を読み込み、その JavaScript にアクセスし、コードを変更して、ドキュメントを再度保存することができます。

### JavaScript を削除すると、PDF コンテンツの残りの部分に影響しますか?
いいえ、JavaScript を削除してもスクリプトにのみ影響します。PDF の内容は変更されません。