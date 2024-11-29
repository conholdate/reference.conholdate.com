---
title: Aspose.Words for .NET を使用して DOCX を MHTML に変換し、電子メールを送信する
linktitle: Aspose.Words for .NET を使用して DOCX を MHTML に変換し、電子メールを送信する
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なガイドでは、.NET の Aspose.Words および Aspose.Email ライブラリを使用して DOCX ドキュメントを MHTML 形式に変換し、電子メールで送信する方法について、ステップバイステップのチュートリアルを提供します。
type: docs
weight: 10
url: /ja/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## 導入

今日のデジタル環境では、ドキュメントをフォーマット間で変換して電子メールで送信することは一般的な作業です。このガイドでは、.NET 用の強力な Aspose.Words および Aspose.Email ライブラリを使用して、DOCX ファイルを MHTML フォーマットに変換し、電子メールで送信する手順を説明します。各手順を明確に分解して、簡単に理解できるようにします。さあ、始めましょう!

## 前提条件

プロセスに進む前に、次の設定がされていることを確認してください。

1.  Aspose.Words for .NET: ライブラリをダウンロードしてインストールします。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: このライブラリを以下のサイトからダウンロードしてインストールします。[Aspose リリース ページ](https://releases.aspose.com/email/net/).
3. .NET Framework: マシンに .NET Framework がインストールされていることを確認します。
4. SMTP サーバー: 電子メールを送信するには、SMTP サーバーにアクセスする必要があります。

## 必要な名前空間のインポート

プロジェクトで Aspose.Words と Aspose.Email を利用するには、必要な名前空間をインポートする必要があります。C# ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## ステップ1: DOCXドキュメントを読み込む

まず、変換したいDOCX文書を読み込みます。`Document`これを実現するには、Aspose.Words のクラスを使用します。

```csharp
//ドキュメント ディレクトリへのパスを指定します。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## ステップ2: ドキュメントをMHTMLとして保存する

次に、読み込んだドキュメントをMHTML形式に変換します。これは、`Save`方法の`Document`クラス。

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    //読み取りのためにストリームの位置を先頭にリセットします。
    stream.Position = 0;
}
```

## ステップ3: 電子メールメッセージを作成する

次に、Aspose.Emailを使用してMHTMLストリームから電子メールメッセージを作成します。`MailMessage`この目的のためのクラスです。

```csharp
// MHTML ストリームを Aspose.Email MIME 電子メール メッセージに読み込みます。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## ステップ4: メールを送信する

最後に、SMTPクライアントを使用してメールを送信します。SMTPクライアントにサーバーの詳細を設定し、`Send`メッセージを送信する方法。

```csharp
// Aspose.Email を使用してメッセージを構成して送信します。
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## 結論

おめでとうございます! Aspose.Words と Aspose.Email for .NET を使用して、DOCX ドキュメントを MHTML に変換し、電子メールで送信できました。このプロセスには、ドキュメントの読み込み、MHTML への変換、電子メール メッセージの作成、SMTP クライアントを介した送信が含まれます。これらの手順により、アプリケーションでドキュメントの変換と電子メール送信をシームレスに自動化できます。

## よくある質問

### この方法を使用して他のドキュメント形式を変換できますか?
もちろんです! Aspose.Words は幅広い形式をサポートしており、DOC、DOCX、RTF などを MHTML に変換できます。

### メールに添付ファイルを追加するにはどうすればよいですか?
添付ファイルは、`Attachments`の財産`MailMessage`クラス。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Words は .NET Core と互換性があるため、.NET Core アプリケーションでの使用に適しています。

### Aspose.Words と Aspose.Email のライセンスは必要ですか?
はい、どちらのライブラリもライセンスが必要です。評価目的で一時的なライセンスを取得するには、[Aspose 購入ページ](https://purchase.conholdate.com/temporary-license/).

### さらに詳しいドキュメントはどこで見つかりますか?
詳細なドキュメントについては、Aspose.Wordsをご覧ください。[ここ](https://reference.aspose.com/words/net/)および Aspose.Email[ここ](https://reference.aspose.com/email/net/).