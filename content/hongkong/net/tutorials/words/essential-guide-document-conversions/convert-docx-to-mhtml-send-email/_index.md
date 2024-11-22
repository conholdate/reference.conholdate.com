---
title: 將 DOCX 轉換為 MHTML 並使用 Aspose.Words for .NET 發送電子郵件
linktitle: 將 DOCX 轉換為 MHTML 並使用 Aspose.Words for .NET 發送電子郵件
second_title: Aspose.Words 文件處理 API
description: 本綜合指南提供了將 DOCX 文件轉換為 MHTML 格式並使用 .NET 中的 Aspose.Words 和 Aspose.Email 庫透過電子郵件發送它們的逐步教學。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## 介紹

在當今的數位環境中，在格式之間轉換文件並透過電子郵件發送它們是一項常見任務。本指南將引導您將 DOCX 檔案轉換為 MHTML 格式，並使用強大的 Aspose.Words 和 Aspose.Email 程式庫（適用於 .NET）透過電子郵件傳送。我們將清楚地分解每個步驟，確保您可以輕鬆遵循。讓我們開始吧！

## 先決條件

在深入了解流程之前，請確保您已進行以下設定：

1.  Aspose.Words for .NET：從以下位置下載並安裝該程式庫[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. Aspose.Email for .NET：從以下位置下載並安裝該程式庫[Aspose 發佈頁面](https://releases.aspose.com/email/net/).
3. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
4. SMTP 伺服器：您需要存取 SMTP 伺服器才能傳送電子郵件。

## 導入必要的命名空間

若要在專案中使用 Aspose.Words 和 Aspose.Email，您必須匯入所需的命名空間。在 C# 檔案頂部新增以下 using 指令：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## 第 1 步：載入 DOCX 文檔

首先載入您想要轉換的 DOCX 文件。使用`Document`Aspose.Words 中的類別來完成此任務。

```csharp
//指定文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 步驟 2：將文件儲存為 MHTML

接下來，將載入的文件轉換為 MHTML 格式。這是使用以下方法完成的`Save`的方法`Document`班級。

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    //將流位置重設為讀取開頭。
    stream.Position = 0;
}
```

## 第 3 步：建立電子郵件訊息

現在，使用 Aspose.Email 從 MHTML 串流建立電子郵件。您將利用`MailMessage`為此目的的類別。

```csharp
//將 MHTML 流載入到 Aspose.Email MIME 電子郵件中。
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 第 4 步：發送電子郵件

最後，使用 SMTP 用戶端傳送電子郵件。使用您的伺服器詳細資訊設定 SMTP 用戶端並使用`Send`發送訊息的方法。

```csharp
//使用 Aspose.Email 設定並傳送訊息。
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## 結論

恭喜！您已成功將 DOCX 文件轉換為 MHTML，並使用 Aspose.Words 和 Aspose.Email for .NET 透過電子郵件傳送。此過程包括載入文件、將其轉換為 MHTML、建立電子郵件並透過 SMTP 用戶端發送。透過這些步驟，您可以在應用程式中無縫地自動轉換文件並透過電子郵件發送。

## 常見問題解答

### 我可以使用此方法轉換其他文件格式嗎？
絕對地！ Aspose.Words 支援多種格式，讓您可以將 DOC、DOCX、RTF 等轉換為 MHTML。

### 如何為電子郵件新增附件？
您可以使用以下命令輕鬆新增附件`Attachments`的財產`MailMessage`班級。

### Aspose.Words 與 .NET Core 相容嗎？
是的，Aspose.Words 與 .NET Core 相容，使其適合在 .NET Core 應用程式中使用。

### 我需要 Aspose.Words 和 Aspose.Email 授權嗎？
是的，兩個庫都需要許可證。您可以從以下機構獲得用於評估目的的臨時許可證[Aspose購買頁面](https://purchase.conholdate.com/temporary-license/).

### 在哪裡可以找到更多文件？
有關詳細文檔，請查看 Aspose.Words[這裡](https://reference.aspose.com/words/net/)和 Aspose.Email[這裡](https://reference.aspose.com/email/net/).