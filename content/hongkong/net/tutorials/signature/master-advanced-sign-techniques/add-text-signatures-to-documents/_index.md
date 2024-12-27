---
title: 使用 GroupDocs.Signature 將文字簽章新增至文檔
linktitle: 新增文字簽名
second_title: GroupDocs.Signature .NET API
description: 了解如何使用 GroupDocs.Signature for .NET 對帶有文字的文件進行簽署。以程式設計方式新增文字簽名的逐步指南。
type: docs
weight: 17
url: /zh-hant/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## 介紹

在當今的數位環境中，電子文件簽名對於簡化工作流程和節省資源至關重要。 GroupDocs.Signature for .NET 提供了一個強大的解決方案，以程式設計方式將文字簽章新增至各種文件格式。本教學將引導您完成使用 GroupDocs.Signature for .NET 對文字文件進行簽署的步驟。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1. GroupDocs.Signature for .NET：從以下位置下載並安裝該程式庫[這裡](https://releases.groupdocs.com/signature/net/).
2. 開發環境：設定 .NET 開發環境。
3. 文件：準備您要簽署的文件（例如 PDF、Word）。

## 導入必要的命名空間

首先將所需的命名空間匯入到您的 .NET 專案中：

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 第 1 步：載入文檔

首先載入您要簽署的文件：

```csharp
string filePath = "sample.pdf"; //您的文件的路徑
string fileName = Path.GetFileName(filePath);
```

## 步驟2：定義輸出檔案路徑

接下來，設定保存簽名文檔的輸出檔案路徑：

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## 第 3 步：建立簽名選項

配置文字簽名的選項，包括內容、位置、大小、顏色和字體樣式：

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X位置
    Top = 200, //Y位置
    Width = 100, //簽名寬度
    Height = 30, //簽名高度
    ForeColor = Color.Red, //文字顏色
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } //字體設定
};
```

## 第 4 步：簽署文件

最後，使用 GroupDocs.Signature 應用文字簽章並儲存簽章文件：

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); //簽署文件
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## 結論

在本教學中，我們示範如何使用 GroupDocs.Signature for .NET 以程式設計方式將文字簽章新增至文件。透過執行以下步驟，您可以有效地增強文件的安全性和真實性。

## 常見問題解答

### 我可以自訂文字簽名的外觀嗎？
是的，您可以自訂文字簽名的各種屬性，例如顏色、字體、大小和位置，以滿足您的需求。

### GroupDocs.Signature 是否與多種文件格式相容？
絕對地！ GroupDocs.Signature 支援多種格式，包括 PDF、Word、Excel、PowerPoint 等。

### 我可以在單一文件中新增多個文字簽名嗎？
是的，您可以新增多個文字簽名，每個簽名都有自己的自訂選項。

### GroupDocs.Signature 是否確保簽署後文件的完整性？
是的，該庫使用強大的加密演算法來確保文檔完整性並防止簽名後被篡改。

### 購買前是否有試用版可供測試？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/)在購買前探索功能。