---
title: Sign Documents with Custom Images Using GroupDocs.Signature
linktitle: Sign Documents with Custom Images
second_title: GroupDocs.Signature .NET API
description: Discover how to enhance the authenticity and security of your documents by signing them with custom images using GroupDocs.Signature for .NET. This step-by-step tutorial covers everything from loading a document.
type: docs
weight: 13
url: /net/tutorials/signature/master-advanced-sign-techniques/sign-documents-with-custom-image/
---
## Introduction

In this tutorial, you'll learn how to use GroupDocs.Signature for .NET to sign documents with images. Document signing enhances the authenticity and security of your files, ensuring they are tamper-proof and legally binding. By integrating document signing functionality into your .NET applications, you can streamline your workflows significantly.

## Prerequisites

Before diving into the tutorial, ensure you have the following:

1. GroupDocs.Signature for .NET: Download and install GroupDocs.Signature for .NET from the [website](https://releases.groupdocs.com/signature/net/).
2. .NET Development Environment: Set up a working environment for .NET development.

## Import Namespaces

To access the required classes and methods, begin by importing the necessary namespaces in your project:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Step 1: Load the Document

Specify the path to the document you want to sign. For example, to load a PDF file:

```csharp
string filePath = "sample.pdf";
```

## Step 2: Specify Signature Image

Define the path to the signature image that you intend to use:

```csharp
string imagePath = "signature_handwrite.jpg";
```

## Step 3: Set Output File Path

Determine where you want to save the signed document:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithImage", "SignedDocument.pdf");
```

## Step 4: Initialize the Signature Object

Create an instance of the `Signature` class, passing in the document file path:

```csharp
using (Signature signature = new Signature(filePath))
{
    // Additional code will go here
}
```

## Step 5: Configure Image Signing Options

Set the options for signing the document. Here, you can specify the position of the signature and whether it should appear on all pages:

```csharp
ImageSignOptions options = new ImageSignOptions(imagePath)
{
    Left = 50,   // Horizontal position
    Top = 50,    // Vertical position
    AllPages = true // Sign on all pages
};
```

## Step 6: Sign the Document

Utilize the configured options to sign the document:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
```

## Step 7: Display the Result

Finally, inform the user about the success of the signing process, including the location of the signed document:

```csharp
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Conclusion

In this tutorial, we covered how to sign documents using images in .NET applications with GroupDocs.Signature for .NET. Document signing is essential for maintaining the authenticity and security of your files, significantly enhancing your document management capabilities.

## FAQ's

### Can I use multiple signature images in a single document?

Yes, you can sign a document using multiple images. Simply repeat the signing process for each image as needed.

### Is GroupDocs.Signature for .NET compatible with all document types?

GroupDocs.Signature for .NET supports a variety of document formats, including PDF, Word, Excel, and more.

### Can I customize the appearance of the signature?

Absolutely! You can adjust various aspects of the signature's appearance, such as size, position, transparency, and more.

### Is a trial version available for testing?

Yes, you can download a free trial version from the website to explore its functionality before committing to a purchase.

### How can I obtain technical support for GroupDocs.Signature for .NET?

For technical assistance, visit the [GroupDocs.Signature forum](https://forum.groupdocs.com/c/signature/13).
