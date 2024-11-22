---
title: 使用 AI 模型掌握文件摘要
linktitle: 使用 AI 模型掌握文件摘要
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 釋放文件自動化的潛力。了解如何使用進階 AI 模型輕鬆總結文件。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/advanced-ai-document-processing/mastering-document-summarization-ai-model/
---
## 介紹

在當今快節奏的世界中，對高效文件管理和快速資料擷取的需求至關重要。想像一下一個自動化解決方案，可以在幾秒鐘內總結長文件。透過 Aspose.Words for .NET，我們可以將 AI 支援的摘要功能直接整合到應用程式中，將冗長的文件轉換為簡潔的摘要，從而節省時間並提高工作效率。本指南涵蓋了利用 Aspose.Words for .NET 和 OpenAI 的 GPT 等 AI 模型所需的所有步驟，以最少的程式碼自動匯總 Word 文件。

## 先決條件

首先，請確保您已具備以下條件：

1. Visual Studio：編碼和測試所需。如果您尚未安裝，可以免費下載。
2. .NET Framework 或 .NET Core：Aspose.Words for .NET 支援兩者，因此請確保您擁有相容的版本。
3.  Aspose.Words for .NET：從以下位置下載並安裝最新版本[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
4. AI 模型 API 金鑰：要產生摘要，需要存取 AI 模型 API（例如 OpenAI）。在 AI 提供者的網站上註冊以取得 API 金鑰。
5. 基本 C# 知識：對 C# 程式設計有一定的了解將有助於您有效地遵循。

完成所有設定後，繼續匯入必要的套件並初始化專案。

## 設定專案環境

讓我們逐步完成在 Visual Studio 中建立和設定控制台應用程式以執行文件摘要的步驟。

### 建立新的控制台應用程式

1. 打開視覺工作室。
2. 選擇“建立新項目”。
3. 根據您的設定選擇「控制台應用程式 (.NET Framework)」或「控制台應用程式 (.NET Core)」。
4. 為您的項目命名並選擇儲存位置。

### 安裝Aspose.Words和AI模型包

若要啟用 Aspose.Words 功能，請透過 NuGet 套件管理員新增它。

1. 在解決方案資源管理器中以滑鼠右鍵按一下您的項目，然後選擇「管理 NuGet 套件」。
2. 搜尋`Aspose.Words`並點擊安裝。
3. 如果需要，還可以安裝任何特定的 AI 模型套件以進行整合（例如 OpenAI）。

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

環境設定完畢後，讓我們繼續進行文件摘要設定。

我們將逐步介紹設定文件目錄、載入文件、配置 AI 模型以及執行單一文件和多文件摘要。

## 第 1 步：定義文檔目錄

指定用於儲存輸入文件和保存匯總輸出的目錄。

```csharp
//定義文件和輸出目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

代替`YOUR_DOCUMENT_DIRECTORY`和`YOUR_ARTIFACTS_DIRECTORY`以及輸入和輸出目錄的路徑。

## 第 2 步：載入要總結的文檔

將要匯總的Word文件載入到程式中。操作方法如下：

```csharp
Document firstDoc = new Document(MyDir + "BigDocument.docx");
Document secondDoc = new Document(MyDir + "AdditionalDocument.docx");
```

此範例假設您有兩份文件另存為`BigDocument.docx`和`AdditionalDocument.docx`。根據您的檔案名稱根據需要進行自訂。

## 步驟 3：初始化並配置 AI 模型

使用 API 金鑰，我們將初始化用於摘要的 AI 模型。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

將 API 金鑰安全地儲存在環境變數中以確保其受到保護。

## 步驟 4：產生單一文件的摘要

總結單一文件很簡單。定義所需的摘要長度並將輸出儲存到指定的目錄。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "SingleDocumentSummary.docx");
```

這段程式碼總結了`firstDoc`文件並將摘要另存為`SingleDocumentSummary.docx`.

## 步驟 5：產生多個文件的摘要

若要一次匯總多個文檔，請將它們作為集合加載並定義匯總選項。

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "MultiDocumentSummary.docx");
```

這種方法允許同時總結兩個文件。輸出將保存為`MultiDocumentSummary.docx`.

## 結論

借助 Aspose.Words for .NET 和 AI 驅動的模型，總結大型文件變得毫不費力。將此功能整合到您的應用程式中可以簡化文件處理，為使用者提供簡潔、準確的摘要。無論是在商業、教育或個人專案中，此設定都可以大幅減少閱讀冗長文件所花費的時間。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個用來管理 Word 文件的綜合函式庫。它允許用戶以編程方式輕鬆創建、編輯、轉換和渲染 Word 文件。

### 如何取得AI模型的API Key？
若要存取 AI 模型服務，請向 OpenAI 或 Google 等供應商註冊，並按照他們的說明產生 API 金鑰。

### Aspose.Words 可以在沒有 AI 的情況下總結文件嗎？
Aspose.Words 本身並不會執行基於 AI 的摘要。它需要與外部人工智慧模型整合以實現摘要功能。

### Aspose.Words 有免費試用版嗎？
是的，Aspose 提供免費試用版，可以從他們的網站下載。

### 在哪裡可以找到更多 Aspose.Words 資源？
這[Aspose.Words 文檔](https://reference.aspose.com/words/net/)提供深入的資源和範例。