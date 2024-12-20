---
title: Change PDF Page Orientation
linktitle: Change PDF Page Orientation
second_title: Aspose.PDF for .NET API Reference
description: Discover how to easily adjust the page orientation of PDF files using Aspose.PDF for .NET. This step-by-step guide provides clear instructions on loading, rotating, and saving your documents.
type: docs
weight: 10
url: /net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Introduction

Have you ever encountered a PDF file where the page orientation is all wrong? Whether it's a document that's been scanned incorrectly or one that simply needs a different layout, adjusting the orientation can make a world of difference. Fortunately, Aspose.PDF for .NET offers a powerful and user-friendly way to manipulate PDF files, including changing the orientation of pages. In this guide, we'll walk you through the process step-by-step, whether you want to switch from portrait to landscape or vice versa.

## Prerequisites

Before we dive into the details, make sure you have the following in place:

- Aspose.PDF for .NET: Ensure you have the Aspose.PDF library installed. If you haven't done this yet, you can [download it here](https://releases.aspose.com/pdf/net/).
- A .NET Development Environment: You can use Visual Studio, JetBrains Rider, or any other IDE you prefer for .NET development.
- Basic Knowledge of C#: Familiarity with C# will help you follow along more easily.
- A PDF File: Have a sample PDF file ready for testing. You can create one or download a sample online.

If you're just starting out, consider trying Aspose.PDF with a [free temporary license](https://purchase.aspose.com/temporary-license/) before deciding to [purchase the full version](https://purchase.aspose.com/buy).

## Import Namespaces

To manipulate PDF pages, you'll first need to import the necessary namespaces in your C# project. Add the following lines at the top of your code file:

```csharp
using System.IO;
using Aspose.Pdf;
```

Now that we have everything set up, let’s get started!

## Step 1: Load the PDF Document

The first step is to load the PDF file you want to modify. Use the `Document` class from the Aspose.PDF namespace:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

Make sure to replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your PDF file.

## Step 2: Loop Through Each Page

Next, we’ll loop through each page in the PDF document. This allows us to apply the orientation change to all pages:

```csharp
foreach (Page page in doc.Pages)
{
    // Manipulate each page
}
```

## Step 3: Access the Page’s MediaBox

Each PDF page has a `MediaBox` that defines its boundaries. We need to access this to check the current orientation and make adjustments:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

The `MediaBox` provides the dimensions of the page, including width and height.

## Step 4: Swap Width and Height

To change the page orientation, we’ll swap the width and height values. This adjustment will change the dimensions of the page:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Here, we compute the new dimensions and reposition the lower-left corner (`LLY`) accordingly.

## Step 5: Update the MediaBox and CropBox

Now that we have the new dimensions, we’ll apply these changes to the `MediaBox` and `CropBox` to ensure the page displays correctly:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Step 6: Rotate the Page

To finalize the orientation change, we’ll rotate the page. This is straightforward with Aspose.PDF:

```csharp
page.Rotate = Rotation.on90; // Rotate 90 degrees
```

This line effectively flips the page into the desired orientation.

## Step 7: Save the Output PDF

After modifying the orientation of all pages, save the updated document to a new file:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Make sure to provide a new filename to avoid overwriting the original document.

## Conclusion

And there you have it! Changing the page orientation of a PDF file using Aspose.PDF for .NET is a straightforward process. By loading the document, looping through the pages, updating the MediaBox, and saving the file, you can easily adjust the layout to meet your needs. Whether you're correcting a poorly scanned document or formatting pages for presentation, this guide should help you get the job done efficiently.

## FAQ's

### Can I rotate specific pages instead of all pages in the PDF?  
Yes, you can modify the loop to target specific pages by their index instead of iterating through all pages.

### What is the `MediaBox`?  
The `MediaBox` defines the size and shape of the page in a PDF file, determining where the content is placed.

### Does Aspose.PDF for .NET work with other file formats?  
Yes, Aspose.PDF can handle various file formats, including HTML, XML, XPS, and more.

### Is there a free version of Aspose.PDF for .NET?  
Yes, you can start with a [free trial](https://releases.aspose.com/) or request a [temporary license](https://purchase.aspose.com/temporary-license/).

### Can I undo the changes once saved?  
Once you save the document, the changes are permanent. It's advisable to work on a copy or keep a backup of the original file.
