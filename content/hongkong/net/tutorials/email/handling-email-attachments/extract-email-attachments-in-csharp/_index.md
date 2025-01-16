---
title: 在 C# 中提取電子郵件附件 - Aspose.Email 教程
linktitle: 在 C# 中提取電子郵件附件 - Aspose.Email 教程
second_title: Aspose.Email .NET 電子郵件處理 API
description: 了解如何使用 Aspose.Email for .NET 在 C# 中擷取電子郵件附件。包含 PDF、圖像等範例的逐步指南。
type: docs
weight: 14
url: /zh-hant/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## 介紹

您是否曾經發現自己需要逐一手動下載電子郵件附件？這不僅耗時而且容易出錯。幸運的是，Aspose.Email for .NET 提供了一種強大且有效的方法來自動執行此任務。無論您處理的是 PDF、圖像或任何其他文件類型，您都可以使用 C# 輕鬆提取附件。

在本指南中，我們將引導您完成完整的教程，從先決條件開始到完整的工作範例。準備好節省數小時的手動工作了嗎？讓我們深入了解吧！

## 先決條件

在開始編碼之前，請確保您具備以下條件：

- Visual Studio 安裝在您的電腦上。
-  Aspose.Email for .NET 函式庫。你可以[在這裡下載](https://releases.aspose.com/email/net/)或透過 NuGet 安裝它。
- 有效的電子郵件帳號（支援 IMAP/POP3）。
- 對 C# 程式設計有基本了解。

如果您是 Aspose.Email 新手，請考慮請求[免費試用](https://releases.aspose.com/)或一個[臨時執照](https://purchase.aspose.com/temporary-license/)解鎖全部功能。

## 導入包

在深入研究程式碼之前，請確保您已匯入必要的命名空間。在 C# 檔案頂部新增以下內容：

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

讓我們將這個過程分解為易於理解的步驟。認真執行每一步，確保順利執行。


## 第 1 步：設定您的 IMAP 用戶端

第一步是使用 IMAP 協定連接到您的電子郵件伺服器。 IMAP 允許我們從伺服器存取和檢索電子郵件。

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

- 代替`imap.example.com`與您的電子郵件提供者的 IMAP 伺服器位址（例如，`imap.gmail.com`對於 Gmail）。
- 使用您的實際電子郵件`username`和`password`.
- `SelectFolder(ImapFolderInfo.InBox)`指定我們要使用收件匣。


## 步驟 2： 從收件匣檢索電子郵件

連接後，您需要從收件匣中取得電子郵件。 Aspose.Email 提供了一個簡單的方法來列出所有訊息。

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()`檢索收件匣中所有電子郵件的元資料。
- 這`ImapMessageInfoCollection`物件包含寄件者、主題和唯一 ID 等詳細資訊。


## 步驟 3：取得每封電子郵件

若要存取內容和附件，您需要使用其唯一 ID 來取得每封電子郵件。


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

- 這`foreach`循環遍歷所有訊息。
- `FetchMessage()`檢索給定訊息 ID 的實際電子郵件內容。


## 第 4 步：循環存取附件

現在您已經有了電子郵件內容，是時候提取附件了。每個`MailMessage`物件包含附件的集合。

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

- 這`Attachments`屬性列出了電子郵件中的所有附件。
- 使用`attachment.Name`取得檔案名稱。


## 第 5 步：將附件儲存到磁碟

最後，將附件儲存到本機。您可以按類型、大小或其他條件篩選檔案。

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

- 代替`"C:\\Attachments"`與您想要的資料夾路徑。
- 這`attachment.Save()`方法將檔案寫入磁碟。


## 步驟 6：依類型處理附件

如果您需要根據附件類型（例如 PDF 與 JPEG）以不同方式處理附件，Aspose.Email 可以輕鬆實現。

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

- `ContentType.MediaType`標識文件類型（例如，`application/pdf`對於 PDF，`image/jpeg`對於圖像）。
- 根據需要為不同文件類型新增自訂邏輯。


## 結論

現在你就擁有了！從電子郵件中提取附件不再是一項繁瑣的任務。使用 Aspose.Email for .NET，您只需幾行程式碼即可自動執行此程序。從設定 IMAP 用戶端到在本機儲存附件，本指南涵蓋了入門所需的所有內容。 

那麼，為什麼還要等呢？[下載 Aspose.Email](https://releases.aspose.com/email/net/)今天就開始簡化您的電子郵件工作流程！


## 常見問題解答

### 我可以將此程式碼用於 Gmail 或 Outlook 嗎？
是的！代替`imap.example.com`與 Gmail 的 (`imap.gmail.com`) 或 Outlook 的 (`outlook.office365.com`) IMAP 伺服器位址。

### Aspose.Email 可以免費使用嗎？
 Aspose.Email 需要完整功能的許可證。您可以請求[免費試用](https://releases.aspose.com/)或一個[臨時執照](https://purchase.aspose.com/temporary-license/).

### 如何處理密碼安全問題？
考慮使用環境變數或安全憑證儲存而不是硬編碼密碼。

### 我可以從發送的郵件中提取附件嗎？
是的，只需使用`SelectFolder(ImapFolderInfo.Sent)`而不是收件匣。

### Aspose.Email支援POP3嗎？
絕對地！除了IMAP之外，它還支援POP3和SMTP。