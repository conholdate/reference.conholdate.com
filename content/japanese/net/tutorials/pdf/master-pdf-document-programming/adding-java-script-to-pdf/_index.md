---
title: PDF ファイルに Java Script を追加する
linktitle: Java Script PDF ファイルを追加
second_title: Aspose.PDF for .NET API リファレンス
description: このドキュメントでは、Aspose.PDF for .NET を使用して PDF ドキュメントにポップアップ アラートや自動印刷機能などのインタラクティブな要素を追加するための包括的なガイドを提供します。
type: docs
weight: 10
url: /ja/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## 導入
このドキュメントでは、Aspose.PDF for .NET を使用して PDF ドキュメントにポップアップ アラートや自動印刷機能などのインタラクティブな要素を追加するための包括的なガイドを提供します。このライブラリの機能を活用することで、さまざまなユーザーのニーズに応える動的で魅力的な PDF を作成できます。

## 前提条件
続行する前に、Aspose.PDF for .NETの最新バージョンを以下からダウンロードしたことを確認してください。[Aspose リリース](https://リリース/pdf/net/)または、ウェブサイトから無料トライアルを入手してください:[releases.aspose.com](http://releases.aspose.com).

また、C# の基礎知識と、使用している開発環境に精通している必要があります。さらに、開発プロセス中に制限を回避する必要がある場合は、Aspose から一時ライセンスを取得することを検討してください。

## 必要なパッケージのインポート
コードの記述を開始するには、Aspose.PDF ライブラリから必要な名前空間をインポートします。

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## ステップ1: 既存のPDFを読み込む
インタラクティブな要素を追加する既存の PDF ドキュメントを読み込みます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

交換する`"YOUR DOCUMENT DIRECTORY"` PDF ファイルへの実際のパスを入力します。

## ステップ2: ドキュメントレベルでJavaScriptを追加する

ドキュメントを開いたときにトリガーされるスクリプトを適用するには、`JavascriptAction`物体：

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## ステップ3: ページレベルでJavaScriptを追加する

ページの開閉に基づいて特定のアクションをトリガーするには、`JavascriptAction`各ページのオブジェクト:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## ステップ4: PDFドキュメントを保存する

変更した PDF ドキュメントを保存するには、出力ファイルのパスを指定します。

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## 結論
このガイドに従って Aspose.PDF for .NET を利用すると、インタラクティブな要素を使用して PDF を効果的に強化できます。このライブラリは、さまざまなユーザーのニーズに応える動的で魅力的なドキュメントを作成するための包括的なソリューションを提供します。

## よくある質問

### PDF 内の異なるページに複数の JavaScript アクションを追加できますか?
はい、個々のページまたはドキュメント全体に異なる JavaScript アクションを割り当てることができます。

### PDF に追加した後で JavaScript を削除することは可能ですか?
はい、既存のJavaScriptアクションを削除または変更するには、`Actions`ドキュメントまたはページのプロパティ。

### PDF ではどのような JavaScript 関数を使用できますか?
印刷、アラート、フォーム操作など、Adobe Acrobat の JavaScript エンジンでサポートされている任意の JavaScript を使用できます。

### JavaScript はすべての PDF ビューアで動作しますか?
ほとんどの JavaScript アクションは、Adobe Acrobat などのインタラクティブ PDF をサポートする PDF ビューアで動作します。ただし、一部の基本的な PDF リーダーは JavaScript をサポートしていない場合があります。