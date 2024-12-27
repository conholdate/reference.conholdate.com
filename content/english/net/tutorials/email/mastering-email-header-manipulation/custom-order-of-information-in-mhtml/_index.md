---
title: Custom Order of Information in MHTML with Aspose.Email
linktitle: Custom Order of Information in MHTML with Aspose.Email
second_title: Aspose.Email .NET Email Processing API
description: Learn how to define custom information order in MHTML using Aspose.Email for .NET in this step-by-step tutorial.
type: docs
weight: 14
url: /net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## Introduction

Creating rich email formats can greatly enhance communication, especially when exporting emails to different file formats like MHTML. Aspose.Email for .NET provides developers with a powerful toolkit for manipulating emails, which includes defining a custom order for how information is displayed when exporting to MHTML. In this guide, we’ll break down the steps needed to achieve this, making it easy to follow along whether you’re a seasoned developer or just starting out. So, let’s get right into it!

## Prerequisites

Before you dive into defining the custom order of information in MHTML, there are a few prerequisites you need to check off your list:

1. .NET Development Environment: Make sure you have a .NET development environment set up. You can use Visual Studio, Visual Studio Code, or any other compatible IDE.

2. Aspose.Email Library: You need to have the Aspose.Email for .NET library installed. You can download the latest version from the [Aspose releases page](https://releases.aspose.com/email/net/).

3. Basic Understanding of C#: Familiarity with C# programming will help you understand the code better.

4. Sample Email File: You'll need a sample `.eml` file (for example, `Attachments.eml`) for testing purposes.

Once you have these prerequisites, you're all set to follow along with the tutorial!

## Import Packages

To get started with your code, you will need to import the necessary namespaces from the Aspose.Email library. This is essential to access all the classes and methods needed for manipulating email files.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

Include these at the top of your C# file. Now you're ready to dive into coding!

Now that you have everything set up, let's break down the tutorial into manageable steps.

## Step 1: Set Your Data Directory

The first thing to do is to establish a directory where your email files will be stored. This could be any path on your local machine.

```csharp
string dataDir = "Your Data Directory";
```

Replace `"Your Data Directory"` with the actual path where your `.eml` file is located. For example, if your file is in `C:\Emails`, you would write:

```csharp
string dataDir = @"C:\Emails\";
```

## Step 2: Load the Email Message

Next, you need to load the `.eml` file into a `MailMessage` object. This allows you to manipulate the email's content and metadata.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

Make sure that the filename matches the one you have in the specified directory. If your file has a different name, update the filename accordingly.

## Step 3: Set Up MHTML Save Options

With your email loaded, it's time to define how you want to save it as MHTML. You can start with default options.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

This line initializes the MHTML save options, setting the stage for customizing the headers later.

## Step 4: Save MHTML with Default Order

Let’s save the email as MHTML using the default order. This gives you a baseline to compare against after customization.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

Run this line, and check your specified directory. You should now see a new MHTML file named `CustomOrderOfInformationInMHTML_1.mhtml`. Open it to see how the information is displayed by default.

## Step 5: Customize Header Order

Now comes the fun part! You can specify which headers to include in the MHTML output and in which order. We’ll start with some common headers.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

By adding these headers, you're telling Aspose how you'd like the email to be displayed.

## Step 6: Save MHTML with Custom Order

After customizing the headers, you need to save the email again as MHTML to see how the new order affects the output.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

Run this code, then open `CustomOrderOfInformationInMHTML_2.mhtml`. Compare it with the first one to see how the information has changed based on your header order.

## Step 7: Clear and Add New Header Order

What if you want a different order altogether? You can start fresh by clearing the existing header settings.

```csharp
opt.RenderingHeaders.Clear();
```

Now it’s time to define a new order for the headers. For example, if you want to prioritize attachments and copy recipients:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## Step 8: Save MHTML with New Custom Order

Finally, save the email one last time with the new header settings.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

After running this line, open `CustomOrderOfInformationInMHTML_3.mhtml` and check how it presents the information based on your new customization.

## Conclusion

And there you have it—a straightforward guide to defining a custom order of information in MHTML using Aspose.Email for .NET. By following these steps, you can control how your emails are represented in MHTML format, ensuring that the most important information is presented in a way that suits your needs. 

## FAQ's

### What is MHTML?
MHTML stands for "MIME HTML," a web page archive format that combines HTML and other resources like images.

### Can I use Aspose.Email for free?
Yes, Aspose provides a free trial version for developers to explore. You can find it [here](https://releases.aspose.com/).

### What if I encounter issues using Aspose.Email?
You can get support from the community via the [Aspose forum](https://forum.aspose.com/c/email/12/).

### Is a temporary license available for Aspose.Email?
Yes, you can apply for a temporary license [here](https://purchase.aspose.com/temporary-license/).

### Where can I buy Aspose.Email?
You can purchase the library at this [link](https://purchase.aspose.com/buy).
