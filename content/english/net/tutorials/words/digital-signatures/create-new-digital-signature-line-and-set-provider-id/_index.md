---
title: Create New Digital Signature Line And Set Provider Id
linktitle: Create New Digital Signature Line And Set Provider Id
second_title: Aspose.Words Document Processing API
description: Discover how to programmatically add signature lines to your Word documents using Aspose.Words for .NET. This comprehensive guide covers everything from setting up your development environment to inserting signature lines and signing documents securely.
type: docs
weight: 10
url: /net/tutorials/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Introduction

Hello, tech enthusiasts! Have you ever wanted to automate the inclusion of signature lines in your Word documents? Today, we’re diving into how to achieve this using Aspose.Words for .NET. This step-by-step guide will walk you through creating a signature line and setting the provider ID, making your document processing tasks more efficient and streamlined.

## Prerequisites

Before we jump in, let’s ensure you have everything set up:

1. Aspose.Words for .NET: If you haven't installed it yet, download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Use Visual Studio or any C# development setup.
3. .NET Framework: Ensure you have the .NET Framework installed on your machine.
4. PFX Certificate: You’ll need a PFX certificate for signing documents, which can be obtained from a trusted certificate authority.

## Importing Necessary Namespaces

To get started, import the required namespaces into your C# project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Now, let’s dive into the details of creating a new signature line and setting the provider ID.

## Step 1: Create a New Document

First, we need to create a new Word document, which will serve as the canvas for our signature line:

```csharp
// Specify the path to your documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Here, we initialize a new `Document` and a `DocumentBuilder`, which allows us to add elements easily.

## Step 2: Define Signature Line Options

Next, we’ll define the options for our signature line, including the signer's name, title, email, and other relevant details:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

These options help personalize the signature line, making it clear and professional.

## Step 3: Insert the Signature Line

With our options ready, we can now insert the signature line into the document:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

The `InsertSignatureLine` method adds the signature line, and we assign a unique provider ID to it.

## Step 4: Save the Document

After inserting the signature line, let’s save the document:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

This saves your document with the newly added signature line.

## Step 5: Set Up Signing Options

Now, we’ll configure the signing options, including the signature line ID, provider ID, comments, and the signing time:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

These settings ensure that the document is signed with the correct details.

## Step 6: Create Certificate Holder

To sign the document, we need to create a certificate holder using the PFX certificate:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Replace `"morzal.pfx"` with your actual certificate file name and `"aw"` with your certificate password.

## Step 7: Sign the Document

Finally, we’ll sign the document using the digital signature utility:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

This process signs the document and saves it as a new file.

## Conclusion

Congratulations! You’ve successfully created a signature line and set the provider ID in a Word document using Aspose.Words for .NET. This powerful library simplifies document processing tasks, making your workflow more efficient. Give it a try and see how it can enhance your projects!

## FAQ's

### Can I customize the appearance of the signature line?
Absolutely! You can adjust various options in the `SignatureLineOptions` to fit your style and requirements.

### What if I don't have a PFX certificate?
You will need to obtain one from a trusted certificate authority, as it is essential for digitally signing documents.

### Can I add multiple signature lines to a document?
Yes, you can add multiple signature lines by repeating the insertion process with different options.

### Is Aspose.Words for .NET compatible with .NET Core?
Yes, Aspose.Words for .NET supports .NET Core, making it versatile for various development environments.

### How secure are the digital signatures?
Digital signatures created with Aspose.Words are highly secure, provided you use a valid and trusted certificate.
