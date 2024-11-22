---
title: 將 Java 腳本新增至 PDF 文件
linktitle: 新增 Java 腳本 PDF 文件
second_title: Aspose.PDF for .NET API 參考
description: 本文檔提供了使用 Aspose.PDF for .NET 將彈出警報或自動列印功能等互動元素新增至 PDF 文件的綜合指南。
type: docs
weight: 10
url: /zh-hant/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## 介紹
本文檔提供了使用 Aspose.PDF for .NET 將彈出警報或自動列印功能等互動元素新增至 PDF 文件的綜合指南。透過利用該程式庫的功能，您可以建立動態且引人入勝的 PDF，以滿足各種使用者的需求。

## 先決條件
在繼續之前，請確保您已從以下位置下載了最新版本的 Aspose.PDF for .NET[Aspose 發布](https://發布.aspose.com/pdf/net/)或透過他們的網站獲得免費試用：[releases.aspose.com](http://releases.aspose.com).

您還應該對 C# 有基本的了解，並熟悉您正在使用的開發環境。此外，如果您需要避免開發過程中的限制，請考慮從 Aspose 取得臨時許可證。

## 導入必要的套件
若要開始編寫程式碼，請從 Aspose.PDF 庫匯入所需的命名空間：

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## 第 1 步：載入現有 PDF
載入要新增互動元素的現有 PDF 文件：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

代替`"YOUR DOCUMENT DIRECTORY"`與 PDF 檔案的實際路徑。

## 步驟 2：在文件層級新增 JavaScript

若要套用在文件開啟時觸發的腳本，請實例化一個`JavascriptAction`目的：

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## 第 3 步：在頁面層級新增 JavaScript

若要根據頁面開啟或關閉觸發特定操作，請實例化一個`JavascriptAction`每個頁面的物件：

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## 步驟 4：儲存 PDF 文檔

若要儲存修改後的 PDF 文檔，請指定輸出文件路徑：

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## 結論
透過遵循本指南並利用 Aspose.PDF for .NET，您可以透過互動式元素有效增強您的 PDF。該庫提供了一個全面的解決方案，用於創建滿足各種用戶需求的動態且引人入勝的文件。

## 常見問題解答

### 我可以將多個 JavaScript 操作新增至 PDF 中的不同頁面嗎？
是的，您可以將不同的 JavaScript 操作指派給各個頁面或整個文件。

### 新增 JavaScript 後是否可以從 PDF 刪除 JavaScript？
是的，您可以透過清除`Actions`文檔或頁面的屬性。

### 我可以在 PDF 中使用哪些類型的 JavaScript 函數？
您可以使用 Adobe Acrobat 的 JavaScript 引擎支援的任何 JavaScript，例如列印、警報和表單操作。

### JavaScript 是否適用於所有 PDF 檢視器？
大多數 JavaScript 操作都可以在支援互動式 PDF 的 PDF 檢視器（例如 Adobe Acrobat）中執行。但是，一些基本的 PDF 閱讀器可能不支援 JavaScript。