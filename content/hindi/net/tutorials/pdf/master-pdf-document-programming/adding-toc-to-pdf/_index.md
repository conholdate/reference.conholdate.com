---
title: पीडीएफ दस्तावेज़ में विषय-सूची जोड़ना
linktitle: पीडीएफ दस्तावेज़ में विषय-सूची जोड़ना
second_title: .NET API संदर्भ के लिए Aspose.PDF
description: यह ट्यूटोरियल दर्शाता है कि .NET के लिए Aspose.Pdf का उपयोग करके PDF दस्तावेज़ में सामग्री तालिका (TOC) कैसे जोड़ें।
type: docs
weight: 40
url: /hi/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## परिचय

PDF दस्तावेज़ में विषय-सूची (TOC) बनाने से इसकी नेविगेशन और पहुँच क्षमता में काफ़ी सुधार हो सकता है। इस गाइड में, हम दिखाएंगे कि .NET के लिए Aspose.Pdf का उपयोग करके PDF फ़ाइल में TOC कैसे जोड़ा जाता है।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.   .NET के लिए Aspose.PDF: यहां से नवीनतम संस्करण डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.aspose.com/pdf/net/).
2.  विकास परिवेश: Visual Studio जैसा .NET विकास परिवेश सेट अप करें.
3.   लाइसेंस: यदि आवश्यक हो तो अस्थायी लाइसेंस का अनुरोध करें; कृपया यहां जाएं[Aspose.Pdf लाइसेंसिंग पृष्ठ](https://asposepdf.com/developers) अधिक जानकारी के लिए.

आवश्यक लाइब्रेरीज़ आयात करना

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## चरण 1: पीडीएफ दस्तावेज़ लोड करें

अपनी मौजूदा PDF फ़ाइल को उस स्थान पर लोड करें जहाँ आप TOC जोड़ना चाहते हैं। अपने दस्तावेज़ निर्देशिका का पथ निर्दिष्ट करें।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## चरण 2: TOC के लिए एक नया पृष्ठ डालें

पीडीएफ दस्तावेज़ की शुरुआत में एक नया पेज डालें। यह पेज विषय-सूची (TOC) के रूप में काम करेगा।

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## चरण 3: TOC सूचना ऑब्जेक्ट बनाएँ

एक ऑब्जेक्ट बनाएँ जो TOC जानकारी को दर्शाएगा। बेहतर नेविगेशन के लिए एक शीर्षक और लिंक जोड़ें।

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## चरण 4: TOC तत्वों को परिभाषित करें

TOC में प्रदर्शित होने वाले तत्वों (या शीर्षकों) को परिभाषित करें। ये तत्व पाठकों को दस्तावेज़ के विशिष्ट अनुभागों तक नेविगेट करने में मदद कर सकते हैं।

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## चरण 5: TOC शीर्षक बनाएँ

TOC में पहले दो तत्वों के लिए शीर्षक बनाएँ। ये शीर्षक अपने-अपने पृष्ठों से जुड़ेंगे।

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## चरण 6: पीडीएफ को TOC के साथ सेव करें

अंत में, अपडेट की गई पीडीएफ फाइल को सेव कर लें।

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## पुष्टिकरण संदेश

उपयोगकर्ता को यह बताने के लिए एक पुष्टिकरण संदेश प्रदर्शित करें कि प्रक्रिया पूरी हो गई है।

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## निष्कर्ष

.NET के लिए Aspose.PDF के साथ, PDF में विषय-सूची जोड़ना न केवल आसान है, बल्कि अनुकूलन योग्य भी है। चाहे आपको सरल नेविगेशन लिंक या जटिल संरचनाएँ बनाने की आवश्यकता हो, यह टूल आपके लिए है। इसलिए, अगली बार जब आप किसी लंबी PDF पर काम कर रहे हों, तो उस पेशेवर स्पर्श के लिए TOC जोड़ना न भूलें।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं Aspose.PDF में TOC के स्वरूप को अनुकूलित कर सकता हूँ?

हां, आप TOC के स्वरूप को पूरी तरह से अनुकूलित कर सकते हैं, जिसमें फ़ॉन्ट शैली, आकार और संरेखण शामिल हैं।

### मैं TOC में उपशीर्षक कैसे जोड़ूं?

आप शीर्षक समायोजित करके उपशीर्षक जोड़ सकते हैं`Heading` स्तर (जैसे,`Heading(2)`).

### क्या दस्तावेज़ में परिवर्तन होने पर TOC को स्वचालित रूप से अद्यतन करना संभव है?

नहीं, TOC अपने आप अपडेट नहीं होगा। अगर दस्तावेज़ की संरचना बदलती है, तो आपको इसे फिर से बनाना होगा।

### क्या मैं TOC प्रविष्टियों को बाह्य दस्तावेज़ों से लिंक कर सकता हूँ?

हां, आप TOC प्रविष्टियों को बाह्य PDF या URL से लिंक करने के लिए हाइपरलिंक का उपयोग कर सकते हैं।

### क्या Aspose.PDF बहु-स्तरीय TOCs का समर्थन करता है?

हां, Aspose.PDF उप-अनुभागों वाले जटिल दस्तावेज़ों के लिए बहु-स्तरीय TOCs का समर्थन करता है।
