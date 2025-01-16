---
title: पावरपॉइंट से ऑडियो और वीडियो निकालना
linktitle: पावरपॉइंट से ऑडियो और वीडियो निकालना
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: जानें कि Aspose.Slides for .NET का उपयोग करके PowerPoint प्रस्तुतियों से ऑडियो और वीडियो तत्वों को आसानी से कैसे निकाला जाए। यह विस्तृत गाइड चरण-दर-चरण दृष्टिकोण प्रदान करता है।
type: docs
weight: 10
url: /hi/net/tutorials/slides/extract-audio-and-video/extracting-audio-and-video/
---
## परिचय

आज के डिजिटल परिदृश्य में, मल्टीमीडिया प्रस्तुतियाँ संचार, शिक्षा और मनोरंजन में महत्वपूर्ण भूमिका निभाती हैं। पावरपॉइंट स्लाइड्स में अक्सर ऑडियो और वीडियो तत्व शामिल होते हैं, जो उन्हें सूचना को प्रभावी ढंग से संप्रेषित करने के लिए आवश्यक बनाते हैं। चाहे संग्रह करना हो, सामग्री का पुनः उपयोग करना हो या प्रस्तुतियों को बेहतर बनाना हो, इन मल्टीमीडिया घटकों को निकालना अक्सर आवश्यक होता है।

यह गाइड आपको .NET के लिए Aspose.Slides का उपयोग करके PowerPoint स्लाइड से ऑडियो और वीडियो निकालने की प्रक्रिया से परिचित कराएगा। Aspose.Slides एक मजबूत लाइब्रेरी है जो .NET डेवलपर्स को प्रोग्रामेटिक रूप से PowerPoint प्रस्तुतियों में हेरफेर करने की शक्ति प्रदान करती है, जिससे मल्टीमीडिया निष्कर्षण कार्य सरल हो जाते हैं।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:

1. विज़ुअल स्टूडियो: सुनिश्चित करें कि आपके पास .NET विकास के लिए विज़ुअल स्टूडियो स्थापित है।
2.  Aspose.Slides for .NET: Aspose.Slides for .NET को डाउनलोड करें और इंस्टॉल करें[Aspose वेबसाइट](https://releases.aspose.com/slides/net/).
3. पावरपॉइंट प्रस्तुति: अभ्यास के लिए ऑडियो और वीडियो तत्वों से युक्त एक पावरपॉइंट प्रस्तुति तैयार करें।

इन पूर्वापेक्षाओं के साथ, आइए निष्कर्षण प्रक्रिया में उतरें।

## पावरपॉइंट स्लाइड से ऑडियो निकालना

### चरण 1: अपना प्रोजेक्ट सेट करें

Visual Studio में एक नया प्रोजेक्ट बनाएं और आवश्यक Aspose.Slides नामस्थान आयात करें:

```csharp
using Aspose.Slides;
using Aspose.Slides.SlideShow;
```

### चरण 2: प्रस्तुति लोड करें

वह पावरपॉइंट प्रस्तुति लोड करें जिसमें वह ऑडियो है जिसे आप निकालना चाहते हैं:

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "AudioSlide.ppt";
Presentation pres = new Presentation(presName);
```

### चरण 3: इच्छित स्लाइड तक पहुंचें

 उपयोग`ISlide` किसी विशिष्ट स्लाइड तक पहुंचने के लिए इंटरफ़ेस:

```csharp
ISlide slide = pres.Slides[0]; // पहली स्लाइड पर पहुँचें
```

### चरण 4: ऑडियो निकालें

स्लाइड के संक्रमण प्रभाव से ऑडियो डेटा पुनः प्राप्त करें:

```csharp
ISlideShowTransition transition = slide.SlideShowTransition;
byte[] audio = transition.Sound.BinaryData;
System.Console.WriteLine("Audio Length: " + audio.Length);
```

## पावरपॉइंट स्लाइड से वीडियो निकालना

### चरण 1: अपना प्रोजेक्ट सेट करें

ऑडियो निष्कर्षण की तरह, एक नया प्रोजेक्ट बनाकर और आवश्यक नामस्थानों को आयात करके आरंभ करें।

### चरण 2: प्रस्तुति लोड करें

वह पावरपॉइंट प्रस्तुति लोड करें जिसमें वह वीडियो है जिसे आप निकालना चाहते हैं:

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "Video.pptx";
Presentation pres = new Presentation(presName);
```

### चरण 3: स्लाइड और आकृतियों के माध्यम से पुनरावृति करें

वीडियो फ़्रेम की पहचान करने के लिए स्लाइडों और आकृतियों को देखें:

```csharp
foreach (ISlide slide in pres.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is IVideoFrame videoFrame)
        {
            // वीडियो फ़्रेम जानकारी निकालें
            string contentType = videoFrame.EmbeddedVideo.ContentType;
            string fileType = contentType.Substring(contentType.LastIndexOf('/') + 1);
            
            // वीडियो डेटा को बाइट सरणी के रूप में प्राप्त करें
            byte[] buffer = videoFrame.EmbeddedVideo.BinaryData;
            
            // वीडियो को फ़ाइल में सहेजें
            using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileType, FileMode.Create, FileAccess.Write, FileShare.Read))
            {
                stream.Write(buffer, 0, buffer.Length);
            }
        }
    }
}
```

## निष्कर्ष

Aspose.Slides for .NET पावरपॉइंट प्रेजेंटेशन से ऑडियो और वीडियो निकालना आसान बनाता है। चाहे आप कंटेंट संग्रहित कर रहे हों, मल्टीमीडिया का पुनः उपयोग कर रहे हों या प्रेजेंटेशन का विश्लेषण कर रहे हों, यह लाइब्रेरी आपको प्रक्रिया को सरल बनाने के लिए आवश्यक उपकरण प्रदान करती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या Aspose.Slides for .NET नवीनतम PowerPoint प्रारूपों के साथ संगत है?
हां, Aspose.Slides for .NET, PPTX सहित नवीनतम PowerPoint प्रारूपों का समर्थन करता है।

### क्या मैं एक साथ कई स्लाइडों से ऑडियो और वीडियो निकाल सकता हूँ?
बिल्कुल! आप कोड को संशोधित करके कई स्लाइडों को दोहरा सकते हैं और प्रत्येक स्लाइड से मल्टीमीडिया निकाल सकते हैं।

### क्या .NET के लिए Aspose.Slides के लिए कोई लाइसेंसिंग विकल्प हैं?
 Aspose कई तरह के लाइसेंसिंग विकल्प प्रदान करता है, जिसमें निःशुल्क परीक्षण और अस्थायी लाइसेंस शामिल हैं।[वेबसाइट](https://purchase.aspose.com/buy) अधिक जानकारी के लिए.

### मैं .NET के लिए Aspose.Slides का समर्थन कैसे प्राप्त कर सकता हूं?
 तकनीकी सहायता और सामुदायिक चर्चाओं के लिए, Aspose.Slides देखें[मंच](https://forum.aspose.com/).

### मैं Aspose.Slides for .NET के साथ अन्य कौन से कार्य कर सकता हूँ?
 Aspose.Slides for .NET में कई तरह की सुविधाएँ उपलब्ध हैं, जिसमें PowerPoint प्रस्तुतियाँ बनाना, संशोधित करना और परिवर्तित करना शामिल है। अधिक जानकारी के लिए दस्तावेज़ देखें:[.NET दस्तावेज़ीकरण के लिए Aspose.Slides](https://reference.aspose.com/slides/net/).