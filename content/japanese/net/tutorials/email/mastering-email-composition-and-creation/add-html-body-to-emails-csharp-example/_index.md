---
title: メールに HTML 本文を追加する - C# の例
linktitle: メールに HTML 本文を追加する - C# の例
second_title: Aspose.Email .NET メール処理 API
description: この詳細なガイドで、Aspose.Email for .NET の強力な機能をご確認ください。HTML コンテンツと埋め込み画像を使用してプロフェッショナルな電子メール メッセージを作成、カスタマイズ、送信する方法を学習します。
type: docs
weight: 18
url: /ja/net/tutorials/email/mastering-email-composition-and-creation/add-html-body-to-emails-csharp-example/
---
## 導入

Aspose.Email for .NET は、開発者が .NET アプリケーション内で電子メール機能をシームレスに統合できるように設計された強力なライブラリです。電子メール クライアントの作成、電子メール タスクの自動化、カスタム電子メール テンプレートの設計など、Aspose.Email は豊富な機能セットでプロセスを簡素化します。

## 開発環境の設定

コーディングを始める前に、Aspose.Email for .NET ライブラリをプロジェクトに統合していることを確認してください。これは NuGet パッケージ マネージャーを使用して簡単に行うことができます。

```bash
Install-Package Aspose.Email
```

## 新しい電子メールメッセージを作成する

新しい電子メールメッセージを作成するには、`MailMessage`クラス。このクラスを使用すると、送信者、受信者、件名、添付ファイルなどのさまざまな属性を指定できます。

```csharp
MailMessage message = new MailMessage
{
    From = new MailAddress("sender@example.com"),
    Subject = "Hello from Aspose.Email!"
};
message.To.Add("recipient@example.com");
```

## メールにHTML本文を追加する

次に、HTML本文を追加してメールを充実させましょう。`HtmlBody`の財産`MailMessage` HTML コンテンツを定義するクラス。

```csharp
string htmlContent = "<html><body><h1>Welcome to our Newsletter!</h1><p>This is a sample HTML email body.</p></body></html>";
message.HtmlBody = htmlContent;
```

## HTML 本文に画像を埋め込む

メールを視覚的に魅力的にするために、HTML 本文に画像を直接埋め込むことができます。これは、base64 でエンコードされた画像データを使用するか、画像 URL にリンクすることで実行できます。

### Base64 エンコードの例

```csharp
string htmlContentWithImage = "<html><body><h1>Check out our New Product!</h1><img src='data:image/jpeg;base64,/9j...'></body></html>";
message.HtmlBody = htmlContentWithImage;
```

### 画像 URL の例

または、オンラインでホストされている画像にリンクします。

```csharp
string htmlContentWithUrlImage = "<html><body><h1>Check out our New Product!</h1><img src='https://example.com/image.jpg'></body></html>";
message.HtmlBody = htmlContentWithUrlImage;
```

## メールの送信

メールの準備ができたら、送信します。メール サーバーまたはサードパーティのサービスを使用するように SMTP 設定を構成できます。

```csharp
using (SmtpClient client = new SmtpClient("smtp.example.com", 587, "username", "password"))
{
    client.Send(message);
}
```

## 例外の処理

潜在的なネットワークの問題やサーバー エラーを適切に管理するために、常に例外処理を実装してください。これにより、スムーズなユーザー エクスペリエンスが確保され、問題の診断に役立ちます。

```csharp
try
{
    client.Send(message);
}
catch (Exception ex)
{
    Console.WriteLine($"An error occurred: {ex.Message}");
}
```

## 結論

Aspose.Email for .NET を使用すると、視覚的に魅力的でインタラクティブな電子メール メッセージを作成できます。ニュースレター、プロモーション キャンペーン、トランザクション メールなど、このライブラリを使用すると、対象ユーザーと効果的につながることができます。

## よくある質問

### Aspose.Email for .NET を Windows フォームと ASP.NET アプリケーションの両方で使用できますか?
はい、Aspose.Email for .NET は汎用性が高く、さまざまな種類の .NET アプリケーションと互換性があります。

### Aspose.Email for .NET は電子メールの添付ファイルをサポートしていますか?
もちろんです! ライブラリを使用すると、電子メール メッセージにファイルを簡単に添付できます。

### Aspose.Email for .NET を使用して電子メールを非同期的に送信することは可能ですか?
はい、ライブラリは電子メールを送信するための非同期メソッドをサポートしており、特定のシナリオでパフォーマンスが向上します。

### HTML メールに埋め込まれた画像の外観をカスタマイズできますか?
もちろんです! HTML と CSS を使用して、埋め込まれた画像のサイズ、配置、その他の属性を制御できます。

### Aspose.Email for .NET の包括的なドキュメントはどこで入手できますか?
詳細なドキュメントについては、Asposeリファレンスをご覧ください。[Aspose.Email for .NET ドキュメント](https://reference.aspose.com/email/net/).