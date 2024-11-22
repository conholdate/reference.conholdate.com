---
title: .NET के लिए Aspose.Slides के साथ एनीमेशन के बाद के प्रभावों में महारत हासिल करना
linktitle: .NET के लिए Aspose.Slides के साथ एनीमेशन के बाद के प्रभावों में महारत हासिल करना
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: Aspose.Slides for .NET के साथ आफ्टर-एनीमेशन इफ़ेक्ट्स में महारत हासिल करके अपनी प्रेजेंटेशन की पूरी क्षमता को अनलॉक करें। यह चरण-दर-चरण गाइड आपको ज़रूरी जानकारी प्रदान करती है।
type: docs
weight: 11
url: /hi/net/tutorials/slides/master-slide-animation-control/control-after-animation-effects/
---
## परिचय

डायनेमिक एनिमेशन आपकी प्रस्तुतियों को महत्वपूर्ण रूप से बेहतर बना सकते हैं, जिससे वे अधिक आकर्षक और आकर्षक बन सकते हैं। Aspose.Slides for .NET के साथ, आप आसानी से आफ्टर-एनीमेशन प्रभावों को नियंत्रित कर सकते हैं, जिससे आप अपने दर्शकों के लिए इंटरैक्टिव अनुभव बना सकते हैं। यह ट्यूटोरियल आपको अपनी स्लाइड्स में इन प्रभावों को हेरफेर करने की प्रक्रिया के माध्यम से चरण-दर-चरण मार्गदर्शन करेगा।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें हैं:

- C# और .NET प्रोग्रामिंग का बुनियादी ज्ञान।
-  Aspose.Slides for .NET लाइब्रेरी स्थापित है। इसे डाउनलोड करें[यहाँ](https://releases.aspose.com/slides/net/).
- विजुअल स्टूडियो जैसा एक एकीकृत विकास वातावरण (आईडीई).

## नामस्थान आयात करें

आवश्यक Aspose.Slides कार्यात्मकताओं तक पहुँचने के लिए, अपने कोड में निम्नलिखित नामस्थान शामिल करें:

```csharp
using System.Drawing;
using System.IO;
using Aspose.Slides.Animation;
using Aspose.Slides.SlideShow;
using Aspose.Slides.Export;
```

## चरण 1: दस्तावेज़ निर्देशिका सेट करें

सबसे पहले यह सुनिश्चित करें कि आपके दस्तावेज़ों के लिए निर्देशिका मौजूद है। अगर नहीं है, तो इसे बनाएँ:

```csharp
string dataDir = "Your Document Directory";
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## चरण 2: आउटपुट फ़ाइल पथ निर्धारित करें

अपनी संशोधित प्रस्तुति के लिए आउटपुट फ़ाइल पथ निर्दिष्ट करें:

```csharp
string outPath = Path.Combine(dataDir, "AnimationAfterEffect-out.pptx");
```

## चरण 3: प्रस्तुति लोड करें

 का उपयोग करके अपनी मौजूदा प्रस्तुति लोड करें`Presentation` कक्षा:

```csharp
using (Presentation pres = new Presentation(dataDir + "AnimationAfterEffect.pptx"))
```

## चरण 4: स्लाइड 1 पर एनीमेशन प्रभाव के बाद संशोधन करें

पहली स्लाइड को क्लोन करें और इसके एनीमेशन प्रभाव को "अगले माउस क्लिक पर छिपाएं" पर सेट करें:

```csharp
ISlide slide1 = pres.Slides.AddClone(pres.Slides[0]);
ISequence seq = slide1.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideOnNextMouseClick;
```

## चरण 5: स्लाइड 2 पर एनीमेशन प्रभाव के बाद संशोधन करें

पहली स्लाइड को पुनः क्लोन करें, तथा एनीमेशन के बाद के प्रभाव को हरे रंग के साथ "रंग" में बदलें:

```csharp
ISlide slide2 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide2.Timeline.MainSequence;
foreach (IEffect effect in seq)
{
    effect.AfterAnimationType = AfterAnimationType.Color;
    effect.AfterAnimationColor.Color = Color.Green;
}
```

## चरण 6: स्लाइड 3 पर एनीमेशन प्रभाव के बाद संशोधन करें

तीसरी स्लाइड के लिए, एनीमेशन के बाद प्रभाव को "एनीमेशन के बाद छिपाएं" पर सेट करें:

```csharp
ISlide slide3 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide3.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideAfterAnimation;
```

## चरण 7: संशोधित प्रस्तुति को सहेजें

अंत में, अपनी संशोधित प्रस्तुति को सहेजें:

```csharp
pres.Save(outPath, SaveFormat.Pptx);
```

## निष्कर्ष

बधाई हो! आपने Aspose.Slides for .NET का उपयोग करके स्लाइड पर आफ्टर-एनीमेशन प्रभावों को नियंत्रित करना सफलतापूर्वक सीख लिया है। अपने दर्शकों को आकर्षित करने वाले गतिशील और आकर्षक प्रस्तुतियाँ बनाने के लिए अलग-अलग प्रभावों के साथ प्रयोग करने के लिए स्वतंत्र महसूस करें।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं स्लाइड के अलग-अलग तत्वों पर अलग-अलग आफ्टर-एनीमेशन प्रभाव लागू कर सकता हूँ?

हां, आप अलग-अलग तत्वों के लिए एनीमेशन के बाद के प्रभावों को उनके माध्यम से पुनरावृत्त करके और उनके गुणों को तदनुसार समायोजित करके अनुकूलित कर सकते हैं।

### क्या Aspose.Slides .NET के नवीनतम संस्करणों के साथ संगत है?

बिल्कुल! Aspose.Slides को नवीनतम .NET फ्रेमवर्क संस्करणों के साथ संगतता सुनिश्चित करने के लिए नियमित रूप से अपडेट किया जाता है।

### मैं Aspose.Slides का उपयोग करके स्लाइड्स में कस्टम एनिमेशन कैसे जोड़ सकता हूँ?

 कस्टम एनिमेशन जोड़ने के बारे में विस्तृत जानकारी के लिए, देखें[Aspose.Slides दस्तावेज़ीकरण](https://reference.aspose.com/slides/net/).

### प्रस्तुतियों को सहेजने के लिए Aspose.Slides किस फ़ाइल स्वरूप का समर्थन करता है?

Aspose.Slides विभिन्न प्रारूपों का समर्थन करता है, जिसमें PPTX, PPT, PDF, और बहुत कुछ शामिल है। पूरी सूची के लिए दस्तावेज़ देखें।

### मैं Aspose.Slides से संबंधित सहायता कहां से प्राप्त कर सकता हूं या प्रश्न कहां पूछ सकता हूं?

 समर्थन और सामुदायिक संपर्क के लिए, यहां जाएं[Aspose.Slides फ़ोरम](https://forum.aspose.com/c/slides/11).