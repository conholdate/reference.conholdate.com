---
title: .NET के लिए Aspose.Slides के साथ PowerPoint में समूह आकृतियाँ बनाएँ
linktitle: .NET के लिए Aspose.Slides के साथ PowerPoint में समूह आकृतियाँ बनाएँ
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: .NET के लिए Aspose.Slides का उपयोग करके समूह आकृतियाँ बनाना और प्रबंधित करना सीखें। यह व्यापक मार्गदर्शिका स्पष्ट, चरण-दर-चरण निर्देश प्रदान करती है।
type: docs
weight: 11
url: /hi/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## परिचय

अपने पावरपॉइंट प्रेजेंटेशन की दृश्य अपील और संगठन को बढ़ाना आपके दर्शकों की सहभागिता को महत्वपूर्ण रूप से प्रभावित कर सकता है। इसे प्राप्त करने का एक प्रभावी तरीका समूह आकृतियों के माध्यम से है। इस ट्यूटोरियल में, हम यह पता लगाएंगे कि अपने प्रेजेंटेशन में समूह आकृतियों को बनाने और उनमें हेरफेर करने के लिए .NET के लिए Aspose.Slides का लाभ कैसे उठाया जाए।

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

-  .NET के लिए Aspose.Slides: Aspose.Slides लाइब्रेरी का नवीनतम संस्करण डाउनलोड करें और इंस्टॉल करें।[Aspose वेबसाइट](https://releases.aspose.com/slides/net/).
- विकास परिवेश: अपने प्रोजेक्ट पर कार्य करने के लिए Visual Studio जैसे .NET-संगत IDE को सेट अप करें।
- बुनियादी C# ज्ञान: मौलिक C# अवधारणाओं से स्वयं को परिचित कराएं।


## आवश्यक नामस्थान आयात करें

अपने C# प्रोजेक्ट में, निम्नलिखित नामस्थानों को शामिल करके शुरुआत करें:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## चरण 1: प्रेजेंटेशन क्लास को इंस्टैंशिएट करें

 इसका एक उदाहरण बनाएं`Presentation`क्लास जहाँ आप अपनी स्लाइड्स पर काम करेंगे। वह निर्देशिका निर्दिष्ट करें जहाँ आपके दस्तावेज़ संग्रहीत हैं:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // आकृतियाँ बनाने और उनमें हेरफेर करने के चरण यहाँ दिए जाएँगे
}
```

## चरण 2: पहली स्लाइड तक पहुंचें

अपनी नई बनाई गई प्रस्तुति की पहली स्लाइड पुनः प्राप्त करें:

```csharp
ISlide slide = pres.Slides[0];
```

## चरण 3: आकृति संग्रह तक पहुँचें

स्लाइड पर आकृतियों का संग्रह प्राप्त करें:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## चरण 4: समूह आकार जोड़ें

अब स्लाइड में समूह आकार जोड़ने का समय आ गया है:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## चरण 5: समूह के अंदर आकृतियाँ जोड़ें

आप समूह आकृति को अलग-अलग आकृतियों से भर सकते हैं, जैसे कि आयतें:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // आकृति 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // आकृति 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // आकृति 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // आकृति 4
```

## चरण 6: समूह आकार के लिए फ़्रेम परिभाषित करें

समूह आकार के लिए फ़्रेम सेट करने से उसे एक परिभाषित सीमा मिल जाती है:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## चरण 7: प्रस्तुति सहेजें

अंत में, अपनी संशोधित प्रस्तुति को निर्दिष्ट निर्देशिका में सहेजें:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.Slides का उपयोग करके अपने PowerPoint प्रस्तुतियों में सफलतापूर्वक समूह आकृतियाँ बनाई हैं। इस तरह से आकृतियों को व्यवस्थित करके, आप अपनी सामग्री के दृश्य लेआउट और स्पष्टता में बहुत सुधार कर सकते हैं, जिससे आपकी प्रस्तुतियाँ अधिक प्रभावशाली बन सकती हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या Aspose.Slides .NET के नवीनतम संस्करण के साथ संगत है?

 हां, Aspose.Slides को नवीनतम .NET संस्करणों के साथ संगतता के लिए नियमित रूप से अपडेट किया जाता है।[प्रलेखन](https://reference.aspose.com/slides/net/) नवीनतम संगतता विवरण के लिए.

### क्या मैं खरीदने से पहले Aspose.Slides आज़मा सकता हूँ?

 बिलकुल! आप इसका निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/).

### मैं Aspose.Slides-संबंधित प्रश्नों के लिए समर्थन कहां पा सकता हूं?

 Aspose.Slides पर जाएँ[मंच](https://forum.aspose.com/c/slides/11) सामुदायिक समर्थन और चर्चा के लिए।

### मैं Aspose.Slides के लिए अस्थायी लाइसेंस कैसे प्राप्त करूं?

 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### मैं Aspose.Slides के लिए पूर्ण लाइसेंस कहां से खरीद सकता हूं?

 आप यहां से लाइसेंस खरीद सकते हैं[खरीद पृष्ठ](https://purchase.aspose.com/buy).