---
title: Saving OneNote Documents in PDF Using Aspose.Note for .NET
linktitle: Saving OneNote Documents in PDF
second_title: Aspose.Note .NET API
description: Learn how to efficiently save Microsoft OneNote documents as PDF files using Aspose.Note for .NET. This guide walks you through the necessary prerequisites, and offers helpful FAQs.
type: docs
weight: 26
url: /net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Introduction

In this tutorial, we'll explore how to save documents to PDF format using Aspose.Note for .NET. Aspose.Note is a powerful library that enables developers to work with Microsoft OneNote files programmatically. We'll cover the prerequisites, import namespaces, and provide step-by-step guides for saving documents to PDF in various page layouts.

## Prerequisites
1. Visual Studio: Ensure it’s installed.
2. Aspose.Note for .NET: Download and install the library.
3. C# Knowledge: Basic understanding of the language is required.

## Importing Necessary Namespaces
Before proceeding, import the following namespaces in your code:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Step 1: Save to PDF with Letter Page Settings
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Update this path
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Loads the OneNote document and saves it as a PDF using letter-sized page settings.

## Step 2: Save to PDF with A4 Page Settings (No Height Limit)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Update this path
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Similar to Step 1 but uses A4 page settings without height limitations.

## Conclusion
The tutorial successfully demonstrates how to convert OneNote files to PDF format using Aspose.Note. By utilizing different page settings, developers gain flexibility in document management.

## FAQ's
### Can Aspose.Note handle complex OneNote files?
Yes, it effectively handles various features of complex OneNote files.

### Is Aspose.Note suitable for commercial projects?
Yes, you can use it for commercial applications after purchasing a license.

### Does Aspose.Note offer a free trial?
Yes, a free trial is available for exploration.

### Where can I find documentation for Aspose.Note?
Detailed documentation is available on the Aspose reference site.

### Need further assistance?
For questions and support, refer to the Aspose.Note forum.

