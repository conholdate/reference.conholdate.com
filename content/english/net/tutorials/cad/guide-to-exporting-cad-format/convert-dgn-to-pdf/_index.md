---
title: Convert DGN to PDF in Aspose.CAD for .NET
linktitle: Convert DGN to PDF in Aspose.CAD for .NET
second_title: Aspose.CAD .NET - CAD and BIM File Format
description: Learn how to effortlessly convert DGN files to PDF using the powerful Aspose.CAD library for .NET. This step-by-step guide is designed for developers of all levels.
type: docs
weight: 12
url: /net/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Introduction

Navigating the world of CAD files can be challenging, but with Aspose.CAD for .NET, developers can easily manipulate and convert various CAD formats. One common need is converting DGN files to PDFs, which we'll explore step by step in this tutorial.

## Prerequisites

To follow along, ensure you have the following:

- Basic proficiency in C# and the .NET framework.
- Aspose.CAD for .NET library installed. You can download it [here](https://releases.aspose.com/cad/net/).
- A sample DGN file (e.g., Nikon_D90_Camera.dgn). 

## Step 1: Import Required Namespaces

Start by importing the relevant namespaces in your C# project:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Step 2: Load the DGN File

Specify the directory for your DGN file and load it using the following code:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Additional processing will go here...
}
```

## Step 3: Configure Rasterization Options

Next, set up the rasterization options to define how your DGN will be rendered in the PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Adjust the width as needed
    PageHeight = 300, // Adjust the height as needed
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Step 4: Create PDF Options

Define the PDF options, integrating the rasterization settings configured earlier:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Step 5: Save the DGN as a PDF

Finally, save the DGN file as a PDF using the options you've configured:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Conclusion

Congratulations! You've successfully converted a DGN file into a PDF using Aspose.CAD for .NET. This straightforward tutorial guided you through loading the DGN file, setting rasterization options, and saving the output as a PDF.

## FAQ's

### Do I need prior CAD knowledge to use Aspose.CAD?  
Absolutely! Aspose.CAD is designed to simplify complex CAD tasks, making it accessible for all developers, regardless of their CAD knowledge.

### Where can I find more resources and documentation for Aspose.CAD?  
You can explore comprehensive guides and examples in the [Aspose.CAD documentation](https://reference.aspose.com/cad/net/).

### Is there a free trial available for Aspose.CAD?  
Yes, a free trial can be obtained [here](https://releases.aspose.com/).

### How can I get a temporary license for Aspose.CAD?  
You can request temporary licenses [here](https://purchase.aspose.com/temporary-license/).

### Need assistance or have questions?  
Join the conversation in the [Aspose.CAD forum](https://forum.aspose.com/c/cad/19) for community support and inquiries.
