---
title: Aspose.Email for .NET を使用して C# で TNEF 添付ファイルを追加する
linktitle: Aspose.Email for .NET を使用して C# で TNEF 添付ファイルを追加する
second_title: Aspose.Email .NET メール処理 API
description: 強力な Aspose.Email for .NET ライブラリを使用して、C# で Transport Neutral Encapsulation Format (TNEF) 添付ファイルを効果的に処理する方法を学びます。このガイドでは、開発環境の設定から読み込みまですべてをカバーしています。
type: docs
weight: 12
url: /ja/net/tutorials/email/handling-email-attachments/add-tnef-attachments-in-csharp/
---
## 導入

TNEF (トランスポート ニュートラル カプセル化形式) は、Microsoft Outlook が電子メール内のリッチ テキストと添付ファイルをカプセル化するために使用する独自の形式です。これらの TNEF 添付ファイルをプログラムで操作する必要がある場合、Aspose.Email for .NET は、TNEF 添付ファイルを含むさまざまな電子メール形式をサポートする優れたライブラリです。このガイドでは、環境の設定、電子メールの読み込み、TNEF 添付ファイルの抽出と変更、変更の保存の方法について説明します。

## 開発環境の設定

コーディングを始める前に、開発環境の準備ができていることを確認してください。次の手順に従います。

1. マシンに Visual Studio をインストールします。
2. 新しい C# プロジェクトを作成します。適切な名前と場所を選択します。

## Aspose.Email for .NET ライブラリの追加

TNEF 添付ファイルを使い始めるには、まず Aspose.Email for .NET ライブラリをプロジェクトに追加する必要があります。これは NuGet パッケージ マネージャーを使用して簡単に行うことができます。

1. Visual Studio で、パッケージ マネージャーを開きます ([ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理])。
2. Aspose.Email を検索し、最新バージョンをインストールします。

## TNEF 添付ファイル付きの既存のメールを読み込む

ライブラリがインストールされたので、TNEF 添付ファイルを含む電子メール メッセージを読み込むことができます。手順は次のとおりです。

```csharp
// TNEF添付ファイル付きのメールを読み込む
MsgLoadOptions options = new MsgLoadOptions
{
    PreserveTnefAttachments = true
};
var message = MailMessage.Load("path/to/email.eml", options);
```

## TNEF 添付ファイルの抽出と変更

電子メールを読み込んだ後、TNEF 添付ファイルにアクセスできます。添付ファイルを反復処理するには、次のコードを使用します。

```csharp
//添付ファイルを反復処理する
foreach (var attachment in message.Attachments)
{
    if (attachment.ContentType.MediaType == "application/ms-tnef")
    {
        //TNEF添付ファイルの抽出
        var tnefAttachment = attachment;

        //TNEFプロパティにアクセスし、必要に応じて変更する
        //例: ファイル名を印刷する
        Console.WriteLine($"Extracted TNEF attachment: {tnefAttachment.Name}");
    }
}
```

TNEFプロパティまたはハンドルを変更するには、次の特定のプロパティを参照してください。`tnefAttachment` 、 のように`tnefAttachment.ContentDisposition`または`tnefAttachment.ContentType`.

## 変更された添付ファイルを含むメールを保存する

TNEF 添付ファイルの変更が完了したら、更新された電子メールを保存できます。手順は次のとおりです。

```csharp
//変更したメールを保存する
EmlSaveOptions emlSaveOptions = new EmlSaveOptions(MailMessageSaveType.EmlFormat)
{
    FileCompatibilityMode = FileCompatibilityMode.PreserveTnefAttachments
};
message.Save("path/to/modified_email.eml", emlSaveOptions);
```

## 結論

このチュートリアルでは、Aspose.Email for .NET を使用して TNEF 添付ファイルを操作するための基本事項について説明しました。電子メールを読み込み、TNEF 添付ファイルを抽出および変更し、変更を効果的に保存する方法を学びました。この機能により、電子メール内のリッチ コンテンツをシームレスに管理できるようになります。

## よくある質問

### Aspose.Email for .NET をインストールするにはどうすればよいですか?

Aspose.Email for .NET は、NuGet パッケージ マネージャーを使用して簡単にインストールできます。「Aspose.Email」を検索し、適切なパッケージを選択してインストールするだけです。

### Aspose.Email for .NET を使用して他の電子メール形式を操作できますか?

もちろんです! Aspose.Email は、EML、MSG、PST など、さまざまな電子メール形式をサポートしており、さまざまな電子メール処理のニーズに柔軟に対応できます。

### Aspose.Email を商用プロジェクトに使用できますか?

はい、適切なライセンスをお持ちであれば、Aspose.Email for .NET は個人プロジェクトと商用プロジェクトの両方に適しています。

### さらに詳しいドキュメントや例はどこで見つかりますか?

詳しいドキュメント、詳細なAPIリファレンス、追加の例については、[Aspose.Email for .NET ドキュメント](https://reference.aspose.com/email/net/).

### さらにサポートが必要ですか?

ご質問がある場合や、プロセスのどの部分についても説明が必要な場合は、お気軽にお問い合わせください。