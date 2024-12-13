---
title: 在 Excel 工作簿之间传输 VBA 用户窗体和宏
linktitle: 在 Excel 工作簿之间传输 VBA 用户窗体和宏
second_title: Aspose.Cells .NET Excel 处理 API
description: 这份全面的指南将帮助您使用 Aspose.Cells for .NET 在工作簿之间传输 VBA 用户表单和宏，释放 Excel 自动化的强大功能。非常适合初学者和经验丰富的开发人员。
type: docs
weight: 11
url: /zh/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## 介绍

欢迎阅读使用 VBA 宏和用户表单增强 Excel 体验的终极指南！在本教程中，我们将探索如何使用强大的 Aspose.Cells for .NET 库将 VBA 宏用户表单设计器从一个工作簿转移到另一个工作簿。无论您是经验丰富的开发人员还是刚刚入门，本分步指南都将为您提供以编程方式处理 Excel 文件的知识。准备好了吗？让我们开始吧！

## 先决条件
在开始编码之前，请确保您已准备好所需的一切：

1. C# 开发环境：C# 开发的工作环境，强烈推荐使用 Visual Studio。
2.  Aspose.Cells for .NET 库：确保将 Aspose.Cells 库集成到您的项目中。您可以轻松[点击下载](https://releases.aspose.com/cells/net/).
3. VBA 和 Excel 宏的基本知识：熟悉 VBA 和 Excel 宏的功能将增强您对本教程的理解。
4. 带有用户表单的 Excel 文件：创建或获取包含用户表单的 Excel 工作簿（最好启用宏，例如`.xlsm`文件）。

## 导入所需包
要利用 Aspose.Cells 提供的功能，请在 C# 文件的顶部包含以下命名空间：

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

这些命名空间将使您能够访问 Aspose.Cells 库中嵌入的强大工具。

## 步骤 1：定义源和输出目录
首先，确定文件的位置：

```csharp
//定义源目录和输出目录
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

将占位符路径替换为存储文件的实际目录。

## 步骤 2：创建空目标工作簿
接下来，创建一个新的工作簿，您将在其中复制用户表单和宏：

```csharp
//创建空的目标工作簿
Workbook target = new Workbook();
```

这将初始化一个空白工作簿，作为即将进行的数据传输的画布。

## 步骤 3：加载模板工作簿
加载包含用户表单和宏的工作簿：

```csharp
//加载包含 VBA-Macro Designer 用户表单的 Excel 文件
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

调整`"sampleDesignerForm.xlsm"`为您的实际文件的名称。

## 步骤 4：将工作表复制到目标工作簿
现在，让我们将工作表从模板复制到目标工作簿：

```csharp
//将所有模板工作表复制到目标工作簿
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        //在目标工作表的单元格 A2 中添加一条消息
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

此代码循环遍历模板中的每个工作表并将其复制到目标工作簿，确保所有数据无缝传输。

## 步骤 5：从模板复制 VBA 宏
接下来，我们将 VBA 宏（包括 UserForm Designer 模块）复制到新的工作簿：

```csharp
//将 VBA 宏设计器用户窗体从模板复制到目标
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        //复制 ThisWorkbook 模块代码
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        //复制其他模块的代码和数据
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            //获取用户表单设计器存储
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            //将设计器存储添加到目标 Vba 项目
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

此代码确保不仅代码而且用户表单设计都被复制，从而保留了宏的功能。

## 步骤 6：保存目标工作簿
完成复制过程后，保存新的工作簿：

```csharp
//保存目标工作簿
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

根据需要修改输出文件名。此步骤将创建包含宏和用户表单的自定义工作簿。

## 步骤 7：确认成功
最后，向控制台打印成功消息：

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

这行简单的话可以让您确信您的流程进展顺利——这是对您辛勤工作的必要确认！

## 结论
恭喜！您已成功学会如何使用 Aspose.Cells for .NET 将 VBA 宏用户表单设计器从一个工作簿复制到另一个工作簿。虽然乍一看似乎很艰巨，但练习将使您精通工作簿操作。请记住，编码是关于实验的，所以不要犹豫，探索 Excel 文件中的不同功能。如果您有任何疑问或需要帮助，Aspose 论坛和文档是极好的支持资源。

## 常见问题解答

### Aspose.Cells 支持哪些版本的 Excel？
Aspose.Cells 支持各种 Excel 格式，包括 XLSX、XLSM、CSV 等。

### 我可以免费使用 Aspose.Cells 吗？
是的！您可以先免费试用一下，以评估该库：[免费试用](https://releases.aspose.com/).

### 我需要 Visual Studio 来运行此代码吗？
虽然由于其用户友好的功能而推荐使用 Visual Studio，但任何支持 .NET 开发的 C# IDE 都可以。

### 在哪里可以找到更多示例和文档？
您可以探索[Aspose.Cells 文档](https://reference.aspose.com/cells/net/)以获取更多示例和深入解释。

### 如何解决使用 Aspose.Cells 时出现的问题？
你应该访问[Aspose 支持论坛](https://forum.aspose.com/c/cells/9)寻求社区和 Aspose 支持人员的帮助。