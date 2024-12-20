---
title: Creating Local Hyperlink In PDF File
linktitle: Creating Local Hyperlink In PDF File
second_title: Aspose.PDF for .NET API Reference
description: Discover how to improve navigation in your PDF documents by creating local hyperlinks using Aspose.PDF for .NET. This step-by-step tutorial walks you through the entire process.
type: docs
weight: 40
url: /net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Introduction

In this guide, we’ll walk you through the process of creating local hyperlinks in a PDF file using Aspose.PDF for .NET. We'll break down each step clearly, ensuring that even if you're new to PDF manipulation, you’ll be able to follow along effortlessly.

## Prerequisites

Before diving into the code, ensure you have the following:

1. Visual Studio: Download it from the [Visual Studio website](https://visualstudio.microsoft.com/).
2. Aspose.PDF for .NET: Download the library via the [Aspose website](https://releases.aspose.com/pdf/net/). This library provides a rich set of features for PDF manipulation.
3. Basic Knowledge of C#: Familiarity with C# programming will help, but don’t worry; we’ll explain the code line by line.
4. .NET Framework: Ensure you have the .NET framework installed on your machine. Check the requirements on the Aspose.PDF [documentation](https://reference.aspose.com/pdf/net/).

With these prerequisites in place, you’re ready to learn how to create local hyperlinks in your PDF documents!

## Importing Required Packages

Now that you’re all set up, it’s time to import the necessary packages into your C# project.

### Open Your Project

Open your existing .NET project or create a new one in Visual Studio. If you're starting fresh, select “Create a new project” from the startup screen.

### Add Reference to Aspose.PDF

Right-click on "Dependencies" in your project folder in Solution Explorer. Select "Manage NuGet Packages," search for `Aspose.PDF`, and install the latest version available. This will bring all the tools you need for creating and manipulating PDFs.

### Import Namespaces

At the top of your .cs file, add the following using directives:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

These directives allow you to access the library’s features seamlessly.

Let’s break down the process of creating local hyperlinks into simple steps.

## Step 1: Set Up Document Instance

Create a new instance of the `Document` class, representing the PDF file you will work with.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Set your document directory
Document doc = new Document(); // Create Document instance
```

Replace `"YOUR_DOCUMENT_DIRECTORY"` with the actual path on your system where the PDF will be saved.

## Step 2: Add a Page to the Document

Next, add a page to your PDF document.

```csharp
Page page = doc.Pages.Add(); // Add a new page
```

This line adds a new page to the document, where all your content will be placed.

## Step 3: Create a Text Fragment

Now, let’s create a piece of text that will act as a clickable link.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Create a text fragment
```

This `TextFragment` will display the text that users can click on.

## Step 4: Create Local Hyperlink

Now, create a local hyperlink that points to page 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Create a local hyperlink
link.TargetPageNumber = 7; // Set the target page for the link
text.Hyperlink = link; // Set the hyperlink for the text fragment
```

The `LocalHyperlink` class allows you to specify the target page number for the hyperlink.

## Step 5: Add the Text Fragment to the Page

Add the clickable text to the page you created.

```csharp
page.Paragraphs.Add(text); // Add the text fragment to the page
```

This line adds your text to the page’s collection of paragraphs.

## Step 6: Create Another Text Fragment (Optional)

Let’s add another hyperlink to navigate back to page 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Create a new text fragment
textBack.IsInNewPage = true; // Indicate it should be on a new page
```

## Step 7: Set Up the Second Local Hyperlink

Create another local hyperlink for page 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Create another local hyperlink
linkBack.TargetPageNumber = 1; // Set target page for the second hyperlink
textBack.Hyperlink = linkBack; // Set the hyperlink for the second text fragment
```

## Step 8: Add the Second Text Fragment to the New Page

Add the second text fragment to its page.

```csharp
Page newPage = doc.Pages.Add(); // Add a new page for the second link
newPage.Paragraphs.Add(textBack); // Add the text fragment to the new page
```

## Step 9: Save the Document

Finally, save your document.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Specify output file name
doc.Save(dataDir); // Save the updated document
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

This line combines your directory path with the file name, and the `Save()` method saves your document.

## Conclusion

Creating local hyperlinks in PDF files using Aspose.PDF for .NET is a practical feature that enhances navigation and user experience. You now have the knowledge to guide your readers directly to the information they need, making your PDFs more interactive and user-friendly.

## FAQ's

### What is Aspose.PDF for .NET?
Aspose.PDF for .NET is a library that allows developers to create, manipulate, and convert PDF documents programmatically using the .NET framework.

### Can I create hyperlinks to external web pages?
Yes, Aspose.PDF also supports creating hyperlinks to external URLs in addition to local hyperlinks within the PDF.

### Is there a free trial for Aspose.PDF?
Absolutely! You can access the free trial from the [Aspose website](https://releases.aspose.com/).

### What programming languages does Aspose support?
Aspose offers libraries for various programming languages, including Java, C++, and Python, among others.

### How do I obtain support for Aspose products?
You can seek support via the [Aspose Forum](https://forum.aspose.com/c/pdf/10).
