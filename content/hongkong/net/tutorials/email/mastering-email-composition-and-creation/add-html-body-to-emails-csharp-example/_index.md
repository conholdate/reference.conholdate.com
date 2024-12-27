---
title: 將 HTML 正文新增至電子郵件 - C# 範例
linktitle: 將 HTML 正文新增至電子郵件 - C# 範例
second_title: Aspose.Email .NET 電子郵件處理 API
description: 在本詳細指南中探索 Aspose.Email for .NET 的強大功能。了解如何建立、自訂和傳送包含 HTML 內容和嵌入圖像的專業電子郵件。
type: docs
weight: 18
url: /zh-hant/net/tutorials/email/mastering-email-composition-and-creation/add-html-body-to-emails-csharp-example/
---
## 介紹

Aspose.Email for .NET 是一個強大的程式庫，專為開發人員在其 .NET 應用程式中無縫整合電子郵件功能而設計。無論您是建立電子郵件用戶端、自動化電子郵件任務還是設計自訂電子郵件模板，Aspose.Email 都可以透過其豐富的功能集簡化流程。

## 設定您的開發環境

在我們開始編碼之前，請確保您已將 Aspose.Email for .NET 庫整合到您的專案中。您可以使用 NuGet 套件管理器輕鬆完成此操作：

```bash
Install-Package Aspose.Email
```

## 建立新電子郵件

若要建立新電子郵件，請實例化`MailMessage`班級。此類別可讓您指定各種屬性，例如寄件者、收件者、主題和附件。

```csharp
MailMessage message = new MailMessage
{
    From = new MailAddress("sender@example.com"),
    Subject = "Hello from Aspose.Email!"
};
message.To.Add("recipient@example.com");
```

## 將 HTML 正文新增至電子郵件

接下來，讓我們透過新增 HTML 正文來增強您的電子郵件。使用`HtmlBody`的財產`MailMessage`類別來定義 HTML 內容。

```csharp
string htmlContent = "<html><body><h1>Welcome to our Newsletter!</h1><p>This is a sample HTML email body.</p></body></html>";
message.HtmlBody = htmlContent;
```

## 在 HTML 正文中嵌入圖像

為了讓您的電子郵件具有視覺吸引力，您可以將圖像直接嵌入到 HTML 正文中。這可以使用 base64 編碼的圖像資料或透過連結到圖像 URL 來完成。

### Base64 編碼範例

```csharp
string htmlContentWithImage = "<html><body><h1>Check out our New Product!</h1><img src='data:image/jpeg;base64,/9j...'></body></html>";
message.HtmlBody = htmlContentWithImage;
```

### 帶有圖像 URL 的範例

或者，連結到線上託管的圖像：

```csharp
string htmlContentWithUrlImage = "<html><body><h1>Check out our New Product!</h1><img src='https://example.com/image.jpg'></body></html>";
message.HtmlBody = htmlContentWithUrlImage;
```

## 傳送電子郵件

電子郵件準備好後，就可以發送了。您可以設定 SMTP 設定以使用電子郵件伺服器或第三方服務。

```csharp
using (SmtpClient client = new SmtpClient("smtp.example.com", 587, "username", "password"))
{
    client.Send(message);
}
```

## 處理例外

始終實施異常處理以妥善管理潛在的網路問題或伺服器錯誤。這可確保流暢的使用者體驗並有助於診斷問題。

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

利用 Aspose.Email for .NET，您可以製作具有視覺吸引力和互動式的電子郵件訊息。無論是新聞通訊、促銷活動或交易電子郵件，該庫都可以讓您有效地與受眾建立聯繫。

## 常見問題解答

### 我可以在 Windows 表單和 ASP.NET 應用程式中使用 Aspose.Email for .NET 嗎？
是的，Aspose.Email for .NET 用途廣泛，並且與各種 .NET 應用程式類型相容。

### Aspose.Email for .NET 支援電子郵件附件嗎？
絕對地！您可以使用該程式庫輕鬆地將文件附加到電子郵件中。

### 是否可以使用 Aspose.Email for .NET 非同步傳送電子郵件？
是的，該庫支援非同步方法發送電子郵件，從而提高了某些情況下的效能。

### 我可以自訂 HTML 電子郵件中嵌入圖像的外觀嗎？
當然！您可以使用 HTML 和 CSS 控制嵌入圖片的大小、對齊方式和其他屬性。

### 在哪裡可以找到 Aspose.Email for .NET 的綜合文件？
有關詳細文檔，請造訪 Aspose 參考：[Aspose.Email for .NET 文檔](https://reference.aspose.com/email/net/).