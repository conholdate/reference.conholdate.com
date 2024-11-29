---
title: पीडीएफ दस्तावेज़ में चेकबॉक्स घटक जोड़ना
linktitle: पीडीएफ दस्तावेज़ में चेकबॉक्स घटक जोड़ना
second_title: GroupDocs.Annotation .NET एपीआई
description: जानें कि GroupDocs.Annotation for .NET SDK का उपयोग करके इंटरैक्टिव चेकबॉक्स घटकों को जोड़कर अपने PDF दस्तावेज़ों को कैसे समृद्ध किया जाए। यह व्यापक ट्यूटोरियल एक स्पष्ट चरण-दर-चरण मार्गदर्शिका प्रदान करता है।
type: docs
weight: 11
url: /hi/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## परिचय

इस ट्यूटोरियल में, हम आपको GroupDocs.Annotation for .NET SDK का उपयोग करके PDF दस्तावेज़ में चेकबॉक्स घटक जोड़ने की प्रक्रिया से परिचित कराएँगे। यह सुविधा आपको अपने PDF दस्तावेज़ों को इंटरैक्टिव तत्वों के साथ बढ़ाने की अनुमति देती है, जिससे वे उपयोगकर्ताओं के लिए अधिक आकर्षक बन जाते हैं।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  .NET SDK के लिए GroupDocs.Annotation: इसे यहाँ से डाउनलोड करें[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: अपनी मशीन पर .NET विकास वातावरण स्थापित करें।

## चरण 1: आवश्यक नामस्थान आयात करें

सबसे पहले, अपने प्रोजेक्ट में आवश्यक नामस्थान शामिल करें:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## चरण 2: आउटपुट पथ निर्धारित करें

निर्दिष्ट करें कि संशोधित PDF दस्तावेज़ कहाँ सहेजा जाएगा:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## चरण 3: एनोटेटर को आरंभ करें

 इसका एक उदाहरण बनाएं`Annotator` अपने इनपुट पीडीएफ दस्तावेज़ के पथ के साथ क्लास:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## चरण 4: चेकबॉक्स घटक बनाएँ

अब, आइए चेकबॉक्स घटक बनाएं और उसे अनुकूलित करें:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // स्थिति और आकार निर्धारित करें
    PenColor = 65535, // रंग सेट करें (इस मामले में, पीला)
    Style = BoxStyle.Star, // चेकबॉक्स के लिए एक शैली चुनें
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## चरण 5: दस्तावेज़ में चेकबॉक्स जोड़ें

बनाए गए चेकबॉक्स घटक को PDF में जोड़ें:

```csharp
annotator.Add(checkBox);
```

## चरण 6: संशोधित दस्तावेज़ सहेजें

अपडेट किए गए PDF दस्तावेज़ को चेकबॉक्स के साथ सहेजें:

```csharp
annotator.Save("result.pdf");
```

## चरण 7: आउटपुट पथ प्रदर्शित करें

अंत में, उपयोगकर्ता को सूचित करें कि संशोधित दस्तावेज़ कहाँ सहेजा गया है:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ में सफलतापूर्वक चेकबॉक्स घटक जोड़ा है। यह कार्यक्षमता आपको इंटरैक्टिव PDF बनाने की अनुमति देती है जो उपयोगकर्ता अनुभव और जुड़ाव को बढ़ा सकती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं चेकबॉक्स का स्वरूप अनुकूलित कर सकता हूँ?

बिल्कुल! आप अपनी विशिष्ट आवश्यकताओं को पूरा करने के लिए रंग, शैली और आकार जैसे विभिन्न गुणों को संशोधित कर सकते हैं।

### क्या GroupDocs.Annotation for .NET व्यावसायिक उपयोग के लिए उपयुक्त है?

हां, GroupDocs.Annotation for .NET व्यवसायों के लिए वाणिज्यिक लाइसेंस प्रदान करता है।

### क्या मैं खरीदने से पहले .NET के लिए GroupDocs.Annotation की कोशिश कर सकता हूं?

 हां, एक निःशुल्क परीक्षण उपलब्ध है। आप इसका उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/).

### मुझे .NET के लिए GroupDocs.Annotation हेतु समर्थन कहां मिल सकता है?

 सहायता और अतिरिक्त संसाधन यहां उपलब्ध हैं[ग्रुपडॉक्स फ़ोरम](https://forum.groupdocs.com/c/annotation/10).

### क्या मुझे परीक्षण प्रयोजनों के लिए अस्थायी लाइसेंस की आवश्यकता है?

 आप परीक्षण के लिए अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).