---
title: .NET के लिए GroupDocs.Annotation के साथ बटन घटक जोड़ना
linktitle: बटन घटक जोड़ना
second_title: GroupDocs.Annotation .NET एपीआई
description: .NET के लिए GroupDocs.Annotation का उपयोग करके इंटरैक्टिव बटन घटकों को जोड़कर अपने पीडीएफ दस्तावेज़ों को बेहतर बनाने का तरीका जानें। यह चरण-दर-चरण ट्यूटोरियल है।
type: docs
weight: 10
url: /hi/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## परिचय

इस ट्यूटोरियल में, हम आपको .NET के लिए GroupDocs.Annotation लाइब्रेरी का उपयोग करके PDF दस्तावेज़ में बटन घटक जोड़ने की सरल प्रक्रिया से परिचित कराएँगे। इस गाइड के अंत तक, आप अपने PDF दस्तावेज़ों को इंटरैक्टिव सुविधाओं के साथ बेहतर बनाने में सक्षम हो जाएँगे।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीज़ें मौजूद हैं:

1.  .NET के लिए GroupDocs.Annotation: .NET लाइब्रेरी के लिए GroupDocs.Annotation डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: .NET फ्रेमवर्क स्थापित करके उपयुक्त विकास परिवेश स्थापित करें।

## चरण 1: आवश्यक नामस्थान आयात करें

अपने प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके प्रारंभ करें:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## चरण 2: आउटपुट पथ आरंभ करें

आउटपुट पथ निर्धारित करें जहां संशोधित PDF सहेजा जाएगा:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## चरण 3: बटन घटक जोड़ें

अब, आइए बटन घटक बनाएं और उसे अपने पीडीएफ में जोड़ें:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // बटन की स्थिति और आकार
        PenColor = 65535,                       // बटन बॉर्डर का रंग
        Style = BorderStyle.Dashed,             // सीमा शैली
        BorderWidth = 0,                        // सीमा की चौड़ाई
        BorderColor = 0,                        // सीमा रंग
        AlternateName = "Name",                 //बटन का वैकल्पिक नाम
        PartialName = "Partial Name",           // बटन का आंशिक नाम
        NormalCaption = "Caption",               // बटन पर प्रदर्शित पाठ
        ButtonColor = 16761035,                 // बटन का पृष्ठभूमि रंग
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // एनोटेटर में बटन जोड़ें
    annotator.Save("result.pdf"); // संशोधित पीडीएफ को सहेजें
}
```

## चरण 4: आउटपुट पथ प्रदर्शित करें

अंत में, उपयोगकर्ता को सूचित करें कि आउटपुट फ़ाइल कहाँ सहेजी गई है:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

बधाई हो! आपने .NET के लिए GroupDocs.Annotation का उपयोग करके PDF दस्तावेज़ में बटन घटक को सफलतापूर्वक जोड़ दिया है।

## निष्कर्ष

इस ट्यूटोरियल में, हमने दिखाया कि .NET के लिए GroupDocs.Annotation के साथ PDF दस्तावेज़ों में बटन घटकों को कैसे शामिल किया जाए। इन चरणों का पालन करके, आप अपने PDF दस्तावेज़ों की अन्तरक्रियाशीलता को महत्वपूर्ण रूप से बढ़ा सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं बटन के स्वरूप को अनुकूलित कर सकता हूँ?

बिल्कुल! आप अपनी आवश्यकताओं के अनुरूप आकार, रंग और शैली जैसे विभिन्न गुणों को संशोधित कर सकते हैं।

### क्या GroupDocs.Annotation for .NET सभी PDF संस्करणों के साथ संगत है?

हां, GroupDocs.Annotation for .NET पीडीएफ संस्करणों की एक विस्तृत श्रृंखला का समर्थन करता है, जो अधिकांश दस्तावेजों के साथ संगतता सुनिश्चित करता है।

### क्या मैं एक एकल PDF दस्तावेज़ में एकाधिक बटन घटक जोड़ सकता हूँ?

हां, आप किसी पीडीएफ दस्तावेज़ में आवश्यकतानुसार जितने बटन घटक हों, जोड़ सकते हैं।

### क्या GroupDocs.Annotation for .NET अन्य फ़ाइल स्वरूपों का समर्थन करता है?

हां, यह पीडीएफ के अलावा DOCX, PPTX और XLSX सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है।

### क्या परीक्षण के उद्देश्य से कोई परीक्षण संस्करण उपलब्ध है?

 हां, आप .NET के लिए GroupDocs.Annotation के एक निःशुल्क परीक्षण को एक्सेस कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
