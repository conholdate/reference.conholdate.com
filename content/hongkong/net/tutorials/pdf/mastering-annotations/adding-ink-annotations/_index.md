---
title: 使用 Aspose.PDF for .NET 新增墨跡註釋
linktitle: 使用 Aspose.PDF for .NET 新增墨跡註釋
second_title: Aspose.PDF for .NET API 參考
description: 了解如何使用 Aspose.PDF for .NET 新增墨跡註釋，讓您的 PDF 文件更具互動性和吸引力。這份綜合指南將引導您完成整個過程。
type: docs
weight: 20
url: /zh-hant/net/tutorials/pdf/mastering-annotations/adding-ink-annotations/
---
## 介紹

歡迎來到使用 Aspose.PDF for .NET 進行 PDF 操作的令人興奮的世界！無論您是為了專業用途、個人專案還是介於兩者之間的任何目的而增強文檔，您都來對地方了。在本指南中，我們將探索 Aspose.PDF 的一個實用功能：在 PDF 檔案中新增墨跡註解。此功能非常適合合併手寫筆記或簽名，使您的文件更具互動性和吸引力。

## 先決條件

在我們進入程式碼之前，讓我們確保您已完成所有設定：

1. .NET Framework：請確定您的電腦上安裝了 .NET Framework。 Aspose.PDF 與各種版本無縫協作，包括 .NET Core。
2.  Aspose.PDF 庫：在專案中下載並引用適用於 .NET 的 Aspose.PDF 庫。您可以從以下位置取得最新版本[下載連結](https://releases.aspose.com/pdf/net/).
3. 程式碼編輯器：雖然您可以使用任何程式碼編輯器，但強烈建議使用 Visual Studio，因為它與 .NET 應用程式的使用者友好介面。
4. 基本 C# 知識：熟悉 C# 將幫助您順利瀏覽編碼範例。
5. 開發環境設定：確保您的 IDE 已針對 .NET 專案進行配置，並且您已正確引用 Aspose.PDF 程式庫。

滿足這些先決條件後，您就可以開始為 PDF 添加墨跡註釋了！

## 導入必要的套件

在深入編碼之前，讓我們先導入所需的套件。在 C# 檔案的頂部，加入以下 using 語句：

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
using System.Collections.Generic;
```

這些語句將提供對使用 PDF 註釋所需的所有類別和方法的存取。

讓我們將在 PDF 文件中添加墨跡註釋的過程分解為清晰的步驟。

## 第 1 步：設定文件和目錄

首先，建立文檔和輸出檔案的儲存路徑：

```csharp
string dataDir = "YOUR DATA DIRECTORY";
Document doc = new Document();
```

這裡，`dataDir`指向將保存生成的 PDF 的目錄，我們實例化一個新的`Document`用於編輯的物件。

## 第 2 步：向文件新增頁面

接下來，將頁面新增到新建立的文檔中：

```csharp
Page pdfPage = doc.Pages.Add();
```

每個 PDF 至少需要一頁，因此這一步至關重要。

## 第 3 步：定義繪圖矩形

現在，定義頁面上放置墨跡註解的位置：

```csharp
System.Drawing.Rectangle drect = new System.Drawing.Rectangle
{
    Height = (int)pdfPage.Rect.Height,
    Width = (int)pdfPage.Rect.Width,
    X = 0,
    Y = 0
};
Aspose.Pdf.Rectangle arect = Aspose.Pdf.Rectangle.FromRect(drect);
```

這段程式碼創建了一個`Rectangle`對象，指定頁面上用於墨跡註釋的區域，以適合整個頁面。

## 第四步：準備墨點

接下來，定義構成墨跡註解的點：

```csharp
IList<Point[]> inkList = new List<Point[]>();
Aspose.Pdf.Point[] arrpt = new Aspose.Pdf.Point[3];
inkList.Add(arrpt);
arrpt[0] = new Aspose.Pdf.Point(100, 800);
arrpt[1] = new Aspose.Pdf.Point(200, 800);
arrpt[2] = new Aspose.Pdf.Point(200, 700);
```

此區塊建立一個點數組列表，其中每個數組代表墨跡筆畫的一組點。在這裡，我們定義了形成三角形的三個點，但您可以隨意調整座標以適合您的設計。

## 第 5 步：建立墨跡註釋

定義點後，建立墨跡註解：

```csharp
InkAnnotation ia = new InkAnnotation(pdfPage, arect, inkList)
{
    Title = "Your Title",
    Color = Aspose.Pdf.Color.LightBlue,
    CapStyle = CapStyle.Rounded
};
```

我們實例化`InkAnnotation`對象，傳入頁、矩形和墨點。自訂屬性，例如`Title`, `Color`， 和`CapStyle`以滿足您的需求！

## 步驟6：設定邊框和不透明度

為了使您的註釋脫穎而出，讓我們對其進行樣式設定：

```csharp
Border border = new Border(ia)
{
    Width = 25
};
ia.Border = border;
ia.Opacity = 0.5;
```

此程式碼會新增具有特定寬度的邊框並設定註解的不透明度以使其半透明。

## 第 7 步：將註釋新增至頁面

現在，將註釋新增至 PDF 頁面：

```csharp
pdfPage.Annotations.Add(ia);
```

此行將墨跡註解新增至頁面的註解集合中。

## 第 8 步：儲存文檔

最後，儲存修改後的文件：

```csharp
dataDir = dataDir + "AddInkAnnotation_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nInk annotation added successfully.\nFile saved at " + dataDir);
```

這裡我們修改一下`dataDir`包含輸出檔名並儲存文件。確認訊息將通知您一切順利。

## 結論

恭喜！您已使用 Aspose.PDF for .NET 成功將墨跡註解新增至 PDF 文件。這個簡單而強大的功能可以增強您的文件並使它們具有互動性。無論您是添加簽名、註釋還是塗鴉，墨跡註釋都提供了一種獨特的方式來豐富您的內容。

## 常見問題解答

### 什麼是Aspose.PDF？
Aspose.PDF 是一個用於在 .NET 應用程式中建立、操作和轉換 PDF 文件的程式庫。

### 我可以免費使用 Aspose.PDF 嗎？
是的！ Aspose 提供免費試用版來評估其產品。你可以下載它[這裡](https://releases.aspose.com/).

### 是否可以新增多個墨跡註解？
絕對地！您可以建立多個`InkAnnotation`物件並將它們新增至文件頁面。

### 我在哪裡可以找到更多範例？
查看[文件](https://reference.aspose.com/pdf/net/)取得詳細教學和範例。

### 如果我需要支持，我該怎麼辦？
如果您遇到任何問題，可以透過以下方式尋求協助[支援論壇](https://forum.aspose.com/c/pdf/10).