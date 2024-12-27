---
title: Aspose.Email を使用した MHTML の情報のカスタム順序
linktitle: Aspose.Email を使用した MHTML の情報のカスタム順序
second_title: Aspose.Email .NET メール処理 API
description: このステップバイステップのチュートリアルでは、Aspose.Email for .NET を使用して MHTML でカスタム情報の順序を定義する方法を学習します。
type: docs
weight: 14
url: /ja/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## 導入

リッチな電子メール形式を作成すると、特に電子メールを MHTML などのさまざまなファイル形式にエクスポートする場合、コミュニケーションが大幅に強化されます。Aspose.Email for .NET は、電子メールを操作するための強力なツールキットを開発者に提供します。これには、MHTML にエクスポートするときに情報を表示するカスタム順序の定義が含まれます。このガイドでは、これを達成するために必要な手順を詳しく説明します。経験豊富な開発者でも、初心者でも、簡単に理解できます。それでは、早速始めましょう。

## 前提条件

MHTML で情報のカスタム順序を定義する前に、いくつかの前提条件を満たす必要があります。

1. .NET 開発環境: .NET 開発環境が設定されていることを確認してください。Visual Studio、Visual Studio Code、またはその他の互換性のある IDE を使用できます。

2.  Aspose.Emailライブラリ: Aspose.Email for .NETライブラリがインストールされている必要があります。最新バージョンは以下からダウンロードできます。[Aspose リリース ページ](https://releases.aspose.com/email/net/).

3. C# の基本的な理解: C# プログラミングに精通していると、コードをよりよく理解できるようになります。

4. サンプルメールファイル: サンプルが必要です`.eml`ファイル（例えば、`Attachments.eml`) をテスト目的で使用します。

これらの前提条件を満たしたら、チュートリアルに従う準備は完了です。

## パッケージのインポート

コードを開始するには、Aspose.Email ライブラリから必要な名前空間をインポートする必要があります。これは、電子メール ファイルの操作に必要なすべてのクラスとメソッドにアクセスするために不可欠です。

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

これらを C# ファイルの先頭に含めます。これでコーディングを始める準備が整いました。

これですべての設定が完了したので、チュートリアルを管理しやすいステップに分解してみましょう。

## ステップ1: データディレクトリを設定する

最初に行うことは、電子メール ファイルを保存するディレクトリを確立することです。これは、ローカル マシン上の任意のパスにすることができます。

```csharp
string dataDir = "Your Data Directory";
```

交換する`"Your Data Directory"`実際の経路で`.eml`ファイルが配置されている場所。たとえば、ファイルが`C:\Emails`次のように記述します。

```csharp
string dataDir = @"C:\Emails\";
```

## ステップ2: 電子メールメッセージを読み込む

次に、`.eml`ファイルに`MailMessage`オブジェクト。これにより、電子メールのコンテンツとメタデータを操作できます。

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

ファイル名が指定されたディレクトリにあるファイル名と一致していることを確認してください。ファイル名が異なる場合は、それに応じてファイル名を更新してください。

## ステップ3: MHTML保存オプションを設定する

メールが読み込まれたら、それを MHTML として保存する方法を定義します。デフォルトのオプションから始めることができます。

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

この行は、MHTML 保存オプションを初期化し、後でヘッダーをカスタマイズするための準備を行います。

## ステップ4: デフォルトの順序でMHTMLを保存する

デフォルトの順序を使用して、電子メールを MHTML として保存しましょう。これにより、カスタマイズ後に比較するための基準が得られます。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

この行を実行し、指定したディレクトリを確認してください。新しいMHTMLファイルが表示されます。`CustomOrderOfInformationInMHTML_1.mhtml`これを開いて、デフォルトで情報がどのように表示されるかを確認します。

## ステップ5: ヘッダーの順序をカスタマイズする

ここからが楽しい部分です。MHTML 出力に含めるヘッダーとその順序を指定できます。まずは一般的なヘッダーから始めましょう。

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

これらのヘッダーを追加することで、電子メールをどのように表示するかを Aspose に指示します。

## ステップ6: カスタムオーダーでMHTMLを保存する

ヘッダーをカスタマイズした後、新しい順序が出力にどのように影響するかを確認するために、電子メールを MHTML として再度保存する必要があります。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

このコードを実行してから`CustomOrderOfInformationInMHTML_2.mhtml`最初のものと比較して、ヘッダーの順序に基づいて情報がどのように変化したかを確認します。

## ステップ7: ヘッダーの順序をクリアして追加する

まったく別の順序にしたい場合はどうすればよいでしょうか? 既存のヘッダー設定をクリアして、最初からやり直すことができます。

```csharp
opt.RenderingHeaders.Clear();
```

ここで、ヘッダーの新しい順序を定義します。たとえば、添付ファイルを優先し、受信者をコピーする場合は、次のようにします。

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## ステップ8: 新しいカスタムオーダーでMHTMLを保存する

最後に、新しいヘッダー設定でメールをもう一度保存します。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

この行を実行した後、`CustomOrderOfInformationInMHTML_3.mhtml`新しいカスタマイズに基づいて情報がどのように表示されるかを確認します。

## 結論

以上が、Aspose.Email for .NET を使用して MHTML で情報のカスタム順序を定義するためのわかりやすいガイドです。これらの手順に従うことで、メールが MHTML 形式でどのように表現されるかを制御し、最も重要な情報がニーズに合った方法で表示されるようにすることができます。 

## よくある質問

### MHTML とは何ですか?
MHTML は「MIME HTML」の略で、HTML と画像などの他のリソースを組み合わせた Web ページ アーカイブ形式です。

### Aspose.Email を無料で使用できますか?
はい、Asposeは開発者向けに無料試用版を提供しています。[ここ](https://releases.aspose.com/).

### Aspose.Email の使用中に問題が発生した場合はどうすればよいですか?
コミュニティからのサポートは、[Aspose フォーラム](https://forum.aspose.com/c/email/12/).

### Aspose.Email には一時ライセンスがありますか?
はい、一時ライセンスを申請できます[ここ](https://purchase.aspose.com/temporary-license/).

### Aspose.Email はどこで購入できますか?
ライブラリはこちらから購入できます[リンク](https://purchase.aspose.com/buy).