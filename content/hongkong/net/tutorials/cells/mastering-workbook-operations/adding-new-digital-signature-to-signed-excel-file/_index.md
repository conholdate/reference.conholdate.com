---
title: 在已簽名的 Excel 檔案中新增新的數位簽名
linktitle: 在已簽名的 Excel 檔案中新增新的數位簽名
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何使用 Aspose.Cells for .NET 將新的數位簽章新增至現有簽署的 Excel 檔案。本綜合指南涵蓋了所有先決條件、逐步說明和程式碼範例。
type: docs
weight: 12
url: /zh-hant/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## 介紹

在當今的數位環境中，確保文件的真實性和完整性比以往任何時候都更加重要。數位簽章提供了一種可靠的方法來驗證文件是否未被更改以及文件是否來自合法來源。如果您正在 .NET 中處理 Excel 文件，並且需要在已簽署的文件中新增的數位簽名，那麼本指南適合您！我們將逐步介紹使用 Aspose.Cells for .NET 將數位簽章新增至現有簽章 Excel 檔案的過程。

## 先決條件

在我們深入實施之前，請確保您具備以下條件：

1.  Aspose.Cells for .NET：從下列位置下載並安裝 Aspose.Cells[發布頁面](https://releases.aspose.com/cells/net/).
2. .NET Framework：確保您的電腦已設定 .NET Framework，並且您熟悉基本的 .NET 程式設計概念。
3. 數位憑證：取得.pfx格式的有效數位憑證。為了進行測試，您可以建立自簽名憑證。
4. 開發環境：使用 Visual Studio 等 IDE 編寫和執行 C# 程式碼。
5. 範例 Excel 文件：擁有一個已進行數位簽章的現有 Excel 文件，該文件將作為新增簽名的目標。

滿足這些先決條件後，讓我們開始編寫程式碼！

## 導入必要的套件

在 C# 檔案的頂部，包含以下命名空間以存取所需的類別和方法：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 第 1 步：定義您的目錄

指定來源檔案的目錄以及輸出檔案的儲存位置：

```csharp
//原始碼目錄
string sourceDir = "Your Document Directory"; //替換為你的實際目錄
//輸出目錄
string outputDir = "Your Document Directory"; //替換為你的實際目錄
```

## 第 2 步：載入現有的簽名工作簿

載入已簽署的 Excel 工作簿：

```csharp
//載入已經數位簽署的工作簿
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## 第 3 步：建立數位簽章集合

建立一個集合來管理您的數位簽名：

```csharp
//建立數位簽章集合
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## 第 4 步：載入您的證書

加載您的數位證書，該證書將用於建立新簽名：

```csharp
//證書文件及其密碼
string certFileName = sourceDir + "AsposeDemo.pfx"; //您的證書文件
string password = "aspose"; //您的憑證密碼

//建立新證書
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## 第 5 步：建立新的數位簽名

現在，建立一個新的數位簽名並將其添加到您的收藏中：

```csharp
//建立新的數位簽章並將其新增至集合中
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## 步驟 6：將簽章集合新增至工作簿中

將數位簽章集合新增至工作簿：

```csharp
//將數位簽章集合新增至工作簿
workbook.AddDigitalSignature(dsCollection);
```

## 第 7 步：儲存工作簿

使用新的數位簽章儲存工作簿，包括：

```csharp
//儲存工作簿
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## 第8步：確認成功

成功執行後提供回饋：

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## 結論

恭喜！您已使用 Aspose.Cells for .NET 成功將新的數位簽章新增至已簽署的 Excel 檔案。此過程增強了文件的安全性並確保其真實性和完整性。

## 常見問題解答

### 什麼是數位簽章？

數位簽名是一種數學方案，用於驗證數位訊息或文件的真實性和完整性，確保它們沒有被更改並確認簽名者的身份。

### 我需要特殊憑證來建立數位簽章嗎？

是的，需要由受信任的憑證授權單位 (CA) 頒發的數位憑證才能建立有效的數位簽章。

### 我可以使用自簽名憑證進行測試嗎？

絕對地！您可以將自簽名憑證用於開發和測試目的，但對於生產，建議使用來自受信任 CA 的憑證。

### 如果我嘗試在未簽名的文件中添加簽名，會發生什麼情況？

如果您嘗試將數位簽章新增至尚未簽署的文件中，它將正常運作，但不會出現原始簽章。

### 在哪裡可以找到有關 Aspose.Cells 的更多資訊？

有關詳細指南和 API 參考，請查看[Aspose.Cells 文檔](https://reference.aspose.com/cells/net/).