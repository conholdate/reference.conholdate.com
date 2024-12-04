---
title: Adding Custom Document Properties in Word
linktitle: Adding Custom Document Properties in Word
second_title: Aspose.Words Document Processing API
description: Learn how to enhance your Word documents with custom document properties using Aspose.Words for .NET. This comprehensive guide walks you through the process.
type: docs
weight: 10
url: /net/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Introduction

Welcome! If you're exploring Aspose.Words for .NET and want to learn how to add custom document properties to your Word files, you’re in the right place. Custom properties are invaluable for storing additional metadata that built-in properties don’t cover. Whether you need to track document authorization, revision numbers, or specific dates, custom properties can help. In this tutorial, we’ll guide you through the steps to add these properties seamlessly using Aspose.Words for .NET. Let’s get started!

## Prerequisites

Before diving into the code, ensure you have the following:

1. Aspose.Words for .NET Library: Download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: An IDE such as Visual Studio.
3. Basic Knowledge of C#: Familiarity with C# and .NET will be helpful.
4. Sample Document: Prepare a sample Word document named `Properties.docx` for modification.

## Importing Namespaces

To access the functionalities of Aspose.Words, you’ll need to import the necessary namespaces at the beginning of your code:

```csharp
using System;
using Aspose.Words;
```

## Step 1: Setting Up the Document Path

Next, let’s define the path to your Word document. This step is essential for locating and opening your `Properties.docx` file.

```csharp
// Specify the path to your documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

Make sure to replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document.

## Step 2: Accessing Custom Document Properties

Now, let’s access the custom document properties of the Word document, where your custom metadata will reside.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

This line gives you access to the collection of custom properties you’ll be working with.

## Step 3: Checking for Existing Properties

Before adding new properties, it’s wise to check if a property already exists to avoid duplication.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

This code checks if the "Authorized" property already exists. If it does, the method exits early, preventing duplicates.

## Step 4: Adding a Boolean Property

Let’s add a custom boolean property to indicate whether the document is authorized.

```csharp
customDocumentProperties.Add("Authorized", true);
```

This line adds a property named "Authorized" and sets its value to `true`.

## Step 5: Adding a String Property

Next, we’ll specify who authorized the document by adding a string property.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Feel free to replace "John Smith" with any name you prefer.

## Step 6: Adding a Date Property

To track when the document was authorized, let’s add a date property.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

This line adds a property called "Authorized Date" and assigns it today’s date using `DateTime.Today`.

## Step 7: Adding a Revision Number

For version control, we can add a property to keep track of the document's revision number.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Here, we add an "Authorized Revision" property that holds the document’s current revision number.

## Step 8: Adding a Numeric Property

Finally, let’s add a numeric property to store an authorized amount, such as a budget figure.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

This line adds a property named "Authorized Amount" with a value of `123.45`. You can adjust this number as needed.

## Conclusion

Congratulations! You’ve successfully added custom document properties to a Word document using Aspose.Words for .NET. These properties are a powerful way to store metadata tailored to your requirements, whether tracking authorization details, revision numbers, or specific amounts.

## FAQ's

### What are custom document properties?
Custom document properties are metadata you can add to a Word document to store additional information not covered by built-in properties.

### Can I add properties other than strings and numbers?
Yes, you can add various types of properties, including boolean values, dates, and even custom objects.

### How can I access these properties in a Word document?
You can access custom properties programmatically using Aspose.Words or view them directly in Word through the document properties.

### Is it possible to edit or delete custom properties?
Absolutely! You can easily edit or delete custom properties using methods provided by Aspose.Words.

### Can custom properties be used for filtering documents?
Yes! Custom properties are excellent for categorizing and filtering documents based on specific metadata.
