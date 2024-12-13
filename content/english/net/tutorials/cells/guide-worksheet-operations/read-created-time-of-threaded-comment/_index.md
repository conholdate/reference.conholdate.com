---
title: Read Created Time of Threaded Comments with Aspose.Cells
linktitle: Read Created Time of Threaded Comments with Aspose.Cells
second_title: Aspose.Cells .NET Excel Processing API
description: Learn how to easily read the created time of threaded comments in an Excel worksheet using Aspose.Cells for .NET. Follow our detailed guide with step-by-step instructions.
type: docs
weight: 21
url: /net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## Introduction

When working with Excel files, managing comments can be essential for collaboration and feedback tracking. In this guide, we’ll walk you through the process of reading the created time of threaded comments in an Excel worksheet using Aspose.Cells for .NET. This powerful tool provides an efficient way to interact with Excel files, enabling developers to extract detailed information from comments, which is particularly useful for tracking the timing of feedback in collaborative scenarios.

## Prerequisites

Before we begin, it’s important to ensure that your development environment is set up properly to use Aspose.Cells for .NET. Here’s what you’ll need:

1. Aspose.Cells for .NET: You’ll need the Aspose.Cells library installed. You can get the latest version from the [Aspose website](https://releases.aspose.com/cells/net/).
2. IDE: Visual Studio (or any .NET IDE of your choice) to write and execute your code.
3. Basic C# Knowledge: Familiarity with C# programming will make it easier to follow the examples.
4. Excel File: For this tutorial, we’ll use an Excel file named `ThreadedCommentsSample.xlsx`, which includes some threaded comments. Make sure your file contains comments to follow along.

## Importing the Required Packages

To begin with, you need to import the necessary namespaces for working with Aspose.Cells. Open your C# project and add the following using directives at the top of your code file:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

The `Aspose.Cells` namespace allows you to access all the classes and methods required for manipulating Excel files, while `System` is needed for general functionality such as output and exception handling.

## Step 1: Specify the Directory of the Excel File

The first step is to define the path where your Excel file is stored. This path will be used to locate the file programmatically.

```csharp
// Define the directory of the Excel file
string sourceDir = "Your Document Directory";
```

Replace `"C:\\YourDirectory\\"` with the actual path to your file. This ensures that the program knows where to find the `ThreadedCommentsSample.xlsx`.

## Step 2: Load the Workbook

With the directory set, we can now load the Excel workbook. This is done by creating a new `Workbook` object and passing the file path to it.

```csharp
// Load the Excel workbook
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

If the file is not found at the specified path, an exception will be thrown, so ensure the file path is correct before proceeding.

## Step 3: Access the Desired Worksheet

Once the workbook is loaded, you need to access the worksheet that contains the threaded comments. In this example, we’ll retrieve the first worksheet of the workbook.

```csharp
// Access the first worksheet in the workbook
Worksheet worksheet = workbook.Worksheets[0];
```

If your comments are located in a different worksheet, simply modify the index accordingly. For instance, use `Worksheets[1]` for the second worksheet, and so on.

## Step 4: Retrieve Threaded Comments

To retrieve the threaded comments, you’ll need to specify the cell that contains the comments. In this case, we’re focusing on cell `A1`. The method `GetThreadedComments` is used to get all the comments associated with a specific cell.

```csharp
// Get threaded comments from cell A1
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

This will return a collection of threaded comments for cell A1. If no comments exist in the specified cell, the collection will be empty.

## Step 5: Iterate Through the Comments and Extract Created Time

With the threaded comments retrieved, the next step is to iterate through the collection and extract relevant details, including the created time for each comment. We can easily achieve this by looping through the `ThreadedCommentCollection`.

```csharp
// Loop through each threaded comment and display the details
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

This code will output the comment’s content, the author’s name, and the time the comment was created. The `CreatedTime` property returns the timestamp when the comment was originally created.

## Step 6: Display a Confirmation Message

After successfully reading the threaded comments and displaying the information, it’s always a good practice to include a confirmation message in your code. This helps confirm that the process was executed correctly.

```csharp
// Confirmation message
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

This message will be printed to the console once the code execution is complete, confirming that the process ran without errors.

## Conclusion

You’ve now learned how to easily read the created time of threaded comments in an Excel worksheet using Aspose.Cells for .NET. This functionality is invaluable for tracking comments and feedback in collaborative environments, providing essential timestamps for document review processes. By following this guide, you can efficiently extract and utilize comment data in your .NET applications, enhancing your workflow and improving collaboration with team members.

## FAQ's

### What is Aspose.Cells for .NET?

Aspose.Cells for .NET is a comprehensive library that enables developers to create, manipulate, and manage Excel files in .NET applications. It provides robust tools for reading, writing, and modifying Excel files programmatically.

### How can I download Aspose.Cells for .NET?

You can download the latest version of Aspose.Cells for .NET from the [Aspose website](https://releases.aspose.com/cells/net/).

### Is there a free trial available?

Yes, Aspose offers a free trial for Aspose.Cells for .NET. You can download the trial version from the [free trial page](https://releases.aspose.com/).

### Can I access comments from other cells?

Yes, you can access threaded comments from any cell in the worksheet by modifying the cell reference in the `GetThreadedComments` method. Simply change `"A1"` to the desired cell’s reference.

### Where can I get support for Aspose.Cells?

If you need support or have questions, visit the [Aspose forum](https://forum.aspose.com/c/cells/9), where you can find answers or ask for help from the community.
