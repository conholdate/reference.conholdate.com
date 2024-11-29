---
title: 使用 GroupDocs.Signature 對具有元資料的圖像進行簽署的指南
linktitle: 使用元資料對影像進行簽署的指南
second_title: GroupDocs.Signature .NET API
description: 了解如何使用 GroupDocs.Signature 在 .NET 應用程式中使用元資料有效地對影像進行簽署。本逐步教學涵蓋了從安裝到實施的所有內容，使您能夠輕鬆地使用元資料簽章增強文件。
type: docs
weight: 10
url: /zh-hant/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## 介紹

GroupDocs.Signature for .NET 是一個功能強大的程式庫，可讓開發人員使用元資料有效地對影像進行簽署。本教學將逐步指導您完成流程。

## 先決條件

在開始之前，請確保您具備以下條件：

1. 適用於 .NET 的 GroupDocs.Signature：在 .NET 專案中安裝 GroupDocs.Signature 套件。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/signature/net/).
2. 影像檔案：準備要使用元資料簽署的影像檔案。

## 導入必要的命名空間

在您的 C# 程式碼中，匯入以下命名空間：

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 第 1 步：載入圖片文件

首先指定影像檔案的路徑和簽名影像的輸出目錄：

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## 第 2 步：建立元資料簽名

接下來，建立元資料簽名並將其新增至簽名選項：

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; //元資料的起始 ID
    MetadataSignOptions options = new MetadataSignOptions();

    //新增各種類型的元資料簽名
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) //字串值
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          //日期時間值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                //整數值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              //雙倍價值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              //十進制值
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             //浮動值

    //簽署文件並儲存結果
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## 結論

在本教學中，您學習如何使用 GroupDocs.Signature for .NET 使用元資料對影像進行簽署。透過執行這些步驟，您可以輕鬆地將元資料簽章新增至 .NET 應用程式中，從而增強影像的功能和完整性。

## 常見問題解答

### 我可以使用 GroupDocs.Signature for .NET 使用元資料簽署多個映像嗎？
是的，您可以透過迭代每個圖像檔案並應用元資料簽名來簽署多個圖像。

### 是否有適用於 .NET 的 GroupDocs.Signature 試用版？
是的，您可以從以下位置下載試用版[這裡](https://releases.groupdocs.com/).

### GroupDocs.Signature for .NET 是否支援圖像以外的其他檔案格式？
絕對地！ GroupDocs.Signature 支援多種格式，包括 PDF、Word、Excel 等。

### 我可以自訂元資料簽章的外觀嗎？
是的，您可以自訂元資料簽名的字體大小、顏色和位置等方面。

### 在哪裡可以獲得對 .NET 的 GroupDocs.Signature 的支援？
如需支持，請造訪 GroupDocs.Signature 論壇[這裡](https://forum.groupdocs.com/c/signature/13).