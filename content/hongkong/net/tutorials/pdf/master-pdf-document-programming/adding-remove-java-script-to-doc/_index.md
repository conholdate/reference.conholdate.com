---
title: 新增刪除 Javascript 到 PDF 文檔
linktitle: 新增刪除 Javascript 到 PDF 文檔
second_title: Aspose.PDF for .NET API 參考
description: 此綜合指南向您展示如何新增自訂行為、動態執行計算或驗證以及與其他軟體應用程式整合。
type: docs
weight: 30
url: /zh-hant/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## 介紹

在這份綜合指南中，我們將深入研究 Aspose.PDF for .NET 的世界，並充分發揮其為 PDF 文件添加自訂 JavaScript 功能的潛力。這項強大的功能可讓您合併動態元素、增強使用者體驗並簡化工作流程。

## 先決條件

要繼續操作，您需要：

1. Aspose.PDF for .NET 安裝在您的專案中（從下載[Aspose.PDF for .NET 下載頁面](https://releases.aspose.com/pdf/net/）)
2. 使用圖書館的有效許可證
3. AC# IDE 或文字編輯器

## 導入包

首先，將必要的命名空間匯入到您的專案中：

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## 步驟 1：初始化一個新的 PDF 文檔

建立一個新的 PDF 文件並將其添加到畫布中：

```csharp
Document doc = new Document();
doc.Pages.Add();
```

您將在此處開始建立包含大量 JavaScript 的 PDF。

## 第 2 步：將 JavaScript 新增至 PDF

使用以下命令將 JavaScript 函數插入到您的文件中`doc.JavaScript`收藏。這是一個例子：

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## 第 3 步：使用 JavaScript 儲存 PDF

將更新的文檔儲存到磁碟：

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

現在，您可以存取和修改現有 PDF 中的 JavaScript 程式碼。

## 第 4 步：在現有 PDF 中載入並查看 JavaScript

載入包含 JavaScript 的 PDF 檔案並使用以下命令存取其金鑰`Keys`財產：

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## 第 5 步：顯示 JavaScript 函數

遍歷 JavaScript 鍵並將其對應的程式碼列印到控制台：

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

這示範如何驗證目前存在哪些 JavaScript 函數。

## 第 6 步：從 PDF 中刪除 JavaScript

使用名稱找到所需的 JavaScript 函數並將其刪除：

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

透過重新列印剩餘的函數來驗證函數是否已成功刪除。

## 結論

在這份綜合指南中，您了解如何釋放 Aspose.PDF for .NET 的可自訂 JavaScript 功能的強大功能。透過此功能，您可以建立動態 PDF、增強使用者體驗並簡化工作流程。透過掌握這些步驟並進一步探索該庫的功能，您將能夠很好地在應用程式中解鎖新的可能性。

## 常見問題解答

### 我可以將多個 JavaScript 函數新增到單一 PDF 中嗎？
是的！您可以使用以下命令根據需要添加任意數量的 JavaScript 函數`doc.JavaScript`收藏。

### 如果我嘗試刪除不存在的 JavaScript 函數會發生什麼？
如果該函數不存在，則`Remove`方法不會拋出錯誤，但也不會刪除任何內容。要處理不存在的函數，您可以新增額外的錯誤處理或修改程式碼以忽略它們。

### 是否可以在開啟 PDF 後立即執行 JavaScript？
是的！您可以將 JavaScript 配置為在特定觸發器上執行，例如開啟文件或按一下按鈕。

### 新增到 PDF 後我可以編輯 JavaScript 嗎？
是的，您可以載入現有 PDF、存取其 JavaScript、修改程式碼並再次儲存文件。

### 刪除 JavaScript 是否會影響 PDF 的其餘內容？
不，刪除 JavaScript 只會影響腳本。 PDF 的內容保持不變。