---
title: 將複選框元件新增至 PDF 文檔
linktitle: 將複選框元件新增至 PDF 文檔
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET SDK 新增互動式複選框元件來豐富您的 PDF 文件。這個綜合教程提供了清晰的逐步指南。
type: docs
weight: 11
url: /zh-hant/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## 介紹

在本教學中，我們將引導您完成使用 GroupDocs.Annotation for .NET SDK 將複選框元件新增至 PDF 文件的過程。此功能可讓您使用互動式元素增強 PDF 文檔，使其對使用者更具吸引力。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  GroupDocs.Annotation for .NET SDK：從以下位置下載[這裡](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：在您的電腦上設定 .NET 開發環境。

## 第 1 步：匯入所需的命名空間

首先，在專案中包含必要的命名空間：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## 步驟2：定義輸出路徑

指定修改後的 PDF 文件的儲存位置：

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 3 步：初始化註釋器

建立一個實例`Annotator`包含輸入 PDF 文件路徑的類別：

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## 第四步：建立複選框組件

現在，讓我們建立並自訂複選框元件：

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), //定義位置和大小
    PenColor = 65535, //設定顏色（在本例中為黃色）
    Style = BoxStyle.Star, //選擇複選框的樣式
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## 第 5 步：將複選框新增至文件中

將已建立的複選框組件新增至 PDF 中：

```csharp
annotator.Add(checkBox);
```

## 步驟6：儲存修改後的文檔

儲存更新的 PDF 文檔，並包含複選框：

```csharp
annotator.Save("result.pdf");
```

## 第7步：顯示輸出路徑

最後，通知使用者修改後的文件保存在哪裡：

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

在本教學課程中，我們使用 GroupDocs.Annotation for .NET 成功將複選框元件新增至 PDF 文件中。此功能可讓您建立互動式 PDF，從而增強使用者體驗和參與度。

## 常見問題解答

### 我可以自訂複選框的外觀嗎？

絕對地！您可以修改各種屬性，例如顏色、樣式和尺寸，以滿足您的特定需求。

### GroupDocs.Annotation for .NET 適合商業用途嗎？

是的，GroupDocs.Annotation for .NET 為企業提供商業授權。

### 可以在購買前試用 GroupDocs.Annotation for .NET 嗎？

是的，可以免費試用。您可以訪問它[這裡](https://releases.groupdocs.com/).

### 在哪裡可以找到對 GroupDocs.Annotation for .NET 的支援？

支援和其他資源可在[集團文檔論壇](https://forum.groupdocs.com/c/annotation/10).

### 我需要臨時許可證才能進行測試嗎？

您可以從以下位置取得臨時測試許可證[這裡](https://purchase.groupdocs.com/temporary-license/).