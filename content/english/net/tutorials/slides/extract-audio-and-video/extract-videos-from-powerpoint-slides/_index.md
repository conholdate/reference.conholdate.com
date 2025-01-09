---
title: Extract Videos from PowerPoint Slides with Aspose.Slides
linktitle: Extract Videos from PowerPoint Slides
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Discover how to easily extract embedded video files from PowerPoint presentations using Aspose.Slides for .NET. This comprehensive step-by-step guide covers everything from setting up your environment to saving the extracted videos.
type: docs
weight: 14
url: /net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Introduction

Aspose.Slides for .NET is a powerful library that allows developers to interact with PowerPoint presentations programmatically. In this guide, we will walk you through the process of extracting videos embedded in PowerPoint slides using Aspose.Slides for .NET. 

## Prerequisites

Before you begin, ensure you have the following:

- Aspose.Slides for .NET: Obtain and install the library from the [Aspose website](https://purchase.aspose.com/buy).
- PowerPoint Presentation: Prepare a PowerPoint file (e.g., `Video.pptx`) with the video you wish to extract.

## Necessary Namespaces

To work with Aspose.Slides for .NET, you need to import the appropriate namespaces. Include the following in your code:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Step 1: Specify the Document Directory

First, define the path to your PowerPoint presentation:

```csharp
string dataDir = "Your Document Directory";
```

Replace `"Your Document Directory"` with the actual path to the directory containing your PowerPoint file.

## Step 2: Load the Presentation

Load the PowerPoint presentation into a `Presentation` object:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

This initializes the `Presentation` object with your specified PowerPoint file.

## Step 3: Iterate Through Slides and Shapes

Next, loop through each slide in the presentation and check for video frames:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Proceed to extract video
        }
    }
}
```

## Step 4: Extract Video Data

Once you find a video frame, extract its properties and binary data:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Store the shape as a video frame
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Get the file extension
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Step 5: Save the Video

Finally, write the extracted video data to a file:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

This code creates a new file in your specified directory and writes the video data into it.

## Conclusion

With Aspose.Slides for .NET, extracting videos from PowerPoint slides is a straightforward process. By following this guide, you can easily manage multimedia content within your .NET applications, enriching user experience and functionality.

## FAQ's

### What is Aspose.Slides for .NET?
Aspose.Slides for .NET is a library designed to work with PowerPoint presentations, allowing users to create, edit, and manipulate presentation files programmatically.

### Where can I find the documentation for Aspose.Slides for .NET?
You can access the full documentation [here](https://reference.aspose.com/slides/net/).

### Is Aspose.Slides for .NET available for a free trial?
Yes, you can download a free trial version from [this link](https://releases.aspose.com/).

### How can I obtain a temporary license for Aspose.Slides for .NET?
Requests for temporary licenses can be made [here](https://purchase.aspose.com/temporary-license/).

### Where can I get support for Aspose.Slides for .NET?
Support is available through the [Aspose.Slides forum](https://forum.aspose.com/).
