---
title: Reading Built-In Properties from PDFs in .NET
linktitle: Reading Built-In Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: Learn how to effectively utilize GroupDocs.Metadata for .NET to read, edit, and manage metadata in PDF files. This tutorial provides a step-by-step guide.
type: docs
weight: 10
url: /net/tutorials/metadata/pdf-metadata-management/reading-built-in-properties-from-pdf/
---
## Introduction
In this tutorial, we'll explore how to use GroupDocs.Metadata for .NET to read and manipulate metadata in PDF files. This powerful library allows developers to access various metadata attributes, such as the author, creation date, and subject, enhancing document management capabilities within applications.

## Prerequisites
Before we begin, ensure you have the following:

- Visual Studio: Make sure it's installed on your system.
- GroupDocs.Metadata for .NET: Download and install it from the [official website](https://releases.groupdocs.com/metadata/net/).
- Basic Knowledge of C#: Familiarity with C# and the .NET framework is recommended.

## Import Namespaces
Start by including the necessary namespaces in your C# project:

```csharp
using System;
using Formats.Document;
```

## Step 1: Load PDF Metadata
To read metadata from a PDF file, load the document and extract its properties using the following code:

```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Access the root package of the PDF file
    var root = metadata.GetRootPackage<PdfRootPackage>();
    
    // Retrieve and display built-in properties
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Access other properties as needed
}
```

With this straightforward approach, you can easily view essential metadata attributes embedded in your PDF files.

## Conclusion
In this tutorial, we've demonstrated how to use GroupDocs.Metadata for .NET to extract and manage built-in properties from PDF files with C#. Integrating this library into your projects will enhance your document metadata handling, making it more efficient and streamlined.

## FAQ's
### Can GroupDocs.Metadata work with other document formats?
Yes, it supports a wide range of formats, including DOCX, XLSX, PPTX, PDF, JPG, PNG, and more.

### Is there a free trial available for GroupDocs.Metadata?
Absolutely! You can access a free trial from the [GroupDocs.Metadata website](https://releases.groupdocs.com/).

### How can I modify metadata properties using GroupDocs.Metadata?
You can modify metadata properties by accessing the relevant document package and setting new values as needed.

### Does GroupDocs.Metadata support .NET Core?
Yes, it is compatible with both .NET Framework and .NET Core.

### Where can I find support or ask questions related to GroupDocs.Metadata?
For support and community discussions, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).
