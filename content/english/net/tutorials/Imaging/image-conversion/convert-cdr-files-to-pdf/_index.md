---
title: Convert CorelDRAW (CDR) Files to PDF with Aspose.Imaging in .NET
linktitle: Convert CorelDRAW (CDR) Files to PDF with Aspose.Imaging in .NET
second_title: Aspose.Imaging .NET Image Processing API
description: Learn how to seamlessly convert CorelDRAW (CDR) files to PDF using Aspose.Imaging for .NET in this comprehensive step-by-step guide.
type: docs
weight: 10
url: /net/tutorials/imaging/image-conversion/convert-cdr-files-to-pdf/
---
## Introduction

In graphic design and document processing, converting CorelDRAW (CDR) files to PDF is a common requirement. Aspose.Imaging for .NET provides an efficient way to perform this conversion. This tutorial offers a step-by-step guide, complete with code examples to ensure a smooth process.

## Prerequisites

Before you start, ensure you have the following:

1. Aspose.Imaging for .NET: Download and install it from the [Aspose website](https://releases.aspose.com/imaging/net/).
2. A CDR File: Prepare the CorelDRAW (CDR) file you wish to convert.
3. Development Environment: Have Visual Studio or another .NET development tool set up.

## Step 1: Import Necessary Namespaces

Begin by importing the required namespaces from Aspose.Imaging:

```csharp
using Aspose.Imaging;
using Aspose.Imaging.FileFormats.Cdr;
using Aspose.Imaging.FileFormats.Pdf;
using Aspose.Imaging.ImageOptions;
```

## Step 2: Load the CDR File

Load your CDR file with the following code:

```csharp
string dataDir = "Your Document Directory";
string inputFileName = Path.Combine(dataDir, "YourFile.cdr");

using (var image = (VectorMultipageImage)Image.Load(inputFileName))
{
    // Proceed to the next steps
}
```

## Step 3: Configure Page Rasterization Options

Create options to rasterize each page of the CDR image:

```csharp
var pageOptions = CreatePageOptions<CdrRasterizationOptions>(image.Size);
```

## Step 4: Set Page Size

Define a method to set the rasterization options based on the page size:

```csharp
private static VectorRasterizationOptions CreatePageOptions<TOptions>(Size pageSize) where TOptions : VectorRasterizationOptions, new()
{
    var options = new TOptions { PageSize = pageSize };
    return options;
}
```

## Step 5: Create PDF Options

Set up the PDF options, incorporating your rasterization settings:

```csharp
var options = new PdfOptions
{
    MultiPageOptions = new MultiPageOptions
    {
        PageRasterizationOptions = pageOptions
    }
};
```

## Step 6: Export to PDF

Finally, export the CDR image to a PDF file with the specified options:

```csharp
image.Save(Path.Combine(dataDir, "YourFile.pdf"), options);
```

## Step 7: Clean Up Temporary Files (Optional)

If you want to delete the PDF file after processing, include this line:

```csharp
File.Delete(Path.Combine(dataDir, "YourFile.pdf"));
```

## Conclusion

You’ve now successfully converted a CDR file to PDF using Aspose.Imaging for .NET. This guide streamlines the process, ensuring clarity at each step.

## FAQ's

### What is Aspose.Imaging for .NET?
Aspose.Imaging for .NET is a robust library for processing various image formats, enabling conversion, manipulation, and editing tasks.

### Is a license required for Aspose.Imaging for .NET?
Yes, a license is necessary for full functionality, which can be purchased [here](https://purchase.conholdate.com/buy). A free trial is available [here](https://releases.aspose.com/).

### Can other image formats be converted to PDF using this library?
Yes, Aspose.Imaging for .NET supports the conversion of multiple image formats to PDF.

### Is batch conversion possible?
Absolutely! Aspose.Imaging for .NET can handle batch conversions of numerous image files to PDF.

### Where can I find more documentation and support?
For thorough documentation, visit [Aspose Imaging Documentation](https://reference.aspose.com/imaging/net/). For support, check the [Aspose forums](https://forum.aspose.com/).
