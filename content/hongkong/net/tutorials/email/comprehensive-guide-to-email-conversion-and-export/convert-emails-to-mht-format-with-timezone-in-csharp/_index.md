---
title: 在 C# 中將電子郵件轉換為帶有時區的 MHT 格式
linktitle: 在 C# 中將電子郵件轉換為帶有時區的 MHT 格式
second_title: Aspose.Email .NET 電子郵件處理 API
description: 本詳細指南提供了有關如何將電子郵件訊息轉換為 MHT 格式，同時使用 Aspose.Email for .NET 程式庫準確處理時區資訊的清晰說明。
type: docs
weight: 12
url: /zh-hant/net/tutorials/email/comprehensive-guide-to-email-conversion-and-export/convert-emails-to-mht-format-with-timezone-in-csharp/
---
## 介紹

將電子郵件訊息轉換為各種格式是軟體應用程式中的常見任務，尤其是在時間和時區資料至關重要的情況下。本指南將引導您完成將電子郵件轉換為 MHT 格式的流程，同時確保準確保留時區資訊。

## 設定您的開發環境

首先，請確保您擁有合適的開發環境：

1. 安裝 Visual Studio：確保您的電腦上安裝了相容版本的 Visual Studio。
2. 建立新的 C# 專案：啟動 Visual Studio 並為電子郵件轉換應用程式建立新的 C# 專案。

## 安裝 Aspose.Email for .NET

Aspose.Email for .NET 是一個功能強大的函式庫，可以簡化電子郵件處理任務。請依照以下步驟進行安裝：

1. 在 Visual Studio 中開啟您的專案。
2. 導覽至工具 > NuGet 套件管理器 > 管理解決方案的 NuGet 套件。
3. 搜尋 Aspose.Email 並安裝該套件。
```csharp
//加入必要的 using 語句
using Aspose.Email;
```
## 載入和解析電子郵件訊息

接下來，您需要載入並解析您想要轉換的電子郵件。使用以下程式碼片段：

```csharp
//載入電子郵件訊息
var message = MailMessage.Load("path/to/your/email.eml");

//訪問訊息屬性
var subject = message.Subject;
var sender = message.From.Address;
//....根據需求提供其他屬性
```

## 處理時區資訊

準確管理時區資訊至關重要。以下程式碼片段示範如何從電子郵件中提取和處理時區資料：

```csharp
var timezone = message.TimezoneOffset;
var timezoneId = Timezone.GetIdFromOffset(timezone);
var timezoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timezoneId);
//現在您可以使用 timezoneInfo 來處理時區轉換
```

## 將電子郵件轉換為 MHT 格式

現在，讓我們使用 Aspose.Email 執行到 MHT 格式的核心轉換：

```csharp
//設定 MHT 儲存選項
var mhtOptions = MhtSaveOptions.DefaultMhtml;

//為 MHT 輸出建立記憶體流
using var mhtStream = new MemoryStream();
message.Save(mhtStream, mhtOptions);
```

## 儲存 MHT 文件

將電子郵件訊息轉換為 MHT 格式後，是時候將其另存為文件了：

```csharp
//將 MHT 流儲存到文件
using var fileStream = new FileStream("output.mht", FileMode.Create);
mhtStream.Seek(0, SeekOrigin.Begin);
mhtStream.CopyTo(fileStream);
```

## 結論

在本指南中，您了解如何使用 Aspose.Email for .NET 將電子郵件轉換為 MHT 格式，同時有效處理時區資訊。透過執行這些步驟並探索其他自訂選項，您可以將電子郵件轉換功能無縫整合到您的應用程式中。

## 常見問題解答

### 電子郵件轉換期間如何處理附件？

若要管理附件，請使用`Attachments`的財產`MailMessage`班級。在轉換過程中迭代附件並根據需要儲存它們。

### 我可以使用 Aspose.Email for .NET 將電子郵件轉換為其他格式嗎？

絕對地！ Aspose.Email for .NET 支援各種格式，包括 MSG、EML、PST 等。您可以調整提供的程式碼範例以適合您所需的輸出格式。

### 時區資訊是否以 MHT 格式儲存？

是的，在轉換過程中會保留時區資訊。透過處理時區偏移並使用適當的`TimeZoneInfo`方法，您可以確保 MHT 檔案中準確的時區表示。

### 在哪裡可以找到有關 Aspose.Email for .NET 的更多文件和更新？

有關全面資訊和更新，請參閱文件：[Aspose.Email for .NET API 參考](https://reference.aspose.com/email/net/)

### 如何下載最新版本的 Aspose.Email for .NET？

您可以從發布頁面下載最新版本：[下載 .NET 版 Aspose.Email](https://releases.aspose.com/email/net/)