---
title: 在 GroupDocs Comparison for .NET 中儲存文件元資料來源
linktitle: 在 .NET 的 GroupDocs Comparison 中儲存文件元資料來源
second_title: GroupDocs.Comparison .NET API
description: 利用 GroupDocs Comparison for .NET 充分發揮 .NET 應用程式中文件比較的潛力。本逐步教學將引導您輕鬆比較文檔，同時專注於保存文檔元資料來源。
type: docs
weight: 14
url: /zh-hant/net/tutorials/comparison/load-and-save-documents/save-documents-metadata-source/
---
## 介紹

在軟體開發中，特別是在法律、金融和教育等行業中，有效比較文件的能力至關重要。 GroupDocs Comparison for .NET 提供了一個強大的解決方案來無縫比較 .NET 應用程式中的文件。本教學將指導您如何利用這個強大的函式庫來保存文件元資料來源，確保您最大限度地發揮其功能來完成文件比較任務。

## 先決條件

在我們開始之前，請確保您已進行以下設定：

1. 開發環境：您的電腦上已準備好.NET 開發環境。
2. GroupDocs Comparison 安裝：從下列位置下載並安裝 GroupDocs Comparison for .NET[地點](https://releases.groupdocs.com/comparison/net/).
3. 文件文件：準備要比較的來源文件文件和目標文件文件。
4. C# 基礎知識：熟悉 C# 程式設計基礎將幫助您理解所提供的程式碼片段。

## 導入所需的命名空間

首先將必要的命名空間匯入到您的專案中：

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## 第 1 步：定義輸出目錄和檔名

首先，指定比較文件的保存位置及其名稱：

```csharp
string outputDirectory = "Your Document Directory"; //例如，“C:\\文檔”
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```

## 第 2 步：初始化比較器對象

創建一個`Comparer`使用來源文件路徑的實例：

```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
這會初始化`Comparer`對象，為您的文件比較提供基礎。

## 第三步：新增目標文檔

接下來，將目標文件納入比較：

```csharp
comparer.Add("TARGET.docx");
```
此步驟指定您要與來源進行比較的文件。

## 步驟 4：比較文件並儲存元資料來源

現在，是時候執行比較並保存文件元資料來源了：

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
在這裡，`Compare`方法比較來源文件和目標文件。透過使用`CloneMetadataType`，您確保保留來源文件中的元資料。

## 第 5 步：顯示輸出訊息

對比完成後，提供操作回饋：

```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
此訊息確認比較成功並指示在哪裡可以找到輸出文件。

## 結論

GroupDocs Comparison for .NET 是執行 .NET 應用程式中的文件比較任務的寶貴工具。透過遵循本指南，您已了解如何有效保存文件元資料來源，從而增強文件比較流程和整體生產力。

## 常見問題解答

### GroupDocs Comparison for .NET 可以比較不同格式的文件嗎？

是的，它支援多種格式，包括 DOCX、PDF、PPTX 等。

### 有試用版嗎？

您可以從以下位置存取試用版[這裡](https://releases.groupdocs.com/).

### 我可以自訂比較文件的輸出格式嗎？

絕對地！ GroupDocs Comparison 允許對輸出格式進行廣泛的自訂。

### 是否能為用戶提供技術支援？

是的，您可以透過以下方式尋求協助[支援論壇](https://forum.groupdocs.com/c/comparison/12).

### 我可以在哪裡購買許可證？

可以向 GroupDocs 網站購買許可證[這裡](https://purchase.groupdocs.com/buy).