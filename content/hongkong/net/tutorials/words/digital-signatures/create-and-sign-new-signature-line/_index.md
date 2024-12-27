---
title: 建立並簽署新的簽名行
linktitle: 建立並簽署新的簽名行
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將數位簽章無縫新增至 Word 文件。這個全面的教程涵蓋了從設定環境和插入簽名行到保存和驗證簽名文件的所有內容。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## 介紹

想要在 Word 文件中新增數位簽章嗎？使用 Aspose.Words for .NET，它比您想像的更容易！本教學將引導您完成設定環境、新增簽名行以及對文件進行數位簽章的步驟。讓我們開始吧！

## 先決條件

在深入研究程式碼之前，請確保您具備以下條件：

1.  Aspose.Words for .NET -[在這裡下載](https://releases.aspose.com/words/net/).
2. .NET 開發環境 - Visual Studio 是完成此任務的理想選擇。
3. 待簽名文件 - 您可以建立新的 Word 文件或使用現有文件。
4. 證書檔-A`.pfx`文件對於數位簽章是必需的。
5. 簽名行圖像（可選）- 您可以包含簽名的圖像檔案。

## 導入所需的命名空間

若要使用Aspose.Words的功能，您需要匯入以下命名空間：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 第 1 步：設定文檔目錄

首先定義文檔目錄的路徑。這將是您儲存和檢索文件的地方。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //指定您的文檔目錄路徑
```

## 第 2 步：建立新文檔

接下來，讓我們建立一個新的 Word 文件。該文件將作為您簽名行的畫布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 3 步：插入簽名行

現在，使用`DocumentBuilder`類別將簽名行插入到文件中：

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 第 4 步：儲存文檔

插入簽名行後，儲存文件。這是簽約前的關鍵一步。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 第 5 步：配置簽名選項

設定簽名過程的選項。這包括指定簽名行 ID 和與簽名一起顯示的選用影像。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") //您的影像的路徑
};
```

## 第6步：載入證書

載入簽署文檔所需的證書文件：

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); //調整檔案名稱和密碼
```

## 第 7 步：簽署文件

最後，使用`DigitalSignatureUtil`班級。使用新名稱儲存簽署的文件以供日後參考。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## 結論

恭喜！您已成功建立了 Word 文檔，新增了簽名行，並使用 Aspose.Words for .NET 對其進行了數位簽章。這個強大的工具簡化了文件自動化，確保您的合約和正式文件得到安全簽署和驗證。

## 常見問題解答

### 我可以使用其他圖像格式作為簽名行嗎？

是的，您可以使用各種圖像格式，包括 PNG、JPG 和 BMP。

### 是否有必要使用一個`.pfx` file for the certificate?

是的，一個`.pfx`文件是用於儲存數位簽章的憑證和私鑰的標準格式。

### 我可以在單一文件中新增多個簽名行嗎？

絕對地！您可以根據需要重複插入步驟來插入多條簽名行。

### 如果我沒有數位憑證怎麼辦？

您需要從受信任的憑證授權單位取得數位憑證或使用 OpenSSL 等工具產生數位憑證。

### 如何驗證文件中的數位簽章？

您可以透過在 Word 中開啟已簽署的文件並檢查簽名詳細資訊來驗證數位簽名，以確認其真實性和完整性。