---
title: 建立新的數位簽章行並設定提供者 ID
linktitle: 建立新的數位簽章行並設定提供者 ID
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 以程式設計方式為 Word 文件新增簽名行。此綜合指南涵蓋了從設定開發環境到插入簽名行和安全簽署文件的所有內容。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## 介紹

你好，科技愛好者！您是否曾經想過在 Word 文件中自動新增簽名行？今天，我們將深入探討如何使用 Aspose.Words for .NET 來實現這一目標。本逐步指南將引導您完成建立簽名行和設定提供者 ID，使您的文件處理任務更加有效率和簡化。

## 先決條件

在我們開始之前，讓我們確保您已完成所有設定：

1.  Aspose.Words for .NET：如果您尚未安裝，請下載它[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：使用 Visual Studio 或任何 C# 開發設定。
3. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
4. PFX 憑證：您需要 PFX 憑證來簽署文檔，該憑證可以從受信任的憑證授權單位取得。

## 導入必要的命名空間

首先，將所需的命名空間匯入到您的 C# 專案中：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

現在，讓我們深入了解建立新簽名行和設定提供者 ID 的詳細資訊。

## 第 1 步：建立一個新文檔

首先，我們需要建立一個新的 Word 文檔，它將作為我們簽名行的畫布：

```csharp
//指定文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在這裡，我們初始化一個新的`Document`和一個`DocumentBuilder`，這使我們可以輕鬆添加元素。

## 第 2 步：定義簽章行選項

接下來，我們將定義簽名行的選項，包括簽署者的姓名、職位、電子郵件和其他相關詳細資訊：

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

這些選項有助於個性化簽名行，使其清晰專業。

## 第 3 步：插入簽名行

準備好選項後，我們現在可以將簽名行插入文件中：

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

這`InsertSignatureLine`方法新增簽名行，並且我們為其分配唯一的提供者 ID。

## 步驟 4：儲存文檔

插入簽名行後，讓我們儲存文件：

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

這將使用新新增的簽名行來儲存您的文件。

## 第 5 步：設定簽名選項

現在，我們將配置簽名選項，包括簽名行 ID、提供者 ID、註解和簽名時間：

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

這些設定可確保文件使用正確的詳細資訊進行簽署。

## 第 6 步：建立證書持有者

要簽署文檔，我們需要使用 PFX 憑證建立憑證持有者：

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

代替`"morzal.pfx"`與您的實際憑證檔案名稱和`"aw"`與您的證書密碼。

## 第 7 步：簽署文件

最後，我們將使用數位簽章實用程式對文件進行簽章：

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

此程序對文件進行簽名並將其另存為新文件。

## 結論

恭喜！您已使用 Aspose.Words for .NET 在 Word 文件中成功建立了簽名行並設定了提供者 ID。這個強大的庫簡化了文件處理任務，使您的工作流程更加有效率。嘗試一下，看看它如何增強您的專案！

## 常見問題解答

### 我可以自訂簽名行的外觀嗎？
絕對地！您可以在其中調整各種選項`SignatureLineOptions`以滿足您的風格和要求。

### 如果我沒有 PFX 憑證怎麼辦？
您需要從受信任的證書頒發機構獲取一個證書，因為它對於數位簽署文件至關重要。

### 我可以在文件中新增多個簽名行嗎？
是的，您可以透過使用不同的選項重複插入程序來新增多個簽名行。

### Aspose.Words for .NET 與 .NET Core 相容嗎？
是的，Aspose.Words for .NET 支援 .NET Core，使其適用於各種開發環境。

### 數位簽章的安全性如何？
只要您使用有效且可信賴的證書，使用 Aspose.Words 建立的數位簽章就非常安全。