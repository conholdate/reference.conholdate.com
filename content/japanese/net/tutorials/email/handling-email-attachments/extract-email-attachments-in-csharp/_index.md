---
title: C# でメール添付ファイルを抽出する - Aspose.Email チュートリアル
linktitle: C# でメール添付ファイルを抽出する - Aspose.Email チュートリアル
second_title: Aspose.Email .NET メール処理 API
description: Aspose.Email for .NET を使用して C# で電子メールの添付ファイルを抽出する方法を学びます。PDF、画像などの例を含むステップバイステップ ガイド。
type: docs
weight: 14
url: /ja/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## 導入

メールの添付ファイルを 1 つずつ手動でダウンロードしたことがありますか? 時間がかかるだけでなく、エラーも発生しやすくなります。幸いなことに、Aspose.Email for .NET は、このタスクを自動化する強力で効率的な方法を提供します。PDF、画像、またはその他のファイル タイプを扱う場合でも、C# を使用して添付ファイルを簡単に抽出できます。

このガイドでは、前提条件から完全に機能する例まで、完全なチュートリアルを順を追って説明します。何時間もの手作業を節約する準備はできていますか? さあ、始めましょう!

## 前提条件

コーディングを開始する前に、次のものを用意してください。

- マシンに Visual Studio がインストールされています。
-  Aspose.Email for .NETライブラリ。[ここからダウンロード](https://releases.aspose.com/email/net/)または NuGet 経由でインストールします。
- 有効な電子メール アカウント (IMAP/POP3 をサポート)。
- C# プログラミングの基本的な理解。

 Aspose.Emailを初めてご利用になる場合は、[無料トライアル](https://releases.aspose.com/)または[一時ライセンス](https://purchase.aspose.com/temporary-license/)全機能のロックを解除します。

## パッケージのインポート

コードに進む前に、必要な名前空間がインポートされていることを確認してください。C# ファイルの先頭に次のコードを追加します。

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

プロセスをわかりやすいステップに分割しましょう。各ステップを注意深く実行して、スムーズに実行できるようにします。


## ステップ1: IMAPクライアントを設定する

最初のステップは、IMAP プロトコルを使用して電子メール サーバーに接続することです。IMAP を使用すると、サーバーから電子メール メッセージにアクセスして取得できます。

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

- 交換する`imap.example.com`メールプロバイダーのIMAPサーバーアドレス（例：`imap.gmail.com` Gmail の場合）。
- 実際のメールアドレスを使用する`username`そして`password`.
- `SelectFolder(ImapFolderInfo.InBox)`受信トレイを操作することを指定します。


## ステップ2: 受信トレイからメールを取得する

接続したら、受信トレイから電子メール メッセージを取得する必要があります。Aspose.Email は、すべてのメッセージを一覧表示する簡単な方法を提供します。

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()`受信トレイ内のすべてのメールのメタデータを取得します。
- の`ImapMessageInfoCollection`オブジェクトには、送信者、件名、一意の ID などの詳細が含まれます。


## ステップ3: 各メールメッセージを取得する

コンテンツと添付ファイルにアクセスするには、一意の ID を使用して各メールを取得する必要があります。


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

- の`foreach`ループはすべてのメッセージを反復処理します。
- `FetchMessage()`指定されたメッセージ ID の実際の電子メール コンテンツを取得します。


## ステップ4: 添付ファイルをループする

メールの内容がわかったら、次は添付ファイルを抽出します。`MailMessage`オブジェクトには添付ファイルのコレクションが含まれています。

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

- の`Attachments`プロパティは電子メール内のすべての添付ファイルをリストします。
- 使用`attachment.Name`ファイル名を取得します。


## ステップ5: 添付ファイルをディスクに保存する

最後に、添付ファイルをローカル マシンに保存します。ファイルは、種類、サイズ、その他の基準でフィルターできます。

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

- 交換する`"C:\\Attachments"`希望するフォルダパスを入力します。
- の`attachment.Save()`メソッドはファイルをディスクに書き込みます。


## ステップ6: 添付ファイルを種類別に処理する

添付ファイルの種類 (PDF と JPEG など) に応じて異なる方法で処理する必要がある場合、Aspose.Email を使用すると簡単に処理できます。

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType`ファイルの種類を識別します（例：`application/pdf` PDFの場合、`image/jpeg`画像の場合）。
- 必要に応じて、さまざまなファイル タイプにカスタム ロジックを追加します。


## 結論

これで完了です。電子メールから添付ファイルを抽出するのは、もはや面倒な作業ではありません。Aspose.Email for .NET を使用すると、わずか数行のコードでこのプロセスを自動化できます。IMAP クライアントの設定から添付ファイルのローカル保存まで、このガイドでは開始するために必要なすべての手順を説明しています。 

では、なぜ待つ必要があるのでしょうか?[Aspose.Email をダウンロード](https://releases.aspose.com/email/net/)今すぐメールワークフローの効率化を始めましょう。


## よくある質問

### このコードは Gmail または Outlook で使用できますか?
はい！交換`imap.example.com`Gmailの（`imap.gmail.com`) または Outlook の (`outlook.office365.com`) IMAP サーバーのアドレス。

### Aspose.Email は無料で使用できますか?
 Aspose.Emailの全機能を利用するにはライセンスが必要です。[無料トライアル](https://releases.aspose.com/)または[一時ライセンス](https://purchase.aspose.com/temporary-license/).

### パスワードのセキュリティをどのように管理すればよいですか?
パスワードをハードコーディングする代わりに、環境変数または安全な資格情報ストレージの使用を検討してください。

### 送信したアイテムから添付ファイルを抽出できますか?
はい、単に使用してください`SelectFolder(ImapFolderInfo.Sent)`受信トレイの代わりに。

### Aspose.Email は POP3 をサポートしていますか?
もちろんです！IMAP に加えて、POP3 と SMTP もサポートしています。