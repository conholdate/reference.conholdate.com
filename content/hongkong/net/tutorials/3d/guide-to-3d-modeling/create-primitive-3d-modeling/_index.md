---
title: 建立原始 3D 建模
linktitle: 建立原始 3D 建模
second_title: Aspose.3D .NET API
description: 了解如何建立和自訂原始 3D 模型（包括盒子和圓柱體），並輕鬆將它們儲存為 FBX 格式。
type: docs
weight: 10
url: /zh-hant/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## 介紹

歡迎來到使用 Aspose.3D for .NET 的沉浸式 3D 建模世界！在這個綜合教程中，我們將指導您逐步完成創建原始 3D 模型的過程。無論您是經驗豐富的開發人員還是渴望學習的初學者，本指南都將幫助您為您的專案創建視覺上令人驚嘆的 3D 元素。

## 先決條件

在深入研究 3D 建模之前，請確保滿足以下先決條件：

-  Aspose.3D for .NET：從下列位置下載並安裝 Aspose.3D for .NET 函式庫：[下載頁面](https://releases.aspose.com/3d/net/).
  
- .NET開發環境：建置與Aspose.3D相容的環境，例如Visual Studio。

一切準備就緒，讓我們開始我們的 3D 建模冒險吧！

## 導入所需的命名空間

首先匯入必要的命名空間以存取 Aspose.3D 功能：

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

這些命名空間將為您提供操作 3D 模型和保存您的創作所需的工具。

## 第 1 步：初始化場景對象

建立一個新的場景物件作為 3D 模型的畫布：

```csharp
//初始化場景對象
Scene scene = new Scene();
```

該場景將包含您將要建立的原始形狀。

## 第 2 步：建立盒子模型

接下來，讓我們將盒子模型添加到場景中：

```csharp
//創建盒子模型
scene.RootNode.CreateChildNode("box", new Box());
```

您可以自訂盒子的尺寸和屬性，以適應您的創意願景。

## 第 3 步：建立圓柱體模型

現在，透過添加圓柱體來增強場景：

```csharp
//建立圓柱體模型
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

就像盒子一樣，您可以隨意調整圓柱體的參數以獲得您想要的外觀。

## 步驟 4：將場景儲存為 FBX 格式

若要保留 3D 模型，請將其儲存為 FBX 格式：

```csharp
//以 FBX 格式儲存繪圖
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

確保為您的模型選擇適當的輸出目錄和檔案名稱。

## 第 5 步：顯示成功訊息

最後，透過顯示一條訊息來慶祝您的成功：

```csharp
//顯示成功訊息
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

由原始模型組成的 3D 場景現已完成並儲存！

## 結論

恭喜您使用 Aspose.3D for .NET 創建了令人驚嘆的 3D 模型！本教程涵蓋了原始建模的基礎知識，但可能性是無限的。探索有關高級功能和技術的更多信息[文件](https://reference.aspose.com/3d/net/).

## 常見問題解答

### 我可以將 Aspose.3D for .NET 與 .NET 以外的程式語言一起使用嗎？

Aspose.3D主要支援.NET，但也有適用於Java和其他平台的版本。

### 可以免費試用嗎？

是的，您可以透過以下方式嘗試 Aspose.3D 的功能：[免費試用](https://releases.aspose.com/).

### 在哪裡可以找到對 Aspose.3D for .NET 的支援？

如需社區支持，請訪問[Aspose.3D 論壇](https://forum.aspose.com/c/3d/18).

### 我怎麼才能獲得臨時許可證？

您可以申請臨時許可證[這裡](https://purchase.conholdate.com/temporary-license/).

### 有其他可用的教學嗎？

是的！探索更多教學和範例[文件](https://reference.aspose.com/3d/net/).