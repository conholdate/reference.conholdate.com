---
title: 在 Word 中新增自訂文件屬性
linktitle: 在 Word 中新增自訂文件屬性
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 透過自訂文件屬性增強您的 Word 文件。本綜合指南將引導您完成整個過程。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## 介紹

歡迎！如果您正在探索 Aspose.Words for .NET 並希望了解如何在 Word 文件中新增自訂文件屬性，那麼您來對地方了。自訂屬性對於儲存內建屬性未涵蓋的其他元資料非常有用。無論您需要追蹤文件授權、修訂號或特定日期，自訂屬性都可以提供協助。在本教學中，我們將引導您完成使用 Aspose.Words for .NET 無縫新增這些屬性的步驟。讓我們開始吧！

## 先決條件

在深入研究程式碼之前，請確保您具備以下條件：

1.  Aspose.Words for .NET 函式庫：下載[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：IDE，例如 Visual Studio。
3. C# 基礎：熟悉 C# 和 .NET 將很有幫助。
4. 範例文檔：準備一個範例 Word 文檔，名為`Properties.docx`進行修改。

## 導入命名空間

要存取 Aspose.Words 的功能，您需要在程式碼開頭匯入必要的命名空間：

```csharp
using System;
using Aspose.Words;
```

## 第1步：設定文檔路徑

接下來，讓我們定義 Word 文件的路徑。此步驟對於找到並打開您的`Properties.docx`文件。

```csharp
//指定文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

確保更換`"YOUR DOCUMENT DIRECTORY"`與文檔的實際路徑。

## 第 2 步：存取自訂文件屬性

現在，讓我們存取 Word 文件的自訂文件屬性，自訂元資料將駐留在其中。

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

此行使您可以存取將要使用的自訂屬性的集合。

## 第 3 步：檢查現有屬性

在新增屬性之前，明智的做法是檢查屬性是否已存在以避免重複。

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

此程式碼檢查“Authorized”屬性是否已存在。如果是這樣，該方法會提前退出，以防止重複。

## 第 4 步：新增布爾屬性

讓我們新增一個自訂布林屬性來指示文件是否已授權。

```csharp
customDocumentProperties.Add("Authorized", true);
```

此行新增一個名為「Authorized」的屬性並將其值設為`true`.

## 第 5 步：新增字串屬性

接下來，我們將透過新增字串屬性來指定誰授權了該文件。

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

請隨意將“John Smith”替換為您喜歡的任何名稱。

## 第 6 步：新增日期屬性

要追蹤文件的授權時間，我們會新增一個日期屬性。

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

此行新增一個名為「授權日期」的屬性，並使用以下命令為其指派今天的日期`DateTime.Today`.

## 第 7 步：新增修訂號

對於版本控制，我們可以新增一個屬性來追蹤文件的修訂號。

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

在這裡，我們新增一個「授權修訂版」屬性，用於保存文件的目前修訂版號。

## 第 8 步：新增數字屬性

最後，讓我們新增一個數字屬性來儲存授權金額，例如預算數字。

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

此行新增一個名為「Authorized Amount」的屬性，其值為`123.45`。您可以根據需要調整此數字。

## 結論

恭喜！您已使用 Aspose.Words for .NET 成功將自訂文件屬性新增至 Word 文件。這些屬性是儲存根據您的需求自訂的元資料的強大方法，無論是追蹤授權詳細資訊、修訂號還是特定金額。

## 常見問題解答

### 什麼是自訂文件屬性？
自訂文件屬性是您可以新增到 Word 文件中的元數據，用於儲存內建屬性未涵蓋的其他資訊。

### 我可以添加字串和數字以外的屬性嗎？
是的，您可以新增各種類型的屬性，包括布林值、日期，甚至自訂物件。

### 如何在 Word 文件中存取這些屬性？
您可以使用 Aspose.Words 以程式設計方式存取自訂屬性，或透過文件屬性直接在 Word 中查看它們。

### 是否可以編輯或刪除自訂屬性？
絕對地！您可以使用Aspose.Words提供的方法輕鬆編輯或刪除自訂屬性。

### 可以使用自訂屬性來過濾文件嗎？
是的！自訂屬性非常適合根據特定元資料對文件進行分類和過濾。