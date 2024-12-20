---
title: 將圖元檔轉換為 Svg
linktitle: 將圖元檔轉換為 Svg
second_title: Aspose.Words 文件處理 API
description: 了解如何使用強大的 Aspose.Words for .NET 程式庫將圖元檔案轉換為 SVG 來增強您的 Word 文件。這個綜合教學將引導您完成從初始化文件到插入 SVG 圖形的每個步驟。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-svg/
---
## 介紹

你好，程式設計愛好者！您是否曾想使用可縮放向量圖形來增強您的 Word 文件？如果是這樣，那麼您來對地方了！在本教學中，我們將探索如何使用強大的 Aspose.Words for .NET 程式庫將 Word 文件中的圖元檔案轉換為 SVG。最後，您將掌握使文件具有視覺吸引力和多功能性的技能。讓我們開始吧！

## 先決條件

在我們深入之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. .NET Framework：確保您已安裝 .NET Framework。
3. 開發環境：可以使用任何IDE，例如Visual Studio。
4. C# 的基本知識：熟悉 C# 將會很有幫助，但如果您是新手，請不要擔心 — 我們將引導您完成每個步驟。

## 導入命名空間

首先，讓我們在 C# 專案中導入必要的命名空間。此步驟對於存取 Aspose.Words 功能至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

整理好先決條件和命名空間後，讓我們繼續學習將圖元檔案轉換為 SVG 的逐步指南。

## 第 1 步：初始化 Document 和 DocumentBuilder

我們首先建立一個新的 Word 文件並初始化`DocumentBuilder`對象，這將幫助我們添加內容。

```csharp
//定義文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

此程式碼初始化一個新文檔和一個文檔產生器。這`dataDir`變數保存您儲存檔案的路徑。

## 第 2 步：為文件新增文本

接下來，讓我們透過文字描述在文件中添加一些上下文。

```csharp
builder.Write("Here is an SVG image: ");
```

此行將文字「Here is an SVG image:」新增至您的文件中，為您要插入的 SVG 提供上下文。

## 第 3 步：插入 SVG 影像

現在到了令人興奮的部分！我們將使用以下命令將 SVG 映像插入到我們的文件中`InsertHtml`方法。

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg>");
```

此程式碼片段插入一個具有指定點和樣式的簡單 SVG 多邊形。請隨意自訂 SVG 程式碼以滿足您的需求！

## 步驟 4：定義 HtmlSaveOptions

為了確保我們的圖元檔案儲存為 SVG，我們將定義`HtmlSaveOptions`並設定`MetafileFormat`財產給`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

此配置告訴 Aspose.Words 在匯出為 HTML 時將文件中的任何圖元文件轉換為 SVG 格式。

## 第 5 步：儲存文檔

最後，讓我們使用以下命令來儲存文檔`Save`的方法`Document`班級。

```csharp
doc.Save(dataDir + "ConvertMetafilesToSvg.html", saveOptions);
```

該行將文件儲存到指定目錄，文件名為`ConvertMetafilesToSvg.html`，應用`saveOptions`以確保圖元檔案轉換為 SVG。

## 結論

恭喜！您已使用 Aspose.Words for .NET 成功將 Word 文件中的圖元檔案轉換為 SVG。只需幾行程式碼，您就可以使用可縮放向量圖形增強文檔，使它們更具動態性和視覺吸引力。在您的專案中嘗試一下，祝您編碼愉快！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個強大的程式庫，可讓您使用 C# 以程式設計方式建立、修改和轉換 Word 文件。

### 我可以將 Aspose.Words for .NET 與 .NET Core 一起使用嗎？
絕對地！ Aspose.Words for .NET 支援 .NET Core，使其適用於各種 .NET 應用程式。

### 如何獲得 Aspose.Words for .NET 的免費試用版？
您可以從以下位置下載免費試用版：[Aspose 發佈頁面](https://releases.aspose.com/).

### 我可以使用 Aspose.Words 將其他圖像格式轉換為 SVG 嗎？
是的，Aspose.Words 支援將各種圖像格式（包括圖元檔案）轉換為 SVG。

### 在哪裡可以找到 Aspose.Words for .NET 的文檔？
詳細文件可在[Aspose 文件頁面](https://reference.aspose.com/words/net/).