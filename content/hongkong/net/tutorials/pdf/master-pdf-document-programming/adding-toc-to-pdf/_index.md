---
title: 將目錄新增至 PDF 文檔
linktitle: 將目錄新增至 PDF 文檔
second_title: Aspose.PDF for .NET API 參考
description: 本教學課程示範如何使用 Aspose.Pdf for .NET 將目錄 (TOC) 新增至 PDF 文件。
type: docs
weight: 40
url: /zh-hant/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## 介紹

在 PDF 文件中建立目錄 (TOC) 可以大大增強其導航性和可存取性。在本指南中，我們將示範如何使用 Aspose.Pdf for .NET 將 TOC 新增至 PDF 檔案。

## 先決條件

在開始之前，請確保您具備以下條件：

1.   Aspose.PDF for .NET：從以下位置下載並安裝最新版本[這裡](https://releases.aspose.com/pdf/net/).
2.  開發環境：設定 .NET 開發環境，如 Visual Studio。
3.  許可證：如果需要，請申請臨時許可證；請訪問[Aspose.Pdf 授權頁面](https://asposepdf.com/developers)了解更多。

導入必要的庫

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## 第 1 步：載入 PDF 文檔

將現有 PDF 檔案載入到要新增目錄的位置。指定文檔目錄的路徑。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## 第 2 步：為目錄插入新頁面

在 PDF 文件的開頭插入新頁面。此頁面將作為目錄 (TOC)。

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## 步驟 3：建立 TOC 資訊對象

建立一個表示 TOC 資訊的物件。添加標題和連結以便更好地導航。

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## 步驟 4：定義目錄元素

定義將在目錄中顯示的元素（或標題）。這些元素可以幫助讀者導航到文件的特定部分。

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## 第 5 步：建立目錄標題

為目錄中的前兩個元素建立標題。這些標題將連結到各自的頁面。

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## 第 6 步：儲存 PDF 和目錄

最後，儲存更新後的 PDF 檔案。

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## 確認訊息

顯示確認訊息，讓使用者知道流程已完成。

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## 結論

透過 Aspose.PDF for .NET，在 PDF 中新增目錄不僅簡單，而且可以自訂。無論您需要建立簡單的導航連結還是複雜的結構，這個工具都能滿足您的需求。因此，下次您處理冗長的 PDF 時，請不要忘記添加目錄以實現專業風格。

## 常見問題解答

### 我可以在 Aspose.PDF 中自訂 TOC 的外觀嗎？

是的，您可以完全自訂目錄的外觀，包括字體樣式、大小和對齊方式。

### 如何為目錄新增副標題？

您可以透過調整來新增副標題`Heading`水平（例如，`Heading(2)`）。

### 如果文件發生變化，是否可以自動更新目錄？

不，目錄不會自動更新。如果文件結構發生變化，您需要重新建立它。

### 我可以將目錄條目連結到外部文件嗎？

是的，您可以使用超連結將目錄條目連結到外部 PDF 或 URL。

### Aspose.PDF 支援多層目錄嗎？

是的，Aspose.PDF 支援帶有子部分的複雜文件的多層目錄。
