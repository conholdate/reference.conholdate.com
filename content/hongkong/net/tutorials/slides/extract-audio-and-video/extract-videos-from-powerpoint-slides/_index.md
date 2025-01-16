---
title: 使用 Aspose.Slides 從 PowerPoint 幻燈片中提取視頻
linktitle: 從 PowerPoint 幻燈片中提取視頻
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 了解如何使用 Aspose.Slides for .NET 從 PowerPoint 簡報中輕鬆擷取嵌入的影片檔案。這個全面的逐步指南涵蓋了從設定環境到保存提取的影片的所有內容。
type: docs
weight: 14
url: /zh-hant/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## 介紹

Aspose.Slides for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式與 PowerPoint 簡報進行互動。在本指南中，我們將引導您完成使用 Aspose.Slides for .NET 擷取嵌入 PowerPoint 投影片中的影片的過程。 

## 先決條件

在開始之前，請確保您具備以下條件：

-  Aspose.Slides for .NET：從下列位置取得並安裝程式庫[阿斯普斯網站](https://purchase.aspose.com/buy).
- PowerPoint 簡報：準備一個 PowerPoint 文件（例如，`Video.pptx`）與您要提取的影片。

## 必要的命名空間

若要使用 Aspose.Slides for .NET，您需要匯入適當的命名空間。在您的程式碼中包含以下內容：

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## 步驟1：指定文檔目錄

首先，定義 PowerPoint 簡報的路徑：

```csharp
string dataDir = "Your Document Directory";
```

代替`"Your Document Directory"`包含 PowerPoint 檔案的目錄的實際路徑。

## 第 2 步：載入簡報

將 PowerPoint 簡報載入到`Presentation`目的：

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

這會初始化`Presentation`物件與您指定的 PowerPoint 檔案。

## 第 3 步：迭代投影片和形狀

接下來，循環瀏覽簡報中的每張投影片並檢查影片幀：

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            //繼續提取視頻
        }
    }
}
```

## 第四步：擷取影片數據

找到視訊幀後，提取其屬性和二進位資料：

```csharp
IVideoFrame vf = (IVideoFrame)shape;  //將形狀儲存為視訊幀
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

//取得檔案副檔名
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## 第5步：保存視頻

最後將擷取的視訊資料寫入檔案：

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

此程式碼在您指定的目錄中建立一個新檔案並將視訊資料寫入其中。

## 結論

使用 Aspose.Slides for .NET，從 PowerPoint 投影片中提取影片是一個簡單的過程。透過遵循本指南，您可以輕鬆管理 .NET 應用程式中的多媒體內容，從而豐富使用者體驗和功能。

## 常見問題解答

### 什麼是 Aspose.Slides for .NET？
Aspose.Slides for .NET 是一個設計用於處理 PowerPoint 簡報的程式庫，可讓使用者以程式設計方式建立、編輯和操作簡報檔案。

### 在哪裡可以找到 Aspose.Slides for .NET 的文檔？
您可以存取完整的文檔[這裡](https://reference.aspose.com/slides/net/).

### Aspose.Slides for .NET 可以免費試用嗎？
是的，您可以從以下位置下載免費試用版[這個連結](https://releases.aspose.com/).

### 如何取得 Aspose.Slides for .NET 的臨時授權？
可以申請臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以獲得 Aspose.Slides for .NET 的支援？
可透過以下方式獲得支持[Aspose.Slides 論壇](https://forum.aspose.com/).