---
title: 文檔文件格式偵測
linktitle: 文檔文件格式偵測
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 無縫偵測和管理各種文件檔案格式。請遵循我們包含實際範例、提示和常見問題的詳細指南。
type: docs
weight: 10
url: /zh-hant/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## 介紹

在當今的數位環境中，有效管理和組織各種文件格式至關重要。 Aspose.Words for .NET 提供了一個強大的解決方案來偵測和處理不同的檔案類型。在本指南中，我們深入研究了檢測文件格式的逐步流程，以確保準確性並節省寶貴的時間。

## 文檔檢測的先決條件

在開始之前，請確保滿足以下要求：

1. Aspose.Words for .NET 函式庫  
   從以下位置下載庫[Aspose Words 發布](https://releases.aspose.com/words/net/)並使用有效的許可證來啟動它。如需臨時許可證，請訪問[申請臨時許可證](https://purchase.aspose.com/temporary-license/).

2. 開發環境  
   使用安裝了 .NET Framework 的 Visual Studio（任何最新版本）。

3. 基本文件設定  
   組織輸入檔案並準備目錄以對偵測到的格式進行排序。

## 導入基本命名空間

在程式開頭包含這些命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

這些導入提供對文件格式檢測所需的類別和方法的存取。

## 第 1 步：初始化有組織輸出的目錄

根據偵測到的格式建立用於儲存檔案的目錄。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

//確保目錄存在
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

這種結構簡化了文件管理。

## 步驟2：檢索文件列表

過濾掉損壞或不支援的文件以簡化處理。

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

過濾後的清單可確保您僅使用有效的文件。

## 第 3 步：偵測文件格式並對其進行分類

循環遍歷每個文件以識別其格式並將其移動到適當的目錄。

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    //輸出檢測格式
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

這`FileFormatUtil.DetectFileFormat`方法是識別文檔特徵的核心。

## 結論

透過利用 Aspose.Words for .NET，偵測文件檔案格式變得輕而易舉。識別和分類各種格式的能力可確保無縫文件管理，從而提高生產力和工作流程效率。

## 常見問題解答

### 檢測文檔格式的主要目的是什麼？  
檢測格式有助於透過針對特定工作流程或應用程式對文件進行分類來簡化文件處理。

### Aspose.Words 支援加密檔案嗎？  
是的，它可以檢測加密並相應地處理加密文件。

### 我可以將此解決方案擴展到其他文件類型嗎？  
是的，您可以修改程式碼以包含其他格式或整合其他 Aspose 程式庫。

### 如何處理未知格式？  
單獨儲存未知格式，以便手動檢查或使用專用工具進一步處理。

### 在哪裡可以找到其他文件？  
參觀[Aspose.Words 文檔](https://reference.aspose.com/words/net/)取得全面的指南和範例。
