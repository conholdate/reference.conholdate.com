---
title: 使用 Aspose.Slides for .NET 在 PowerPoint 中建立群組形狀
linktitle: 使用 Aspose.Slides for .NET 在 PowerPoint 中建立群組形狀
second_title: Aspose.Slides .NET PowerPoint 處理 API
description: 了解如何使用 Aspose.Slides for .NET 建立和管理群組形狀。本綜合指南提供了清晰的逐步說明。
type: docs
weight: 11
url: /zh-hant/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## 介紹

增強 PowerPoint 簡報的視覺吸引力和組織性可以顯著影響觀眾的參與度。實現這一目標的一種有效方法是透過群體形狀。在本教程中，我們將探討如何利用 Aspose.Slides for .NET 在簡報中建立和操作群組形狀。

## 先決條件

在深入學習本教學之前，請確保您具備以下條件：

-  Aspose.Slides for .NET：從下列位置下載並安裝最新版本的 Aspose.Slides 函式庫[阿斯普斯網站](https://releases.aspose.com/slides/net/).
- 開發環境：設定與 .NET 相容的 IDE（例如 Visual Studio）來處理您的專案。
- 基本 C# 知識：熟悉基本 C# 概念。


## 導入必要的命名空間

在您的 C# 專案中，首先包含以下命名空間：

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## 第 1 步：實例化演示類

建立一個實例`Presentation`您將在其中製作幻燈片的課程。指定儲存文檔的目錄：

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    //創建和操作形狀的步驟將在此處
}
```

## 第 2 步：存取第一張投影片

檢索新建立的簡報的第一張投影片：

```csharp
ISlide slide = pres.Slides[0];
```

## 第 3 步：存取形狀集合

取得投影片上的形狀集合：

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## 第 4 步：新增群組形狀

現在是時候為投影片新增群組形狀了：

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## 第 5 步：在群組內新增形狀

您可以使用單一形狀填滿群組形狀，例如矩形：

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); //形狀1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); //形狀2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); //形狀3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); //形狀4
```

## 第 6 步：定義群組形狀的框架

為群組形狀設定框架為其提供了定義的邊界：

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## 第 7 步：儲存簡報

最後，將修改後的簡報儲存到指定目錄：

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## 結論

恭喜！您已使用 Aspose.Slides for .NET 在 PowerPoint 簡報中成功建立了群組形狀。透過以這種方式組織形狀，您可以大大改善內容的視覺佈局和清晰度，使您的簡報更具影響力。

## 常見問題解答

### Aspose.Slides 與最新版本的 .NET 相容嗎？

是的，Aspose.Slides 會定期更新以與最新的 .NET 版本相容。檢查[文件](https://reference.aspose.com/slides/net/)了解最新的相容性詳細資訊。

### 我可以在購買前試用 Aspose.Slides 嗎？

絕對地！您可以下載免費試用版[這裡](https://releases.aspose.com/).

### 在哪裡可以找到 Aspose.Slides 相關查詢的支援？

請造訪 Aspose.Slides[論壇](https://forum.aspose.com/c/slides/11)以獲得社區支持和討論。

### 如何獲得 Aspose.Slides 的臨時許可證？

您可以申請臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以購買 Aspose.Slides 的完整授權？

您可以從以下位置購買許可證[購買頁面](https://purchase.aspose.com/buy).