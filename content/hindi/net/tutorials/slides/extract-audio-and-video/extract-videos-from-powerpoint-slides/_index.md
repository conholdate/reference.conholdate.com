---
title: Aspose.Slides के साथ PowerPoint स्लाइड से वीडियो निकालें
linktitle: पावरपॉइंट स्लाइड से वीडियो निकालें
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: जानें कि Aspose.Slides for .NET का उपयोग करके PowerPoint प्रस्तुतियों से एम्बेडेड वीडियो फ़ाइलों को आसानी से कैसे निकाला जाए। यह व्यापक चरण-दर-चरण मार्गदर्शिका आपके परिवेश को सेट करने से लेकर निकाले गए वीडियो को सहेजने तक सब कुछ कवर करती है।
type: docs
weight: 14
url: /hi/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## परिचय

Aspose.Slides for .NET एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से PowerPoint प्रस्तुतियों के साथ इंटरैक्ट करने की अनुमति देती है। इस गाइड में, हम आपको Aspose.Slides for .NET का उपयोग करके PowerPoint स्लाइड में एम्बेड किए गए वीडियो निकालने की प्रक्रिया के बारे में बताएँगे। 

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  Aspose.Slides for .NET: लाइब्रेरी प्राप्त करें और इंस्टॉल करें[Aspose वेबसाइट](https://purchase.aspose.com/buy).
-  पावरपॉइंट प्रस्तुति: एक पावरपॉइंट फ़ाइल तैयार करें (जैसे,`Video.pptx`) पर क्लिक करें, जिस वीडियो को आप निकालना चाहते हैं।

## आवश्यक नामस्थान

.NET के लिए Aspose.Slides के साथ काम करने के लिए, आपको उचित नामस्थान आयात करने की आवश्यकता है। अपने कोड में निम्नलिखित शामिल करें:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## चरण 1: दस्तावेज़ निर्देशिका निर्दिष्ट करें

सबसे पहले, अपने पावरपॉइंट प्रेजेंटेशन का पथ निर्धारित करें:

```csharp
string dataDir = "Your Document Directory";
```

 प्रतिस्थापित करें`"Your Document Directory"` आपकी पावरपॉइंट फ़ाइल वाली निर्देशिका का वास्तविक पथ.

## चरण 2: प्रस्तुति लोड करें

 पावरपॉइंट प्रेजेंटेशन को एक में लोड करें`Presentation` वस्तु:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 यह आरंभ करता है`Presentation` अपनी निर्दिष्ट पावरपॉइंट फ़ाइल के साथ ऑब्जेक्ट को सहेजें।

## चरण 3: स्लाइड और आकृतियों के माध्यम से पुनरावृति करें

इसके बाद, प्रस्तुति में प्रत्येक स्लाइड को देखें और वीडियो फ़्रेम की जांच करें:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // वीडियो निकालने के लिए आगे बढ़ें
        }
    }
}
```

## चरण 4: वीडियो डेटा निकालें

एक बार जब आपको कोई वीडियो फ्रेम मिल जाए, तो उसके गुण और बाइनरी डेटा निकालें:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // आकृति को वीडियो फ़्रेम के रूप में संग्रहीत करें
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// फ़ाइल एक्सटेंशन प्राप्त करें
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## चरण 5: वीडियो सहेजें

अंत में, निकाले गए वीडियो डेटा को एक फ़ाइल में लिखें:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

यह कोड आपकी निर्दिष्ट निर्देशिका में एक नई फ़ाइल बनाता है और उसमें वीडियो डेटा लिखता है।

## निष्कर्ष

Aspose.Slides for .NET के साथ, PowerPoint स्लाइड से वीडियो निकालना एक सीधी प्रक्रिया है। इस गाइड का पालन करके, आप अपने .NET अनुप्रयोगों में मल्टीमीडिया सामग्री को आसानी से प्रबंधित कर सकते हैं, जिससे उपयोगकर्ता अनुभव और कार्यक्षमता समृद्ध हो सकती है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Slides क्या है?
Aspose.Slides for .NET एक लाइब्रेरी है जिसे पावरपॉइंट प्रस्तुतियों के साथ काम करने के लिए डिज़ाइन किया गया है, जो उपयोगकर्ताओं को प्रोग्रामेटिक रूप से प्रस्तुति फ़ाइलों को बनाने, संपादित करने और हेरफेर करने की अनुमति देता है।

### मैं Aspose.Slides for .NET के लिए दस्तावेज़ कहां पा सकता हूं?
 आप सम्पूर्ण दस्तावेज़ तक पहुँच सकते हैं[यहाँ](https://reference.aspose.com/slides/net/).

### क्या Aspose.Slides for .NET निःशुल्क परीक्षण के लिए उपलब्ध है?
 हां, आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[इस लिंक](https://releases.aspose.com/).

### मैं Aspose.Slides for .NET के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 अस्थायी लाइसेंस के लिए अनुरोध किया जा सकता है[यहाँ](https://purchase.aspose.com/temporary-license/).

### मुझे Aspose.Slides for .NET के लिए समर्थन कहां मिल सकता है?
 सहायता निम्नलिखित माध्यम से उपलब्ध है[Aspose.Slides फ़ोरम](https://forum.aspose.com/).