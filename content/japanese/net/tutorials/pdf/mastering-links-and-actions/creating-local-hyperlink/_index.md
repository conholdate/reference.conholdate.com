---
title: PDF ファイルにローカル ハイパーリンクを作成する
linktitle: PDF ファイルにローカル ハイパーリンクを作成する
second_title: Aspose.PDF for .NET API リファレンス
description: Aspose.PDF for .NET を使用してローカル ハイパーリンクを作成し、PDF ドキュメント内のナビゲーションを改善する方法を説明します。このステップ バイ ステップのチュートリアルでは、プロセス全体を順を追って説明します。
type: docs
weight: 40
url: /ja/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## 導入

このガイドでは、Aspose.PDF for .NET を使用して PDF ファイルにローカル ハイパーリンクを作成する手順を説明します。各手順を明確に説明しているので、PDF の操作に慣れていない場合でも簡単に理解できます。

## 前提条件

コードに進む前に、次のものを用意してください。

1.  Visual Studio: ダウンロードはこちらから[Visual Studio の Web サイト](https://visualstudio.microsoft.com/).
2. Aspose.PDF for .NET: ライブラリを以下からダウンロードしてください。[Aspose ウェブサイト](https://releases.aspose.com/pdf/net/)このライブラリは、PDF 操作のための豊富な機能を提供します。
3. C# の基礎知識: C# プログラミングの知識があると役立ちますが、心配しないでください。コードを 1 行ずつ説明します。
4. .NET Framework: .NET Frameworkがマシンにインストールされていることを確認してください。Aspose.PDFの要件を確認してください。[ドキュメント](https://reference.aspose.com/pdf/net/).

これらの前提条件が満たされたら、PDF ドキュメントにローカル ハイパーリンクを作成する方法を学習する準備が整いました。

## 必要なパッケージのインポート

これですべての設定が完了したので、必要なパッケージを C# プロジェクトにインポートします。

### プロジェクトを開く

Visual Studio で既存の .NET プロジェクトを開くか、新しいプロジェクトを作成します。最初から始める場合は、起動画面から [新しいプロジェクトの作成] を選択します。

### Aspose.PDF への参照を追加する

ソリューションエクスプローラーのプロジェクトフォルダの「依存関係」を右クリックします。「NuGetパッケージの管理」を選択し、`Aspose.PDF`、最新バージョンをインストールしてください。これにより、PDF の作成と操作に必要なすべてのツールが利用できるようになります。

### 名前空間のインポート

.cs ファイルの先頭に、次の using ディレクティブを追加します。

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

これらのディレクティブを使用すると、ライブラリの機能にシームレスにアクセスできます。

ローカル ハイパーリンクを作成するプロセスを簡単な手順に分解してみましょう。

## ステップ1: ドキュメントインスタンスの設定

新しいインスタンスを作成する`Document`作業する PDF ファイルを表すクラスです。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; //ドキュメントディレクトリを設定する
Document doc = new Document(); //ドキュメントインスタンスを作成する
```

交換する`"YOUR_DOCUMENT_DIRECTORY"`PDF が保存されるシステム上の実際のパスを入力します。

## ステップ2: ドキュメントにページを追加する

次に、PDF ドキュメントにページを追加します。

```csharp
Page page = doc.Pages.Add(); //新しいページを追加
```

この行はドキュメントに新しいページを追加し、そこにすべてのコンテンツが配置されます。

## ステップ3: テキストフラグメントを作成する

次に、クリック可能なリンクとして機能するテキストを作成しましょう。

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); //テキストフラグメントを作成する
```

これ`TextFragment`ユーザーがクリックできるテキストが表示されます。

## ステップ4: ローカルハイパーリンクを作成する

次に、ページ 7 を指すローカル ハイパーリンクを作成します。

```csharp
LocalHyperlink link = new LocalHyperlink(); //ローカルハイパーリンクを作成する
link.TargetPageNumber = 7; //リンクのターゲットページを設定する
text.Hyperlink = link; //テキストフラグメントのハイパーリンクを設定する
```

の`LocalHyperlink`クラスを使用すると、ハイパーリンクのターゲット ページ番号を指定できます。

## ステップ5: ページにテキストフラグメントを追加する

作成したページにクリック可能なテキストを追加します。

```csharp
page.Paragraphs.Add(text); //ページにテキストフラグメントを追加する
```

この行は、ページの段落のコレクションにテキストを追加します。

## ステップ 6: 別のテキスト フラグメントを作成する (オプション)

ページ 1 に戻るためのハイパーリンクをもう 1 つ追加しましょう。

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); //新しいテキストフラグメントを作成する
textBack.IsInNewPage = true; //新しいページにあることを示す
```

## ステップ 7: 2 番目のローカル ハイパーリンクを設定する

ページ 1 に別のローカル ハイパーリンクを作成します。

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); //別のローカルハイパーリンクを作成する
linkBack.TargetPageNumber = 1; //2番目のハイパーリンクのターゲットページを設定する
textBack.Hyperlink = linkBack; //2番目のテキストフラグメントのハイパーリンクを設定する
```

## ステップ8: 新しいページに2番目のテキストフラグメントを追加する

番目のテキスト フラグメントをそのページに追加します。

```csharp
Page newPage = doc.Pages.Add(); // 2番目のリンクに新しいページを追加する
newPage.Paragraphs.Add(textBack); //新しいページにテキストフラグメントを追加する
```

## ステップ9: ドキュメントを保存する

最後に、ドキュメントを保存します。

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; //出力ファイル名を指定
doc.Save(dataDir); //更新されたドキュメントを保存する
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

この行はディレクトリパスとファイル名を結合し、`Save()`メソッドはドキュメントを保存します。

## 結論

Aspose.PDF for .NET を使用して PDF ファイルにローカル ハイパーリンクを作成すると、ナビゲーションとユーザー エクスペリエンスが強化される実用的な機能が得られます。これで、読者を必要な情報に直接誘導する知識が得られ、PDF がよりインタラクティブでユーザー フレンドリになります。

## よくある質問

### Aspose.PDF for .NET とは何ですか?
Aspose.PDF for .NET は、開発者が .NET フレームワークを使用してプログラムで PDF ドキュメントを作成、操作、変換できるようにするライブラリです。

### 外部 Web ページへのハイパーリンクを作成できますか?
はい、Aspose.PDF は、PDF 内のローカル ハイパーリンクに加えて、外部 URL へのハイパーリンクの作成もサポートしています。

### Aspose.PDF の無料試用版はありますか?
もちろんです！無料トライアルは[Aspose ウェブサイト](https://releases.aspose.com/).

### Aspose はどのようなプログラミング言語をサポートしていますか?
AsposeはJava、Cなどさまざまなプログラミング言語用のライブラリを提供しています。++、Python などがあります。

### Aspose 製品のサポートを受けるにはどうすればよいですか?
サポートを受けるには、[Aspose フォーラム](https://forum.aspose.com/c/pdf/10).