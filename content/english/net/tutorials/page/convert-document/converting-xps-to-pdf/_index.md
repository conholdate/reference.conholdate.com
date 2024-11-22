---
title: Converting XPS to PDF with Aspose.Page for .NET
linktitle: Converting XPS to PDF
second_title: Aspose.Page .NET API
description: Discover how to seamlessly convert XPS (XML Paper Specification) documents to PDF (Portable Document Format) using the powerful Aspose.Page for .NET library.
type: docs
weight: 11
url: /net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introduction

In this tutorial, we’ll explore how to convert XPS (XML Paper Specification) documents to PDF (Portable Document Format) using the versatile Aspose.Page for .NET library. This powerful library simplifies document conversion and offers various customization options, making it an excellent choice for developers.

## Prerequisites

Before we begin, ensure you have the following in place:

- Aspose.Page for .NET Library: Download and install the Aspose.Page for .NET library from the [Aspose.Page documentation](https://reference.aspose.com/page/net/).
  
- Development Environment: Set up a .NET development environment using Visual Studio or another compatible IDE.

- XPS Document: Have the XPS file you wish to convert ready, stored in a designated directory.

## Step 1: Import Required Namespaces

Start by importing the necessary namespace to access the Aspose.Page functionalities:

```csharp
using Aspose.Page.XPS;
```

## Step 2: Initialize Document Directory

Define the directory path where your documents are stored:

```csharp
string dataDir = "Your Document Directory";
```

Make sure to replace `"Your Document Directory"` with the actual path to the directory containing your XPS document.

### Step 3: Open PDF and XPS Streams

Next, initialize streams for both the input XPS file and output PDF file:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Ensure you have the correct path set for your files.

### Step 4: Load the XPS Document

Now, load your XPS document using the Aspose.Page library:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Step 5: Configure PDF Save Options

Set up the save options for your PDF, including image quality and compression parameters:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Set the JPEG quality level
    ImageCompression = PdfImageCompression.Jpeg, // Use JPEG compression for images
    TextCompression = PdfTextCompression.Flate, // Apply Flate compression for text
    PageNumbers = new int[] { 1, 2, 6 } // Specify page numbers to include
};
```

Feel free to adjust these parameters according to your requirements.

### Step 6: Create the PDF Rendering Device

Create a rendering device for the PDF format:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Step 7: Save the Document as PDF

Finally, save the XPS document to PDF using the specified device and options:

```csharp
document.Save(device, options);
```

## Conclusion

Congratulations! You have successfully converted an XPS document to PDF using Aspose.Page for .NET. This library not only simplifies document conversion but also offers extensive capabilities for handling various formats.

## FAQ's

### Can I convert multiple XPS files into a single PDF?

Absolutely! You can iterate through multiple XPS files and merge them into a single PDF document following the same conversion steps.

### What other output formats does Aspose.Page for .NET support?

In addition to PDF, Aspose.Page for .NET supports a range of formats, including TIFF, JPEG, and PNG.

### How can I customize the appearance of the converted PDF?

You can adjust the parameters in the `PdfSaveOptions` object, such as JPEG quality and compression settings, to achieve your desired appearance.

### Is there a trial version available for Aspose.Page for .NET?

Yes, you can try out Aspose.Page for .NET with a free trial available [here](https://releases.aspose.com/).

### Where can I find community support for Aspose.Page for .NET?

For community discussions and support, visit the [Aspose.Page forum](https://forum.aspose.com/c/page/39).
