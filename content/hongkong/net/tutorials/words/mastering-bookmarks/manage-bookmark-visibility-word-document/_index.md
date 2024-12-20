---
title: 管理 Word 文件中的書籤可見性
linktitle: 管理 Word 文件中的書籤可見性
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 熟練地控制 Word 文件中內容的可見性。本逐步指南。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## 介紹

您準備好使用 Aspose.Words for .NET 提升您的文件操作技能了嗎？無論您是經驗豐富的自動化文件任務開發人員，還是好奇的探索 Word 文件程式控制的個人，本指南都是為您量身定制的。今天，我們將深入研究如何在Word文件中根據書籤顯示和隱藏內容。讓我們開始吧！

## 先決條件

在我們深入之前，請確保您具備以下條件：

1. Visual Studio：與 .NET 相容的任何版本。
2. Aspose.Words for .NET：下載[這裡](https://releases.aspose.com/words/net/).
3. 基本 C# 知識：熟悉編寫簡單的 C# 程式就足夠了。
4. 範例 Word 文件：準備一個包含本教學書籤的 Word 文件（例如「Bookmarks.docx」）。

### 建立一個新項目

1. 開啟 Visual Studio 並建立一個新的控制台應用程式 (.NET Core) 專案。將其命名為“BookmarkVisibilityManager”。

### 安裝 Aspose.Words for .NET

透過 NuGet Package Manager 將 Aspose.Words 加入到您的專案中：

1. 導覽至工具 > NuGet 套件管理器 > 管理解決方案的 NuGet 套件。
2. 搜尋“Aspose.Words”。
3. 安裝軟體包。

設定好項目後，讓我們繼續載入文件。

## 導入命名空間

首先導入必要的命名空間。它們提供了使用 Aspose.Words 操作 Word 文件所需的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## 第 1 步：載入文檔

要操作Word文檔，我們需要先載入它。具體做法如下：

```csharp
//定義文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

此程式碼片段設定文檔目錄的路徑並將文檔載入到`Document`目的。

## 步驟 2：顯示/隱藏 新增書籤的內容

現在，讓我們建立一個方法來根據書籤切換內容的可見性。我們將呼叫這個方法`ShowHideBookmarkedContent`.

下面是方法的實作：

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

- 書籤檢索：`Bookmark bm = doc.Range.Bookmarks[bookmarkName];`取得指定的書籤。
- 節點遍歷：我們遍歷書籤內的節點。
- 可見性切換：對於每個`Run`節點（代表一段文字），我們設定它的`Hidden`財產基於`isHidden`範圍。

## 第三步：應用此方法

現在我們已經準備好了方法，讓我們用它來顯示或隱藏特定書籤中的內容：

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); //隱藏「MyBookmark1」中的內容
```

此行將隱藏與名為「MyBookmark1」的書籤關聯的內容。

## 第 4 步：儲存文檔

完成變更後，請不要忘記儲存修改後的文件：

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

這將保存具有更新的可見性設定的文件。

## 結論

恭喜！您已經成功學習如何使用 Aspose.Words for .NET 在 Word 文件中顯示和隱藏新增書籤的內容。這個強大的庫簡化了文件操作，使其成為自動化報告、建立範本或試驗 Word 文件的理想選擇。快樂編碼！

## 常見問題解答

### 我可以一次切換多個書籤嗎？
是的，只需致電`ShowHideBookmarkedContent`您想要切換的每個書籤的方法。

### 隱藏內容會影響文件的結構嗎？
不會，隱藏內容只會影響其可見性；文檔中的內容保持不變。

### 我可以將此方法用於其他類型的內容嗎？
該方法是專門為文本運行而設計的。對於其他內容類型，您需要相應地調整節點遍歷邏輯。

### Aspose.Words for .NET 是免費的嗎？
 Aspose.Words 提供免費試用[這裡](https://releases.aspose.com/)，但生產使用需要完整的許可證。您可以購買[這裡](https://purchase.aspose.com/buy).

### 如果遇到問題，我該如何獲得支援？
如需支持，請造訪 Aspose 社群論壇[這裡](https://forum.aspose.com/c/words/8).