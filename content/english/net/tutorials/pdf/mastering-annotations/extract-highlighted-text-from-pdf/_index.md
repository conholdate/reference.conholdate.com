---
title: Extract Highlighted Text from PDFs Using Aspose.PDF for .NET
linktitle: Extract Highlighted Text from PDFs Using Aspose.PDF for .NET
second_title: Aspose.PDF for .NET API Reference
description: Unlock the potential of your PDF documents by learning how to extract highlighted text with Aspose.PDF for .NET. This comprehensive guide walks you through each step, from setup to implementation.
type: docs
weight: 60
url: /net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Introduction

When working with PDF files, extracting highlighted text can be essential for data analysis, content review, or organizing notes. If you're using Aspose.PDF for .NET, you're in luck. This tutorial provides clear, step-by-step instructions on how to efficiently extract highlighted text from a PDF document.

## Prerequisites

Before you start, ensure you have the following in place:

- Aspose.PDF for .NET Library: Download the library from the [release page](https://releases.aspose.com/pdf/net/).
- Development Environment: A working environment like Visual Studio.
- Basic Knowledge of C#: Familiarity with C# and object-oriented programming is necessary.
- Aspose License: While you can start with a free trial, a [temporary license](https://purchase.aspose.com/temporary-license/) or a full license from [here](https://purchase.aspose.com/buy) will provide unrestricted access.

## Import Necessary Namespaces

Start by importing the required namespaces in your C# project:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

These namespaces provide access to the classes and methods needed for handling PDF documents and annotations.

## Step 1: Set Up Your Project Directory

Specify the directory where your PDF file is located:

```csharp
// Path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Make sure to replace the path with the actual directory of your PDF file.

## Step 2: Load the PDF Document

Load the PDF document with the following code:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Ensure that the specified file exists in the given directory.

## Step 3: Access Annotations on the Page

To access the annotations, loop through the annotations on your desired page (in this case, the first page):

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

This code filters for `TextMarkupAnnotation` types, which represent highlights.

## Step 4: Extract the Highlighted Text

Now, extract and display the text from the highlighted annotations:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

This retrieves all marked text fragments associated with the highlight and prints them to the console.

## Conclusion

Extracting highlighted text from a PDF using Aspose.PDF for .NET is straightforward and can significantly enhance your document handling process. By following the steps outlined above, you can efficiently gather highlighted text for various applications, such as report preparation or data analysis.

## FAQ's

### Can I extract other types of annotations?
Yes, simply adjust the `if` condition to include different annotation types like `TextAnnotation` or `StampAnnotation`.

### How can I extract highlighted text from all PDF pages?
You can loop through all pages using:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Is a license necessary for Aspose.PDF for .NET?
A free trial is available, but consider a [temporary license](https://purchase.aspose.com/temporary-license/) or a full license for complete access.

### Can I save the extracted text to a file?
Absolutely! You can modify the code to write extracted text to a text file.

### Does Aspose.PDF support other platforms?
Yes, Aspose.PDF also supports Java and other platforms, providing similar functionality.
