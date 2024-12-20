---
title: भरा हुआ आयत बनाना
linktitle: भरा हुआ आयत बनाना
second_title: .NET API संदर्भ के लिए Aspose.PDF
description: इस चरण-दर-चरण ट्यूटोरियल में .NET के लिए Aspose.PDF के साथ PDF हेरफेर की शक्ति को अनलॉक करें। भरे हुए आयतों को बनाकर प्रोग्रामेटिक रूप से आकर्षक PDF दस्तावेज़ बनाने का तरीका जानें।
type: docs
weight: 50
url: /hi/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## परिचय

क्या आपने कभी प्रोग्रामेटिक रूप से शानदार PDF बनाना चाहा है? अगर हाँ, तो आप सही जगह पर हैं! इस ट्यूटोरियल में, हम .NET के लिए Aspose.PDF के बारे में जानेंगे, जो एक शक्तिशाली लाइब्रेरी है जो PDF दस्तावेज़ में हेरफेर को सरल बनाती है। आज, हम PDF फ़ाइल के भीतर एक भरा हुआ आयत बनाने पर ध्यान केंद्रित करेंगे। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, यह गाइड आपको प्रत्येक चरण को एक दोस्ताना और आकर्षक तरीके से समझाएगा। तो, अपनी कोडिंग टोपी पकड़ो, और चलो शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. विजुअल स्टूडियो: अपनी मशीन पर विजुअल स्टूडियो स्थापित करें, क्योंकि यह .NET विकास के लिए एक उत्कृष्ट IDE है।
2. .NET के लिए Aspose.PDF: Aspose.PDF लाइब्रेरी को यहां से डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.aspose.com/pdf/net/).
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होने से आपको कोड स्निपेट को बेहतर ढंग से समझने में मदद मिलेगी।

## चरण 1: एक नया प्रोजेक्ट बनाएं

1. विज़ुअल स्टूडियो खोलें और एक नया कंसोल एप्लिकेशन प्रोजेक्ट बनाएं।
2. अपनी परियोजना का उचित नाम रखें।

## चरण 2: Aspose.PDF संदर्भ जोड़ें

1. समाधान एक्सप्लोरर में अपने प्रोजेक्ट पर राइट-क्लिक करें।
2. NuGet पैकेज प्रबंधित करें चुनें.
3. Aspose.PDF खोजें और नवीनतम संस्करण स्थापित करें।

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

अब जब हमने सब कुछ सेट कर लिया है, तो चलिए कोड पर आते हैं!

## चरण 3: अपनी दस्तावेज़ निर्देशिका सेट करें

वह पथ निर्दिष्ट करें जहां आपका PDF सहेजा जाएगा:

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` अपनी मशीन पर उस वास्तविक पथ के साथ जहां आप पीडीएफ को सहेजना चाहते हैं।

## चरण 4: दस्तावेज़ इंस्टेंस बनाएँ

एक नया PDF दस्तावेज़ आरंभ करें:

```csharp
//दस्तावेज़ उदाहरण बनाएँ
Document doc = new Document();
```

## चरण 5: दस्तावेज़ में एक पृष्ठ जोड़ें

हर PDF में कम से कम एक पेज होना चाहिए। चलिए एक पेज जोड़ते हैं:

```csharp
// पीडीएफ फाइल के पेज टू पेज संग्रह को जोड़ें
Page page = doc.Pages.Add();
```

## चरण 6: ग्राफ़ इंस्टेंस बनाएँ

 ए`Graph` उदाहरण आकृतियाँ बनाने के लिए कैनवास के रूप में कार्य करता है:

```csharp
// ग्राफ़ इंस्टेंस बनाएँ
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## चरण 7: पेज पर ग्राफ़ जोड़ें

पृष्ठ पर ग्राफ संलग्न करें:

```csharp
// पेज इंस्टेंस के पैराग्राफ़ संग्रह में ग्राफ़ ऑब्जेक्ट जोड़ें
page.Paragraphs.Add(graph);
```

## चरण 8: एक आयत उदाहरण बनाएँ

आयत की स्थिति और आकार निर्धारित करें:

```csharp
// आयत उदाहरण बनाएँ
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## चरण 9: भरण रंग निर्दिष्ट करें

अपने आयत के लिए एक रंग चुनें। इस उदाहरण के लिए, हम लाल रंग का उपयोग करेंगे:

```csharp
// ग्राफ़ ऑब्जेक्ट के लिए भरण रंग निर्दिष्ट करें
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## चरण 10: ग्राफ़ में आयत जोड़ें

आयत को ग्राफ में जोड़ें:

```csharp
// ग्राफ़ ऑब्जेक्ट के आकार संग्रह में आयत ऑब्जेक्ट जोड़ें
graph.Shapes.Add(rect);
```

## चरण 11: पीडीएफ दस्तावेज़ सहेजें

अंत में, अपने दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// पीडीएफ फाइल सहेजें
doc.Save(dataDir);
```

## चरण 12: पुष्टिकरण संदेश

सफलता दर्शाने के लिए एक पुष्टिकरण संदेश प्रिंट करें:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.PDF का उपयोग करके PDF दस्तावेज़ में सफलतापूर्वक एक भरा हुआ आयत बनाया है। यह शक्तिशाली लाइब्रेरी PDF हेरफेर के लिए संभावनाओं की एक दुनिया खोलती है, जिससे आप प्रोग्रामेटिक रूप से शानदार दस्तावेज़ बना सकते हैं। चाहे आप रिपोर्ट, चालान या किसी अन्य प्रकार का PDF बना रहे हों, Aspose.PDF आपके लिए है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.PDF क्या है?
.NET के लिए Aspose.PDF एक लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से PDF दस्तावेज़ बनाने, हेरफेर करने और परिवर्तित करने की अनुमति देती है।

### क्या मैं Aspose.PDF का निःशुल्क उपयोग कर सकता हूँ?
 हां, Aspose एक निःशुल्क परीक्षण संस्करण प्रदान करता है जिसका उपयोग आप लाइब्रेरी की विशेषताओं का पता लगाने के लिए कर सकते हैं। आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/).

### क्या Aspose.PDF के लिए समर्थन पाने का कोई तरीका है?
 बिल्कुल! आप Aspose फ़ोरम के ज़रिए सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.aspose.com/c/pdf/10).

### मैं Aspose.PDF कैसे खरीद सकता हूँ?
 आप खरीद पृष्ठ पर जाकर Aspose.PDF खरीद सकते हैं[यहाँ](https://purchase.aspose.com/buy).

### मैं Aspose.PDF के साथ किस प्रकार की आकृतियाँ बना सकता हूँ?
आप Aspose.PDF लाइब्रेरी का उपयोग करके आयत, वृत्त, रेखाएँ आदि सहित विभिन्न आकृतियाँ बना सकते हैं।