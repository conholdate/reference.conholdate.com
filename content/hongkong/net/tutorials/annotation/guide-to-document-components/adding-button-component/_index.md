---
title: 使用 GroupDocs.Annotation for .NET 新增按鈕元件
linktitle: 新增按鈕組件
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 新增互動式按鈕元件來提升您的 PDF 文件。這個逐步教程。
type: docs
weight: 10
url: /zh-hant/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## 介紹

在本教學中，我們將引導您完成使用 .NET 的 GroupDocs.Annotation 庫將按鈕元件新增至 PDF 文件的簡單程序。閱讀本指南後，您將能夠透過互動功能增強您的 PDF 文件。

## 先決條件

在開始之前，請確保您已具備以下條件：

1.  GroupDocs.Annotation for .NET：從下列位置下載並安裝 GroupDocs.Annotation for .NET 程式庫[這裡](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：建置合適的開發環境，安裝.NET框架。

## 步驟1：導入必要的命名空間

首先將所需的命名空間匯入到您的專案中：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## 第2步：初始化輸出路徑

定義儲存修改後的 PDF 的輸出路徑：

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第三步：新增按鈕組件

現在，讓我們建立按鈕元件並將其新增至您的 PDF ：

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), //按鈕的位置和大小
        PenColor = 65535,                       //按鈕邊框顏色
        Style = BorderStyle.Dashed,             //邊框樣式
        BorderWidth = 0,                        //邊框寬度
        BorderColor = 0,                        //邊框顏色
        AlternateName = "Name",                 //按鈕的替代名稱
        PartialName = "Partial Name",           //按鈕的部分名稱
        NormalCaption = "Caption",               //按鈕上顯示的文字
        ButtonColor = 16761035,                 //按鈕的背景顏色
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); //將按鈕新增至註釋器
    annotator.Save("result.pdf"); //儲存修改後的PDF
}
```

## 第四步：顯示輸出路徑

最後，通知使用者輸出檔案的保存位置：

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

恭喜！您已使用 GroupDocs.Annotation for .NET 成功將按鈕元件新增至 PDF 文件。

## 結論

在本教學中，我們示範如何使用 GroupDocs.Annotation for .NET 將按鈕元件合併到 PDF 文件中。透過執行這些步驟，您可以顯著增強 PDF 文件的互動性。

## 常見問題解答

### 我可以自訂按鈕的外觀嗎？

絕對地！您可以修改各種屬性，例如尺寸、顏色和樣式以滿足您的要求。

### GroupDocs.Annotation for .NET 是否與所有 PDF 版本相容？

是的，GroupDocs.Annotation for .NET 支援多種 PDF 版本，確保與大多數文件相容。

### 我可以將多個按鈕元件新增到單一 PDF 文件中嗎？

是的，您可以根據需要向 PDF 文件添加任意數量的按鈕元件。

### GroupDocs.Annotation for .NET 支援其他檔案格式嗎？

是的，除了 PDF 之外，它還支援多種文件格式，包括 DOCX、PPTX 和 XLSX。

### 是否有可用於測試目的的試用版？

是的，您可以存取 GroupDocs.Annotation for .NET 的免費試用版：[這裡](https://releases.groupdocs.com/).
