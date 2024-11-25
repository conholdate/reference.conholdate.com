---
title: Reordering Pages in Documents Using GroupDocs.Viewer for .NET
linktitle: Reordering Pages in Documents
second_title: GroupDocs.Viewer .NET API
description: This comprehensive tutorial guides .NET developers through the process of rearranging pages in various document formats using GroupDocs.Viewer for .NET.
type: docs
weight: 19
url: /net/mastering-render-options/reordering-pages-in-document/
---
## Introduction

In .NET development, efficiently managing and manipulating documents is pivotal. GroupDocs.Viewer for .NET offers an exceptional solution for viewing various document formats directly within your applications. One common task developers face is reordering pages in documents, which can significantly enhance workflows and user experience. This tutorial explores how to reorder pages using GroupDocs.Viewer for .NET.

## Prerequisites

Before you begin, ensure that you have the following set up:

1. Install GroupDocs.Viewer for .NET: Obtain the latest version from the [GroupDocs website](https://releases.groupdocs.com/viewer/net/) and follow the installation instructions.
   
2. Set Up Your Development Environment: Make sure you have Visual Studio or your preferred IDE ready for .NET development.

3. Obtain Sample Documents: Gather some sample documents (PDF, DOCX, etc.) for testing.

## Step 1: Import Necessary Namespaces

Begin by importing the required namespaces in your .NET application.

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Step 2: Specify Output Directory and File Path

Define the directory where you want to save the reordered document and set the output file path.

```csharp
string outputDirectory = "Your Document Directory";
string outputFilePath = Path.Combine(outputDirectory, "output.pdf");
```

## Step 3: Initialize Viewer Object

Create an instance of the `Viewer` class by supplying the path to your input document.

```csharp
using (Viewer viewer = new Viewer("Path_to_Your_Document"))
{
    // Code for reordering pages will go here
}
```

## Step 4: Set PDF Rendering Options

Specify the rendering options for the document, and indicate where the output file will be saved.

```csharp
PdfViewOptions options = new PdfViewOptions(outputFilePath);
```

## Step 5: Define the Order of the Pages

Pass the page numbers in the desired order for rendering. For example, to switch the first and second pages:

```csharp
viewer.View(options, 2, 1); // Reorder as needed
```

## Step 6: Notify User of Successful Rendering

Once the document has been rendered, inform the user that the operation was successful.

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Conclusion

Rearranging pages in documents is straightforward using GroupDocs.Viewer for .NET. By following this step-by-step guide, you can effectively manage document pages within your applications, improving usability and productivity.

## FAQ's

### Can GroupDocs.Viewer for .NET handle multiple document formats?
Yes, it supports a variety of formats, including PDF, DOCX, XLSX, PPTX, and more.

### Is there a free trial available?
Yes, a free trial can be accessed [here](https://releases.groupdocs.com/).

### Do I need a permanent license for development use?
A temporary license is available for testing; however, a permanent license is required for production environments. Temporary licenses can be obtained [here](https://purchase.groupdocs.com/temporary-license/).

### Can I customize the rendered document's appearance?
Absolutely! GroupDocs.Viewer allows various customizations, including page rotation and watermarking.

### Where can I find support for GroupDocs.Viewer for .NET?
For further assistance, visit the [GroupDocs.Viewer forum](https://forum.groupdocs.com/c/viewer/9).
