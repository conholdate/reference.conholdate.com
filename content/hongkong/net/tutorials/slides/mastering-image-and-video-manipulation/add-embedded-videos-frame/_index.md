---
title: 在 .NET 簡報中新增嵌入式視訊框架
linktitle: 在 .NET 簡報中新增嵌入式視訊框架
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 透過學習如何使用 Aspose.Slides for .NET 嵌入影片來釋放簡報的潛力。這個綜合教學將引導您完成整合多媒體元素的逐步流程。
type: docs
weight: 19
url: /zh-hant/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## 介紹

在當今快節奏的演示環境中，整合多媒體元素可以顯著提高參與度和觀眾保留率。 Aspose.Slides for .NET 提供了一個強大的解決方案，用於將視訊幀嵌入到幻燈片中。本教學將逐步引導您完成整個過程，確保從開始到結束都有流暢的體驗。

## 先決條件

在開始之前，請確保您具備以下條件：

-  Aspose.Slides for .NET Library：從以下位置下載並安裝該程式庫：[發布頁面](https://releases.aspose.com/slides/net/).
- 媒體內容：您想要嵌入到簡報中的影片檔案（例如「Wildlife.mp4」）。

## 導入必要的命名空間

首先在 .NET 專案中導入所需的命名空間：

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## 第 1 步：設定您的目錄

確保您的專案包含文件和媒體文件的必要目錄：

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

//如果目錄不存在則建立
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## 第 2 步：實例化演示類

建立一個實例`Presentation`類別來表示您的 PPTX 檔案：

```csharp
using (Presentation pres = new Presentation())
{
    //取得第一張投影片
    ISlide sld = pres.Slides[0];
```

## 第 3 步：嵌入視頻

使用以下程式碼將影片嵌入到您的簡報中：

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## 第 4 步：新增視訊幀

接下來，為投影片添加視訊幀：

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## 步驟 5：配置視訊屬性

設定影片屬性，包括播放模式和音量：

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; //自動播放視頻
vf.Volume = AudioVolumeMode.Loud; //設定音量等級
```

## 第 6 步：儲存您的簡報

最後，將修改後的PPTX檔案儲存到磁碟：

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

您可以對要嵌入簡報中的每個影片重複這些步驟。

## 結論

恭喜！您已使用 Aspose.Slides for .NET 成功將影片影格嵌入到簡報中。這種動態功能可以將您的簡報提升到一個新的水平，透過無縫整合的多媒體來吸引觀眾。

## 常見問題解答

### 我可以在簡報的任何幻燈片中嵌入影片嗎？

是的，您可以透過調整索引來選擇任何幻燈片`pres.Slides[index]`.

### 支援哪些影片格式？

Aspose.Slides支援各種視訊格式，包括MP4、AVI和WMV。

### 我可以自訂視訊畫面的大小和位置嗎？

絕對地！您可以修改其中的參數`AddVideoFrame(x, y, width, height, video)`以滿足您的需求。

### 我可以嵌入的影片數量有限制嗎？

嵌入影片的限制通常取決於簡報軟體的容量。

### 我可以在哪裡尋求進一步的幫助或分享我的經驗？

請隨時訪問[Aspose.Slides 論壇](https://forum.aspose.com/c/slides/11)以獲得社區支持和討論。