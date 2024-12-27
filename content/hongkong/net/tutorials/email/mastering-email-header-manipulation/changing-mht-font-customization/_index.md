---
title: 使用 C# 變更 MHT 字型自訂
linktitle: 使用 C# 變更 MHT 字型自訂
second_title: Aspose.Email .NET 電子郵件處理 API
description: 了解如何使用 Aspose.Email for .NET 在 MHT 轉換期間變更字體。請按照此逐步指南輕鬆進行自訂。
type: docs
weight: 11
url: /zh-hant/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## 介紹

在 Web 通訊領域，MHT (MHTML) 檔案是儲存和分享包含圖像、連結和樣式的 Web 內容的便捷方式。但是，當您需要透過更改字體來美化這些 MHT 檔案時會發生什麼？感謝 Aspose.Email for .NET，這項任務變得輕而易舉。在本教程中，我們將逐步引導您完成 MHT 轉換期間更改字體的過程。無論您是在開發處理電子郵件格式的應用程序，還是只想為您的業務自訂文檔，本指南都將為您提供所需的知識。

## 先決條件

在深入研究程式碼之前，您應該準備一些要點：

1. Visual Studio：您需要一個整合開發環境 (IDE) 來處理您的 C# 專案。
2.  Aspose.Email for .NET Library：確保您已安裝該程式庫。您可以從[關聯](https://releases.aspose.com/email/net/).
3. .NET Framework：您的專案應與.NET Framework相容；通常，.NET Core 或更高版本運作良好。

這些都排好了嗎？驚人的！讓我們開始吧。

## 導入包

首先，請確保您的專案設定為使用必要的命名空間。您需要在 C# 檔案的頂部包含以下內容：

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

這些軟體包將使您能夠存取使用 MHT 檔案並修改其內容所需的功能。

現在，讓我們分解一下 MHT 轉換期間更改字體所涉及的步驟。

## 第 1 步：載入 MHT 文件

您需要做的第一件事是將 MHT 檔案載入到`MailMessage`目的。您可以在此處存取和操作其內容。

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

說明： 在這裡，`"input.mht"`是 MHT 檔案的路徑。這`MhtmlLoadOptions()`允許您設定檔的載入方式，例如，以不同的方式處理附件或連結資源。

## 第 2 步：迭代替代視圖

MHT 檔案通常有多個備用視圖，特別是當它們包含 HTML 內容時。您需要循環瀏覽這些視圖以找到您想要修改的視圖。

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

說明：您正在檢查每個`AlternateView`查看它是否是 HTML 類型。如果是的話，您可以訪問`LinkedResources`，通常儲存 HTML 中連結的任何字體。

## 第 3 步：識別並自訂字體

現在您可以存取連結的資源，您可以識別哪些資源是字體並根據需要自訂它們。

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  //變更為所需字體
        linkedResource.TransferEncoding = TransferEncoding.Base64;  //確保其編碼正確
    }
}
```

說明：此循環檢查連結資源的內容類型是否為 TrueType 字型。如果匹配，您可以將字體名稱更改為您想要的名稱（例如本例中的“Arial”）。這`TransferEncoding`還應該設定以確保儲存文件時字體資料編碼正確。

## 步驟 4：儲存更新的 MHT 文件

自訂字體後，就可以儲存修改後的 MHT 檔案了。您需要確保使用正確的儲存選項來維護文件的完整性。

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

說明：在這行程式碼中，`"output.mht"`是要儲存更新內容的文件的名稱。使用`SaveOptions.DefaultMhtml`確保新文件保持 MHT 格式。

## 結論

更改 MHT 文件中的字體可以顯著增強文件的外觀。透過利用 Aspose.Email for .NET，您只需幾行程式碼即可輕鬆載入 MHT 檔案、修改其內容並儲存變更。無論您是在處理個人專案還是大型應用程序，掌握這些技能都可以改善您呈現資訊的方式。

## 常見問題解答

### 什麼是 MHT 格式？
MHT 是一種網頁存檔格式，它將 HTML 文件、圖像和其他資源儲存在單一文件中。

### 我可以使用 Aspose 更改 MHT 檔案的其他方面嗎？
絕對地！ Aspose.Email 允許您修改 MHT 檔案的幾乎所有方面，包括附件、標題等。

### Aspose.Email for .NET 是免費的嗎？
 Aspose 提供免費試用版，但完整版需要授權。您可以從以下地點獲得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以找到有關 Aspose.Email 的更多文件？
您可以在以下位置找到全面的文件和範例[Aspose 電子郵件文件頁面](https://reference.aspose.com/email/net/).

### 如果我在使用 Aspose 時遇到問題怎麼辦？
如果您遇到任何問題，可以透過以下方式尋求支持[Aspose 支援論壇](https://forum.aspose.com/c/email/12/).