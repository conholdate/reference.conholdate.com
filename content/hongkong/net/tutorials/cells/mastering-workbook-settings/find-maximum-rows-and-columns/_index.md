---
title: 尋找 XLS 和 XLSX 格式的最大行數和列數
linktitle: 尋找 XLS 和 XLSX 格式的最大行數和列數
second_title: Aspose.Cells .NET Excel 處理 API
description: 了解如何利用 Aspose.Cells for .NET 函式庫在 Excel 中高效管理大型資料集。本指南提供了一種逐步方法來確定 XLS 和 XLSX 檔案格式支援的最大行數和列數。
type: docs
weight: 11
url: /zh-hant/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## 介紹

在 Excel 中管理大型資料集可能具有挑戰性，特別是考慮到各種文件格式的限制。本教學將指導您使用 Aspose.Cells for .NET 函式庫來確定 XLS (Excel 97-2003) 和 XLSX（Excel 2007 及更高版本）格式支援的最大行數和列數。最後，您將能夠有效率地處理與 Excel 相關的任務。

## 先決條件

在開始之前，請確保您具備以下條件：

1. [.NET框架](https://dotnet.microsoft.com/en-us/download)或者[.NET核心](https://dotnet.microsoft.com/en-us/download)安裝在您的系統上。
2. [Aspose.Cells for .NET](https://releases.aspose.com/cells/net/)下載並在您的專案中引用的庫（您也可以透過安裝它[努格特](https://www.nuget.org/packages/Aspose.Cells/)）。

## 導入所需的套件

在 C# 檔案頂部新增以下 using 語句，以從 Aspose.Cells 庫匯入必要的套件：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 第 1 步：XLS 格式的最大行數和列數

我們首先查找 XLS 格式支援的最大行數和列數。

```csharp
//列印有關 XLS 格式的消息。
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

//建立 XLS 格式的工作簿。
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

//檢索最大行數和列數。
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

//顯示結果。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. 列印一條訊息以表示我們正在使用 XLS 格式。
2. 創建一個`Workbook` XLS 格式的實例使用`FileFormatType.Excel97To2003`.
3. 取得最大行數和列數`wb.Settings.MaxRow`和`wb.Settings.MaxColumn`，加 1，因為它們是從零開始的。
4. 將最大行數和列數輸出到控制台。

## 步驟 2：XLSX 格式的最大行數和列數

接下來，我們將探討 XLSX 格式支援的最大行數和列數。

```csharp
//列印有關 XLSX 格式的消息。
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

//建立 XLSX 格式的工作簿。
wb = new Workbook(FileFormatType.Xlsx);

//檢索最大行數和列數。
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

//顯示結果。
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. 列印一條訊息，表示我們正在使用 XLSX 格式。
2. 創建一個`Workbook` XLSX 格式的實例使用`FileFormatType.Xlsx`.
3. 像以前一樣檢索並輸出最大行數和列數。

## 第 3 步：顯示成功訊息

執行完步驟後，我們就表明成功了。

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## 結論

在本教學中，您學習如何使用 Aspose.Cells for .NET 函式庫來尋找 XLS 和 XLSX 檔案格式支援的最大行數和列數。了解這些限制對於有效的 Excel 資料管理至關重要，確保您的資料集符合格式功能。

## 常見問題解答

### XLS 格式支援的最大行數是多少？
XLS 格式支援的最大行數為 65,536。

### XLS 格式支援的最大列數是多少？
XLS 格式支援的最大列數為 256。

### XLSX 格式支援的最大行數是多少？
XLSX 格式支援的最大行數為 1,048,576。

### XLSX 格式支援的最大列數是多少？
XLSX 格式支援的最大列數為 16,384。

### 我可以將 Aspose.Cells for .NET 函式庫與其他 Excel 檔案格式一起使用嗎？
是的，Aspose.Cells for .NET 支援各種檔案格式，包括 XLS、XLSX、ODS 等。檢查[文件](https://reference.aspose.com/cells/net/)有關支援的特性和功能的詳細資訊。