---
title: .NET के लिए Aspose.PDF का उपयोग करके स्टाइलिश क्रमांकित सूचियाँ
linktitle: .NET के लिए Aspose.PDF का उपयोग करके स्टाइलिश क्रमांकित सूचियाँ
second_title: .NET API संदर्भ के लिए Aspose.PDF
description: जानें कि .NET के लिए Aspose.PDF के साथ अपने PDF दस्तावेज़ों में खूबसूरती से क्रमांकित सूचियाँ कैसे बनाएँ। यह मार्गदर्शिका आपको रोमन अंकों जैसी विभिन्न नंबरिंग शैलियों को लागू करने की प्रक्रिया से गुज़ारती है।
type: docs
weight: 10
url: /hi/net/programming-with-headings/stylish-numbered-lists/
---
## परिचय

क्या आपको कभी अपने PDF दस्तावेज़ों में अच्छी तरह से संरचित, क्रमांकित सूचियाँ बनाने की ज़रूरत पड़ी है? चाहे वह कानूनी कागजात, रिपोर्ट या प्रस्तुतियों के लिए हो, प्रभावी क्रमांकन शैलियाँ आपकी सामग्री को व्यवस्थित करने के लिए महत्वपूर्ण हैं। .NET के लिए Aspose.PDF के साथ, आप आसानी से अपने PDF शीर्षकों पर विभिन्न क्रमांकन शैलियों को लागू कर सकते हैं, जिसके परिणामस्वरूप पॉलिश और पेशेवर दस्तावेज़ बनते हैं।

## आवश्यक शर्तें

इससे पहले कि हम कोडिंग शुरू करें, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें तैयार हैं:

1.  .NET के लिए Aspose.PDF: यहां से नवीनतम संस्करण डाउनलोड करें[यहाँ](https://releases.aspose.com/pdf/net/).
2. विकास वातावरण: आपको विज़ुअल स्टूडियो या किसी .NET-संगत IDE की आवश्यकता होगी।
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके पास .NET फ्रेमवर्क 4.0 या उच्चतर संस्करण स्थापित है।
4.  लाइसेंस: आप अस्थायी लाइसेंस का उपयोग कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/) या अन्वेषण करें[मुफ्त परीक्षण](https://releases.aspose.com/) विकल्प.

## आवश्यक पैकेज आयात करना

अपने प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके प्रारंभ करें:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## चरण 1: दस्तावेज़ सेट करना

आइए एक नया पीडीएफ दस्तावेज़ बनाकर और पृष्ठ आकार और मार्जिन सहित इसके लेआउट को कॉन्फ़िगर करके शुरू करें।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// पृष्ठ आयाम और मार्जिन सेट करें
pdfDoc.PageInfo.Width = 612.0; // 8.5 इंच
pdfDoc.PageInfo.Height = 792.0; // 11 इंच
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // 1 इंच मार्जिन
```

यह सेटअप आपके दस्तावेज़ को सभी तरफ एक इंच मार्जिन के साथ एक मानक अक्षर आकार देता है।

## चरण 2: पीडीएफ में पेज जोड़ना

इसके बाद, हम पीडीएफ दस्तावेज़ में एक रिक्त पृष्ठ जोड़ेंगे, जहां हम बाद में क्रमांकन शैलियाँ लागू करेंगे।

```csharp
// PDF दस्तावेज़ में नया पृष्ठ जोड़ें
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // दस्तावेज़ के समान सेटिंग्स का उपयोग करें
```

## चरण 3: फ़्लोटिंग बॉक्स बनाना

फ्लोटिंगबॉक्स आपको पृष्ठ के प्रवाह से स्वतंत्र रूप से सामग्री को रखने की अनुमति देता है, जिससे आपको अपने लेआउट पर अधिक नियंत्रण मिलता है।

```csharp
//संरचित सामग्री के लिए फ़्लोटिंगबॉक्स बनाएँ
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## चरण 4: रोमन अंकों के साथ शीर्षक जोड़ना

अब, आइए हम अपने पहले शीर्षक को छोटे रोमन अंकों के साथ जोड़ते हैं।

```csharp
// रोमन अंकों के साथ पहला शीर्षक बनाएँ
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## चरण 5: कस्टम आरंभिक संख्या के साथ दूसरा शीर्षक जोड़ना

इसके बाद, हम रोमन अंक 13 से शुरू करते हुए दूसरा शीर्षक जोड़ेंगे।

```csharp
// रोमन अंक 13 से शुरू करते हुए दूसरा शीर्षक बनाएं
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## चरण 6: वर्णमाला क्रमांकन के साथ शीर्षक जोड़ना

विविधता के लिए, आइए लोअरकेस में वर्णमाला क्रमानुसार संख्या का उपयोग करते हुए एक तीसरा शीर्षक जोड़ें।

```csharp
// वर्णमाला क्रमांकन के साथ शीर्षक बनाएं
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## चरण 7: पीडीएफ को सेव करना

अंत में, पीडीएफ फाइल को अपनी इच्छित डायरेक्टरी में सेव करें।

```csharp
// पीडीएफ दस्तावेज़ सहेजें
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.PDF का उपयोग करके PDF फ़ाइल में शीर्षकों पर विभिन्न नंबरिंग शैलियों—रोमन अंक और वर्णमाला—को सफलतापूर्वक लागू किया है। Aspose.PDF की लचीलापन आपको पृष्ठ लेआउट, नंबरिंग शैलियों और सामग्री स्थिति को नियंत्रित करने की अनुमति देता है, जिससे आप सुव्यवस्थित और पेशेवर PDF दस्तावेज़ बनाने में सक्षम होते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं एक ही PDF दस्तावेज़ पर अलग-अलग संख्या शैलियाँ लागू कर सकता हूँ?  
हां, आप एक ही दस्तावेज़ में विभिन्न संख्याकरण शैलियों, जैसे रोमन अंक, अरबी अंक और वर्णमाला क्रमांकन को मिश्रित कर सकते हैं।

### मैं शीर्षकों के लिए प्रारंभिक संख्या को कैसे अनुकूलित कर सकता हूँ?  
 आप किसी भी शीर्षक के लिए प्रारंभिक संख्या निर्धारित कर सकते हैं`StartNumber` संपत्ति।

### क्या क्रमांकन अनुक्रम को रीसेट करने का कोई तरीका है?  
 हां, आप नंबरिंग को समायोजित करके रीसेट कर सकते हैं`StartNumber` प्रत्येक शीर्षक के लिए संपत्ति.

### क्या मैं क्रमांकन के अतिरिक्त शीर्षकों पर बोल्ड या इटैलिक स्टाइलिंग भी लागू कर सकता हूँ?  
 बिलकुल! आप फ़ॉन्ट, आकार, बोल्ड और इटैलिक जैसे गुणों को संशोधित करके शीर्षक शैलियों को अनुकूलित कर सकते हैं`TextState` वस्तु।

### मैं Aspose.PDF के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?  
 आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/)Aspose.PDF को बिना किसी प्रतिबंध के परीक्षण करने के लिए।