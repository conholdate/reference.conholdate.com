---
title: Extracting Line Rectangles from Images Recognition
linktitle: Extracting Line Rectangles from Images Recognition
second_title: Aspose.OCR .NET API
description: Learn how to implement Optical Character Recognition (OCR) in your .NET applications using Aspose.OCR. This comprehensive guide walks you through the process of extracting rectangles for recognized lines.
type: docs
weight: 10
url: /net/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Introduction

Welcome to the world of Aspose.OCR for .NET, an impressive tool designed to integrate Optical Character Recognition (OCR) into your .NET applications. Whether you're an experienced developer or a curious newcomer, this guide will walk you through the steps to obtain rectangles representing lines from recognized text in images.

## Prerequisites

Before you begin, ensure you have the following in place:

- Basic knowledge of C# and .NET development.
- An integrated development environment (IDE) like Visual Studio.
- The Aspose.OCR for .NET library installed. You can download it [here](https://releases.aspose.com/ocr/net/).
- A sample image containing text for recognition.

## Required Namespaces

To start, you'll need to add the necessary namespaces to your project. Include these lines at the top of your C# file:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Follow these steps to retrieve rectangles for lines in an OCR image.

## Step 1: Set Up Your Document Directory

Specify the directory where your image file is located:

```csharp
// Define the path to your document directory
string dataDir = "Your Document Directory";
```

Make sure to replace `"Your Document Directory"` with the actual path.

## Step 2: Initialize Aspose.OCR

Create an instance of the `AsposeOcr` class to access its features:

```csharp
// Initialize the Aspose.OCR API
AsposeOcr api = new AsposeOcr();
```

## Step 3: Specify the Image Path

Define the full path to the image file you want to process:

```csharp
// Specify the full path to the image
string fullPath = dataDir + "sample.png";
```

## Step 4: Recognize Image and Get Rectangles for Lines

Now, you can use the `GetRectangles` method to extract rectangles of recognized text lines:

```csharp
// Retrieve rectangles for lines in the specified image
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Step 5: Output the Results

Finally, print the coordinates of each detected line rectangle to the console:

```csharp
// Display the coordinates of the detected rectangles
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Conclusion

Congratulations! You have successfully retrieved rectangles for lines in an OCR image using Aspose.OCR for .NET. This technology opens up numerous possibilities for text extraction and processing in your applications.

## FAQ's

### Can I use Aspose.OCR for .NET with any type of image?

Yes, Aspose.OCR supports various image formats, providing flexibility for your OCR applications.

### What is the accuracy rate of the OCR recognition?

Aspose.OCR uses advanced algorithms to achieve high accuracy in text recognition, suitable for diverse scenarios.

### Is a trial version available?

Yes, you can explore the features of Aspose.OCR for .NET by downloading the [free trial](https://releases.aspose.com/).

### Where can I find detailed documentation?

Comprehensive documentation can be found [here](https://reference.aspose.com/ocr/net/), offering in-depth information and guidelines.

### Need further assistance or have questions?

Join the discussion at the [Aspose.OCR forum](https://forum.aspose.com/c/ocr/16) for community support.
