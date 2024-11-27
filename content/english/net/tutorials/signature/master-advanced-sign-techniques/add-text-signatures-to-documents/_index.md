---
title: Add Text Signatures to Documents Using GroupDocs.Signature
linktitle: Add Text Signatures to Documents
second_title: GroupDocs.Signature .NET API
description: Learn how to sign documents with text using GroupDocs.Signature for .NET. Step-by-step guide for adding text signatures programmatically.
type: docs
weight: 17
url: /net/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Introduction

In today's digital landscape, electronic document signing has become essential for streamlining workflows and saving resources. GroupDocs.Signature for .NET provides a powerful solution for programmatically adding text signatures to various document formats. This tutorial will guide you through the steps to sign a document with text using GroupDocs.Signature for .NET.

## Prerequisites

Before we begin, ensure you have the following:

1. GroupDocs.Signature for .NET: Download and install the library from [here](https://releases.groupdocs.com/signature/net/).
2. Development Environment: Set up your .NET development environment.
3. Document: Prepare the document you want to sign (e.g., PDF, Word).

## Importing Necessary Namespaces

Start by importing the required namespaces into your .NET project:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Step 1: Load the Document

Begin by loading the document you intend to sign:

```csharp
string filePath = "sample.pdf"; // Path to your document
string fileName = Path.GetFileName(filePath);
```

## Step 2: Define the Output File Path

Next, set the output file path where the signed document will be saved:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Step 3: Create Signature Options

Configure the options for your text signature, including the content, position, size, color, and font style:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X position
    Top = 200, // Y position
    Width = 100, // Width of the signature
    Height = 30, // Height of the signature
    ForeColor = Color.Red, // Text color
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Font settings
};
```

## Step 4: Sign the Document

Finally, use GroupDocs.Signature to apply the text signature and save the signed document:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Sign the document
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Conclusion

In this tutorial, we demonstrated how to programmatically add a text signature to a document using GroupDocs.Signature for .NET. By following these steps, you can enhance the security and authenticity of your documents efficiently.

## FAQ's

### Can I customize the appearance of the text signature?
Yes, you can customize various attributes such as color, font, size, and position of the text signature to suit your needs.

### Is GroupDocs.Signature compatible with multiple document formats?
Absolutely! GroupDocs.Signature supports a wide range of formats, including PDF, Word, Excel, PowerPoint, and more.

### Can I add multiple text signatures to a single document?
Yes, you can add multiple text signatures, each with its own customization options.

### Does GroupDocs.Signature ensure document integrity after signing?
Yes, the library uses robust cryptographic algorithms to ensure document integrity and prevent tampering after signing.

### Is there a trial version available for testing before purchasing?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/) to explore the features before making a purchase.
