---
title: Extrahera videor från PowerPoint-bilder med Aspose.Slides
linktitle: Extrahera videor från PowerPoint-bilder
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Upptäck hur du enkelt extraherar inbäddade videofiler från PowerPoint-presentationer med Aspose.Slides för .NET. Den här omfattande steg-för-steg-guiden täcker allt från att ställa in din miljö till att spara de extraherade videorna.
type: docs
weight: 14
url: /sv/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Introduktion

Aspose.Slides för .NET är ett kraftfullt bibliotek som låter utvecklare interagera med PowerPoint-presentationer programmatiskt. I den här guiden går vi igenom processen att extrahera videor inbäddade i PowerPoint-bilder med Aspose.Slides för .NET. 

## Förutsättningar

Innan du börjar, se till att du har följande:

-  Aspose.Slides för .NET: Skaffa och installera biblioteket från[Aspose hemsida](https://purchase.aspose.com/buy).
-  PowerPoint-presentation: Förbered en PowerPoint-fil (t.ex.`Video.pptx`) med videon du vill extrahera.

## Nödvändiga namnutrymmen

För att arbeta med Aspose.Slides för .NET måste du importera lämpliga namnområden. Inkludera följande i din kod:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Steg 1: Ange dokumentkatalogen

Definiera först sökvägen till din PowerPoint-presentation:

```csharp
string dataDir = "Your Document Directory";
```

 Ersätta`"Your Document Directory"` med den faktiska sökvägen till katalogen som innehåller din PowerPoint-fil.

## Steg 2: Ladda presentationen

 Ladda PowerPoint-presentationen i en`Presentation` objekt:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Detta initierar`Presentation` objekt med din angivna PowerPoint-fil.

## Steg 3: Iterera genom diabilder och former

Gå sedan igenom varje bild i presentationen och leta efter videoramar:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Fortsätt för att extrahera video
        }
    }
}
```

## Steg 4: Extrahera videodata

När du har hittat en videoram, extrahera dess egenskaper och binära data:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Lagra formen som en videoram
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Skaffa filtillägget
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Steg 5: Spara videon

Skriv slutligen den extraherade videodatan till en fil:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Den här koden skapar en ny fil i din angivna katalog och skriver in videodata i den.

## Slutsats

Med Aspose.Slides för .NET är det en enkel process att extrahera videor från PowerPoint-bilder. Genom att följa den här guiden kan du enkelt hantera multimediainnehåll i dina .NET-applikationer, vilket berikar användarupplevelsen och funktionaliteten.

## FAQ's

### Vad är Aspose.Slides för .NET?
Aspose.Slides för .NET är ett bibliotek som är utformat för att fungera med PowerPoint-presentationer, vilket tillåter användare att skapa, redigera och manipulera presentationsfiler programmatiskt.

### Var kan jag hitta dokumentationen för Aspose.Slides för .NET?
 Du kan få tillgång till hela dokumentationen[här](https://reference.aspose.com/slides/net/).

### Är Aspose.Slides för .NET tillgängligt för en gratis provperiod?
 Ja, du kan ladda ner en gratis testversion från[denna länk](https://releases.aspose.com/).

### Hur kan jag få en tillfällig licens för Aspose.Slides för .NET?
 Begäran om tillfälliga licenser kan göras[här](https://purchase.aspose.com/temporary-license/).

### Var kan jag få support för Aspose.Slides för .NET?
 Support finns tillgänglig via[Aspose.Slides forum](https://forum.aspose.com/).