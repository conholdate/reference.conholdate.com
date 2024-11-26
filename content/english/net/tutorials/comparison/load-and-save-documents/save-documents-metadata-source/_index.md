---
title: Save Documents Metadata Source in GroupDocs Comparison for .NET
linktitle: Saving Documents Metadata Source in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Unlock the full potential of document comparison in your .NET applications by leveraging GroupDocs Comparison for .NET. This step-by-step tutorial walks you through comparing documents effortlessly, while focusing on saving document metadata source.
type: docs
weight: 14
url: /net/load-and-save-documents/save-documents-metadata-source/
---
## Introduction

In software development, particularly within industries like legal, finance, and education, the ability to compare documents efficiently is paramount. GroupDocs Comparison for .NET provides a robust solution to seamlessly compare documents within your .NET applications. This tutorial will guide you through utilizing this powerful library to save the document metadata source, ensuring you maximize its capabilities for your document comparison tasks.

## Prerequisites

Before we start, make sure you have the following set up:

1. Development Environment: A .NET development environment is ready on your machine.
2. GroupDocs Comparison Installation: Download and install GroupDocs Comparison for .NET from the [site](https://releases.groupdocs.com/comparison/net/).
3. Document Files: Prepare the source and target document files you wish to compare.
4. Basic Knowledge of C#: Familiarity with the basics of C# programming will help you understand the provided code snippets.

## Import Required Namespaces

Start by importing the necessary namespaces into your project:

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## Step 1: Define Output Directory and File Name

First, specify where the compared document will be saved and its name:

```csharp
string outputDirectory = "Your Document Directory"; // e.g., "C:\\Documents"
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```

## Step 2: Initialize the Comparer Object

Create a `Comparer` instance using the path to your source document:

```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
This initializes the `Comparer` object, providing a foundation for your document comparison.

## Step 3: Add the Target Document

Next, incorporate the target document into the comparison:

```csharp
comparer.Add("TARGET.docx");
```
This step specifies the document you want to compare against the source.

## Step 4: Compare Documents and Save Metadata Source

Now, it's time to perform the comparison and save the document metadata source:

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
Here, the `Compare` method compares the source and target documents. By using `CloneMetadataType`, you ensure that the metadata from the source document is retained.

## Step 5: Display Output Message

After the comparison is complete, provide feedback on the operation:

```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
This message confirms a successful comparison and indicates where to find the output document.

## Conclusion

GroupDocs Comparison for .NET is an invaluable tool for document comparison tasks within .NET applications. By following this guide, you've learned how to efficiently save document metadata source, enhancing your document comparison process and overall productivity.

## FAQ's

### Can GroupDocs Comparison for .NET compare documents of different formats?

Yes, it supports a variety of formats, including DOCX, PDF, PPTX, and more.

### Is there a trial version available?

You can access the trial version from [here](https://releases.groupdocs.com/).

### Can I customize the output format of the compared documents?

Absolutely! GroupDocs Comparison allows for extensive customization of the output format.

### Is technical support available for users?

Yes, you can seek assistance through the [support forum](https://forum.groupdocs.com/c/comparison/12).

### Where can I purchase a license?

Licenses can be purchased from the GroupDocs website [here](https://purchase.groupdocs.com/buy).
