---
title: Reading Custom Properties from PDFs in .NET
linktitle: Reading Custom Properties from PDFs in .NET
second_title: GroupDocs.Metadata .NET API
description: Discover how to efficiently access and manage custom properties from PDF documents using GroupDocs.Metadata for .NET. This comprehensive tutorial provides step-by-step guide.
type: docs
weight: 11
url: /net/pdf-metadata-management/reading-custom-properties-from-pdf/
---
## Introduction

In the world of .NET development, efficiently managing metadata within documents is essential for organizing information and extracting valuable insights. GroupDocs.Metadata for .NET is a comprehensive library that empowers developers to access and manipulate document metadata seamlessly. This tutorial will guide you through the process of extracting custom properties from PDF files using C#. 

## Prerequisites

Before you begin, make sure you have the following:

- A fundamental understanding of the C# programming language.
- Visual Studio installed on your system.
- The GroupDocs.Metadata for .NET library installed. You can download it [here](https://releases.groupdocs.com/metadata/net/).
- A PDF file containing custom properties for testing.

## Step 1: Setting Up Your Project

Start by creating a new C# project in Visual Studio. After setting up the project, you need to import the necessary namespaces. Include the following at the top of your C# file:

```csharp
using System;
using Formats.Document;
using Tagging;
```

## Step 2: Load the PDF Document

Next, you’ll load the PDF document that contains the custom properties. Use the following code snippet to accomplish this:

```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Code for retrieving custom properties will go here.
}
```

Note: Replace `"YourInputFile.pdf"` with the path of your PDF file.

## Step 3: Retrieve and Display Custom Properties

Now that you have loaded the PDF, it’s time to retrieve and display its custom properties. Use the following code block:

```csharp
var customProperties = root.DocumentProperties.FindProperties(p => !p.Tags.Contains(Tags.Document.BuiltIn));
foreach (var property in customProperties)
{
    Console.WriteLine($"{property.Name} = {property.Value}");
}
```

In this code:
- We filter out built-in properties, focusing only on custom ones.
- Each custom property’s name and value are printed to the console, making it easy to view the metadata contained within the PDF.

## Conclusion

In this tutorial, we demonstrated how to utilize GroupDocs.Metadata for .NET to read custom properties from PDF documents using C#. These steps allow you to efficiently incorporate metadata management capabilities into your .NET applications, enhancing your document processing workflow. 

Now, with a solid understanding of how to access custom metadata, you can explore further functionalities offered by the GroupDocs.Metadata library, such as editing and managing metadata.

## FAQ's

### Can I modify custom properties using GroupDocs.Metadata?
Yes, the library provides functionalities to edit, add, or remove custom properties across various document formats.

### Does GroupDocs.Metadata support other file formats besides PDF?
Indeed, GroupDocs.Metadata supports a wide array of file formats, including Word documents, Excel spreadsheets, PowerPoint presentations, images, and more.

### Where can I find further documentation and support for GroupDocs.Metadata?
For comprehensive information, you can refer to the [GroupDocs.Metadata documentation](https://reference.groupdocs.com/metadata/net/). For additional assistance, visit the [GroupDocs.Metadata forum](https://forum.groupdocs.com/c/metadata/14).

### Is there a free trial available for GroupDocs.Metadata?
Yes, you can access a [free trial](https://releases.groupdocs.com/) to explore the features of GroupDocs.Metadata.

### How can I purchase a license for GroupDocs.Metadata?
To acquire a license, please visit the [purchase page](https://purchase.groupdocs.com/buy). Temporary licenses are also available [here](https://purchase.groupdocs.com/temporary-license/).
