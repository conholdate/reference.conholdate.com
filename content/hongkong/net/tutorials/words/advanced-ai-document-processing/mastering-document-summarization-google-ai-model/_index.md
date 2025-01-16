---
title: 掌握文件摘要 Google AI 模型
linktitle: 掌握文件摘要 Google AI 模型
second_title: Aspose.Words 文件處理 API
description: 逐步學習如何在 .NET 中使用 Aspose.Words 和 Google AI 總結 Word 文件。請依照本指南簡化內容提取、文件洞察和自動化。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/advanced-ai-document-processing/mastering-document-summarization-google-ai-model/
---
## 介紹

簡化大型文件中的資訊從未如此簡單。本指南探討如何利用 Aspose.Words for .NET 和 Google 的 AI 模型準確且有效率地總結 Word 文件。無論您是需要建立簡潔的報告摘要、從研究中提取關鍵見解，還是處理多個文檔，這個綜合教學都將引導您完成每一步。

## 先決條件

首先，請確保您具備以下條件：

1. 熟練 C# 和 .NET：對 C# 和 .NET 的基本了解將幫助您更有效地瀏覽程式碼和概念。
2.  Aspose.Words for .NET：這個強大的程式庫提供了在.NET應用程式中建立、編輯和管理Word文件的工具。下載它[這裡](https://releases.aspose.com/words/net/).
3. Google AI 的 API 金鑰：需要 API 金鑰來驗證對 Google AI 模型的請求。將此密鑰安全地儲存在您的環境變數中。
4. 開發環境：建置和執行應用程式需要與 .NET 相容的 IDE（例如 Visual Studio）。
5. 範例 Word 文件：確保您準備好範例 Word 文件（例如「Big document.docx」、「Document.docx」）以測試摘要功能。

## 導入必要的命名空間

首先匯入所需的命名空間以將 Aspose.Words 與 Google AI 整合。

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.AI;
```

準備好這些包後，您就可以開始進行文件摘要了。

## 第 1 步：設定目錄路徑

首先定義輸入文件的文件路徑以及要儲存摘要文件的位置。

```csharp
//原始檔目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//保存輸出工件的目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

代替`"YOUR_DOCUMENT_DIRECTORY"`和`"YOUR_ARTIFACTS_DIRECTORY"`與系統上的實際路徑。這些目錄將作為載入和保存文件的參考。

## 步驟2：載入Word文檔

接下來，使用以下命令載入您想要總結的文檔`Document`來自 Aspose.Words 的類別。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

確保檔案名稱與指定目錄中的文件相符。這`Document`類別允許您將 Word 文件載入到記憶體中進行處理。

## 步驟 3： 檢索您的 Google API 金鑰

若要存取 Google 的 AI 模型，請從環境變數中安全地檢索 API 金鑰。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

透過將 API 金鑰儲存為環境變量，可以降低暴露程式碼中敏感資訊的風險。

## 步驟 4：設定 AI 模型實例

透過使用GPT-4 Mini模型建立實例來配置AI模型。該模型為您的文件提供高效的摘要功能。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

請參閱[Aspose.Words 文檔](https://reference.aspose.com/words/net/)有關型號選擇和配置的更多詳細資訊。

## 第 5 步：總結單一文檔

若要建立單一文件的摘要，請使用`Summarize`模型實例提供的方法。指定所需的摘要長度，在本例中為簡短摘要。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

這段程式碼創建了一個總結版本`firstDoc`並將其保存在artifacts目錄中。調整摘要長度以滿足您的需要，無論是短、中或長。

## 第 6 步：同時總結多個文檔

對於想要一次匯總多個文件的場景，請將文件陣列傳遞給`Summarize`方法。

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

這種方法產生了一個綜合的摘要，整合了來自雙方的內容`firstDoc`和`secondDoc`，在單一總結文件中提供更廣泛的概述。

## 結論

透過本教學課程，您將能夠使用 Aspose.Words for .NET 和 Google AI 模型有效地總結文件。從定義文件目錄和載入文件到檢索 API 金鑰和設定模型實例，每個步驟都確保您可以有效地處理大量文字並僅用幾行程式碼即可建立簡潔的摘要。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？

Aspose.Words for .NET 是一個多功能函式庫，用於在 .NET 應用程式中建立、編輯和轉換 Word 文檔，提供進階文檔自動化功能。

### 如何取得用於 AI 摘要的 Google API 金鑰？

若要使用 Google 的 AI 服務，請在 Google Cloud 上註冊、啟用相關 API 服務並保護您的 API 金鑰。

### 我可以同時總結多個文件嗎？

是的，Aspose.Words 可讓您將多個文件傳遞給 AI 模型，從多個來源產生全面的摘要。

### 如何控制摘要長度？

使用`SummaryLength`內的選項`SummarizeOptions`類別將所需的摘要長度設為短、中或長。

### 在哪裡可以找到 Aspose.Words 的其他資源？

有關更多範例和技術細節，請參閱[Aspose.Words 文檔](https://reference.aspose.com/words/net/).