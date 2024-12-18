---
title: Creating Filled Rectangle
linktitle: Creating Filled Rectangle
second_title: Aspose.PDF for .NET API Reference
description: Unlock the power of PDF manipulation with Aspose.PDF for .NET in this step-by-step tutorial. Learn how to programmatically create visually appealing PDF documents by drawing filled rectangles.
type: docs
weight: 50
url: /net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introduction

Have you ever wanted to create visually stunning PDFs programmatically? If so, you’re in the right place! In this tutorial, we’ll explore Aspose.PDF for .NET, a powerful library that simplifies PDF document manipulation. Today, we’ll focus on creating a filled rectangle within a PDF file. Whether you’re a seasoned developer or just starting, this guide will walk you through each step in a friendly and engaging manner. So, grab your coding hat, and let’s get started!

## Prerequisites

Before we dive into the code, ensure you have the following:

1. Visual Studio: Install Visual Studio on your machine, as it’s an excellent IDE for .NET development.
2. Aspose.PDF for .NET: Download and install the Aspose.PDF library from [here](https://releases.aspose.com/pdf/net/).
3. Basic Knowledge of C#: Familiarity with C# programming will help you understand the code snippets better.

## Step 1: Create a New Project

1. Open Visual Studio and create a new Console Application project.
2. Name your project appropriately.

## Step 2: Add Aspose.PDF Reference

1. Right-click on your project in the Solution Explorer.
2. Select Manage NuGet Packages.
3. Search for Aspose.PDF and install the latest version.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Now that we have everything set up, let’s dive into the code!

## Step 3: Set Up Your Document Directory

Specify the path where your PDF will be saved:

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path on your machine where you want to save the PDF.

## Step 4: Create a Document Instance

Initialize a new PDF document:

```csharp
// Create Document instance
Document doc = new Document();
```

## Step 5: Add a Page to the Document

Every PDF needs at least one page. Let’s add one:

```csharp
// Add page to pages collection of PDF file
Page page = doc.Pages.Add();
```

## Step 6: Create a Graph Instance

A `Graph` instance acts as a canvas for drawing shapes:

```csharp
// Create Graph instance
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Step 7: Add the Graph to the Page

Attach the graph to the page:

```csharp
// Add graph object to paragraphs collection of page instance
page.Paragraphs.Add(graph);
```

## Step 8: Create a Rectangle Instance

Define the rectangle’s position and size:

```csharp
// Create Rectangle instance
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Step 9: Specify the Fill Color

Choose a color for your rectangle. For this example, we’ll use red:

```csharp
// Specify fill color for Graph object
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Step 10: Add the Rectangle to the Graph

Add the rectangle to the graph:

```csharp
// Add rectangle object to shapes collection of Graph object
graph.Shapes.Add(rect);
```

## Step 11: Save the PDF Document

Finally, save your document to the specified directory:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Save PDF file
doc.Save(dataDir);
```

## Step 12: Confirmation Message

Print a confirmation message to indicate success:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusion

Congratulations! You’ve successfully created a filled rectangle in a PDF document using Aspose.PDF for .NET. This powerful library opens up a world of possibilities for PDF manipulation, allowing you to generate stunning documents programmatically. Whether you’re creating reports, invoices, or any other type of PDF, Aspose.PDF has got you covered.

## FAQ's

### What is Aspose.PDF for .NET?
Aspose.PDF for .NET is a library that allows developers to create, manipulate, and convert PDF documents programmatically.

### Can I use Aspose.PDF for free?
Yes, Aspose offers a free trial version that you can use to explore the library's features. You can download it [here](https://releases.aspose.com/).

### Is there a way to get support for Aspose.PDF?
Absolutely! You can get support through the Aspose forum [here](https://forum.aspose.com/c/pdf/10).

### How can I purchase Aspose.PDF?
You can buy Aspose.PDF by visiting the purchase page [here](https://purchase.aspose.com/buy).

### What types of shapes can I create with Aspose.PDF?
You can create various shapes, including rectangles, circles, lines, and more, using the Aspose.PDF library.
