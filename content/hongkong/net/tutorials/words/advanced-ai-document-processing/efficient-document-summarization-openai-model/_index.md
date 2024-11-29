---
title: 高效文檔摘要開放AI模型
linktitle: 高效文檔摘要開放AI模型
second_title: Aspose.Words 文件處理 API
description: 透過這個涵蓋先決條件、設定和編碼範例的綜合教程，了解如何快速且準確地總結大型文件。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/advanced-ai-document-processing/efficient-document-summarization-openai-model/
---
## 介紹

高效的文件管理在當今的數位世界中已變得不可或缺。透過 Aspose.Words for .NET，文件摘要變得更容易、更有效率，特別是與 OpenAI 模型的功能搭配使用時。本指南將引導您逐步完成使用 Aspose.Words for .NET 和 OpenAI 模型自動匯總文件的過程，從而節省您的時間並提供快速見解。無論您是在總結報告、學術論文或大量文檔，本指南都將幫助您充分利用您的工具。

## 先決條件

### .NET環境設定
確保您擁有相容的 .NET Framework 版本。本教學與 .NET 5.0 及更高版本相容。

### 安裝 Aspose.Words for .NET
從以下位置下載 Aspose.Words for .NET 套件[阿斯普斯網站](https://releases.aspose.com/words/net/)，然後使用 Visual Studio 中的 NuGet 套件管理器將其安裝到您的專案中。

### 取得 OpenAI API 金鑰
要存取 OpenAI 的語言模型，您需要 API 金鑰。註冊[OpenAI 網站](https://openai.com/)，檢索您的密鑰，並妥善保管以進行整合。

### 整合開發環境
使用 Visual Studio 作為 IDE 將簡化編碼和偵錯過程。

## 導入必要的庫

在您的專案中，匯入所需的庫，以確保您可以存取文件操作和摘要所需的類別和方法。

### 導入 Aspose.Words 包

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;
using System.Text;
```

如果使用外部程式庫來處理對 OpenAI 的 API 呼叫，請確保已安裝並配置它。現在，讓我們深入了解如何設定文件摘要。

## 第 1 步：定義文檔路徑

定義目錄來組織文件來源並保存產生的摘要。

```csharp
string MyDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
string ArtifactsDir = "YOUR_OUTPUT_DIRECTORY_PATH";
```

## 第 2 步：載入要總結的文檔

使用 Aspose.Words 將一份或多份文件載入到您的應用程式中。此範例載入兩個文件用於演示目的：

```csharp
Document doc1 = new Document(MyDir + "BigDocument.docx");
Document doc2 = new Document(MyDir + "AnotherDocument.docx");
```

## 第 3 步：設定 OpenAI API 金鑰

為了安全起見，請從環境變數中檢索 OpenAI API 金鑰，而不是對其進行硬編碼。

```csharp
string apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
```

## 第四步：初始化OpenAI模型

建立 OpenAI 模型的實例以進行匯總。在這裡，我們使用的是`Gpt4OMini`保持摘要簡潔但富有洞察力。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

## 第 5 步：總結單一文檔

建立模型實例後，產生單一文件的摘要。

```csharp
Document summaryDoc = model.Summarize(doc1, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
summaryDoc.Save(ArtifactsDir + "SingleDocSummary.docx");
```

這將保存一個簡短的摘要`doc1`在指定的輸出目錄中。

## 第 6 步：總結多個文檔

如果您想從多個文件產生組合摘要，只需修改摘要方法即可。

```csharp
Document combinedSummary = model.Summarize(new Document[] { doc1, doc2 }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
combinedSummary.Save(ArtifactsDir + "CombinedSummary.docx");
```

此方法非常適合從大量報告或相關文件中批次產生摘要。

## 結論

利用 Aspose.Words for .NET 和 OpenAI 模型進行文件摘要可帶來巨大的生產力優勢。無論是處理單一文件還是多個文件，這種整合都可以提供快速、可靠的摘要，將複雜的文件轉換為簡潔、易於理解的見解。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個強大的程式庫，用於以程式設計方式管理 Word 文件。它支援多種格式的建立、操作和轉換。

### 為什麼需要 OpenAI API 金鑰？
需要 API 金鑰才能存取 OpenAI 的語言模型以產生摘要或其他自然語言處理任務。

### 我可以合併多個文檔摘要嗎？
是的，Aspose.Words 允許您同時從多個文件產生摘要，非常適合專案報告或案例研究。

### 如何安裝 Aspose.Words for .NET？
使用 Visual Studio 中的 NuGet 套件管理器透過搜尋套件並選擇「安裝」來安裝 Aspose.Words。

### Aspose.Words 可以免費使用嗎？
您可以下載 Aspose.Words 的免費試用版，透過以下方式測試其功能：[阿斯普斯網站](https://releases.aspose.com/).