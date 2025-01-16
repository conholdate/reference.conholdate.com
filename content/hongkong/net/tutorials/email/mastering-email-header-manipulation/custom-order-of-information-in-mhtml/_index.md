---
title: 使用 Aspose.Email 在 MHTML 中自訂資訊順序
linktitle: 使用 Aspose.Email 在 MHTML 中自訂資訊順序
second_title: Aspose.Email .NET 電子郵件處理 API
description: 在此逐步教學中，了解如何使用 Aspose.Email for .NET 在 MHTML 中定義自訂資訊順序。
type: docs
weight: 14
url: /zh-hant/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## 介紹

創建豐富的電子郵件格式可以大大增強溝通，尤其是在將電子郵件匯出為 MHTML 等不同文件格式時。 Aspose.Email for .NET 為開發人員提供了一個用於操作電子郵件的強大工具包，其中包括定義匯出至 MHTML 時如何顯示資訊的自訂順序。在本指南中，我們將分解實現這一目標所需的步驟，以便無論您是經驗豐富的開發人員還是剛起步的開發人員，都可以輕鬆遵循。那麼，就讓我們開始吧！

## 先決條件

在開始在 MHTML 中定義資訊的自訂順序之前，您需要檢查以下幾個先決條件：

1. .NET 開發環境：確保您已設定 .NET 開發環境。您可以使用 Visual Studio、Visual Studio Code 或任何其他相容的 IDE。

2.  Aspose.Email 函式庫：您需要安裝 Aspose.Email for .NET 函式庫。您可以從以下位置下載最新版本[Aspose 發佈頁面](https://releases.aspose.com/email/net/).

3. 對 C# 的基本了解：熟悉 C# 程式設計將有助於您更好地理解程式碼。

4. 範例電子郵件文件：您需要一個範例`.eml`文件（例如，`Attachments.eml`）用於測試目的。

一旦滿足了這些先決條件，您就可以按照本教學進行操作了！

## 導入包

要開始使用您的程式碼，您需要從 Aspose.Email 庫匯入必要的命名空間。這對於存取操作電子郵件文件所需的所有類別和方法至關重要。

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

將它們包含在 C# 檔案的頂部。現在您已準備好開始編碼！

現在您已完成所有設置，讓我們將教程分解為可管理的步驟。

## 第 1 步：設定您的資料目錄

首先要做的是建立一個用於儲存電子郵件檔案的目錄。這可以是本機電腦上的任何路徑。

```csharp
string dataDir = "Your Data Directory";
```

代替`"Your Data Directory"`與你的實際路徑`.eml`文件位於。例如，如果您的檔案位於`C:\Emails`，你會寫：

```csharp
string dataDir = @"C:\Emails\";
```

## 第 2 步：載入電子郵件訊息

接下來，您需要加載`.eml`文件到一個`MailMessage`目的。這允許您操縱電子郵件的內容和元資料。

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

確保檔案名稱與指定目錄中的檔案名稱相符。如果您的檔案具有不同的名稱，請相應地更新檔案名稱。

## 步驟 3：設定 MHTML 儲存選項

電子郵件載入完畢後，就可以定義如何將其另存為 MHTML。您可以從預設選項開始。

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

此行初始化 MHTML 儲存選項，為稍後自訂標題做好準備。

## 第 4 步：使用預設順序儲存 MHTML

讓我們使用預設順序將電子郵件另存為 MHTML。這為您提供了定制後進行比較的基準。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

運行此行，並檢查您指定的目錄。現在您應該會看到一個名為的新 MHTML 文件`CustomOrderOfInformationInMHTML_1.mhtml`。打開它可以看到預設情況下資訊是如何顯示的。

## 第 5 步：自訂標題順序

現在來了有趣的部分！您可以指定要在 MHTML 輸出中包含哪些標頭以及依什麼順序。我們將從一些常見的標題開始。

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

透過新增這些標頭，您可以告訴 Aspose 您希望如何顯示電子郵件。

## 第 6 步：使用自訂訂單儲存 MHTML

自訂標頭後，您需要將電子郵件再次儲存為 MHTML，以查看新順序如何影響輸出。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

運行此程式碼，然後打開`CustomOrderOfInformationInMHTML_2.mhtml`。將其與第一個進行比較，以了解資訊如何根據標頭順序變化。

## 第 7 步：清除並新增新的標題訂單

如果您想要完全不同的訂單怎麼辦？您可以透過清除現有標頭設定來重新開始。

```csharp
opt.RenderingHeaders.Clear();
```

現在是時候為標題定義新的順序了。例如，如果您想要確定附件的優先順序並複製收件者：

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## 步驟 8： 使用新的自訂訂單儲存 MHTML

最後，使用新的標頭設定最後一次儲存電子郵件。

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

運行此行後，打開`CustomOrderOfInformationInMHTML_3.mhtml`並檢查它如何根據您的新自訂呈現資訊。

## 結論

這就是使用 Aspose.Email for .NET 在 MHTML 中定義自訂資訊順序的簡單指南。透過執行以下步驟，您可以控制電子郵件以 MHTML 格式表示的方式，確保以適合您需求的方式呈現最重要的資訊。 

## 常見問題解答

### 什麼是 MHTML？
MHTML 代表“MIME HTML”，一種結合了 HTML 和映像等其他資源的網頁存檔格式。

### 我可以免費使用 Aspose.Email 嗎？
是的，Aspose 提供了免費試用版供開發人員探索。你可以找到它[這裡](https://releases.aspose.com/).

### 如果我在使用 Aspose.Email 時遇到問題怎麼辦？
您可以透過以下方式獲得社區的支持[Aspose論壇](https://forum.aspose.com/c/email/12/).

### Aspose.Email 是否可以使用臨時許可證？
是的，您可以申請臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以購買 Aspose.Email？
您可以在此處購買該庫[關聯](https://purchase.aspose.com/buy).