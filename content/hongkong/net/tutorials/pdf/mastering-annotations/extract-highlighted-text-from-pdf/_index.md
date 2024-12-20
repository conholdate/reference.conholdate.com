---
title: 使用 Aspose.PDF for .NET 從 PDF 中提取反白的文本
linktitle: 使用 Aspose.PDF for .NET 從 PDF 中提取反白的文本
second_title: Aspose.PDF for .NET API 參考
description: 透過學習如何使用 Aspose.PDF for .NET 提取突出顯示的文本，釋放 PDF 文件的潛力。這份綜合指南將引導您完成從設定到實施的每個步驟。
type: docs
weight: 60
url: /zh-hant/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## 介紹

處理 PDF 檔案時，提取突出顯示的文字對於資料分析、內容審查或組織筆記至關重要。如果您使用 Aspose.PDF for .NET，那麼您很幸運。本教學提供了有關如何有效地從 PDF 文件中提取突出顯示文字的清晰逐步說明。

## 先決條件

在開始之前，請確保您已具備以下條件：

-  Aspose.PDF for .NET Library：從以下位置下載該程式庫：[發布頁面](https://releases.aspose.com/pdf/net/).
- 開發環境：像Visual Studio這樣的工作環境。
- C# 基礎知識：需要熟悉 C# 和物件導向程式設計。
-  Aspose 授權：雖然您可以從免費試用開始，[臨時執照](https://purchase.aspose.com/temporary-license/)或完整許可證[這裡](https://purchase.aspose.com/buy)將提供不受限制的訪問。

## 導入必要的命名空間

首先在 C# 專案中匯入所需的命名空間：

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

這些命名空間提供對處理 PDF 文件和註釋所需的類別和方法的存取。

## 第 1 步：設定您的專案目錄

指定 PDF 檔案所在的目錄：

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

確保將路徑替換為 PDF 檔案的實際目錄。

## 第 2 步：載入 PDF 文檔

使用以下程式碼載入 PDF 文件：

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

確保指定的檔案存在於給定目錄中。

## 第 3 步：訪問頁面上的註釋

若要存取註釋，請循環瀏覽所需頁面（在本例中為第一頁）上的註釋：

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

此程式碼過濾`TextMarkupAnnotation`類型，代表亮點。

## 步驟 4：提取突出顯示的文本

現在，從突出顯示的註釋中提取並顯示文字：

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

這將檢索與突出顯示相關的所有標記文字片段並將它們列印到控制台。

## 結論

使用 Aspose.PDF for .NET 從 PDF 中提取反白的文字非常簡單，並且可以顯著增強文件處理過程。透過執行上述步驟，您可以有效地收集各種應用程式的突出顯示文本，例如報告準備或資料分析。

## 常見問題解答

### 我可以提取其他類型的註釋嗎？
是的，只需調整`if`條件包括不同的註釋類型，例如`TextAnnotation`或者`StampAnnotation`.

### 如何從所有 PDF 頁面中提取突出顯示的文字？
您可以使用以下方法循環瀏覽所有頁面：
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Aspose.PDF for .NET 是否需要許可證？
可以免費試用，但請考慮[臨時執照](https://purchase.aspose.com/temporary-license/)或完全存取的完整許可證。

### 我可以將提取的文字儲存到文件中嗎？
絕對地！您可以修改程式碼以將提取的文字寫入文字檔案。

### Aspose.PDF 支援其他平台嗎？
是的，Aspose.PDF也支援Java和其他平台，提供類似的功能。