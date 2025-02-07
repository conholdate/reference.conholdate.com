---
title: पीडीएफ फाइल में जावा स्क्रिप्ट जोड़ना
linktitle: जावा स्क्रिप्ट पीडीएफ फाइल जोड़ें
second_title: .NET API संदर्भ के लिए Aspose.PDF
description: यह दस्तावेज़ .NET के लिए Aspose.PDF का उपयोग करके PDF दस्तावेज़ों में पॉप-अप अलर्ट या ऑटो-प्रिंट फ़ंक्शन जैसे इंटरैक्टिव तत्वों को जोड़ने के लिए एक व्यापक मार्गदर्शिका प्रदान करता है।
type: docs
weight: 10
url: /hi/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## परिचय
यह दस्तावेज़ .NET के लिए Aspose.PDF का उपयोग करके PDF दस्तावेज़ों में पॉप-अप अलर्ट या ऑटो-प्रिंट फ़ंक्शन जैसे इंटरैक्टिव तत्व जोड़ने के लिए एक व्यापक मार्गदर्शिका प्रदान करता है। इस लाइब्रेरी की क्षमताओं का लाभ उठाकर, आप गतिशील और आकर्षक PDF बना सकते हैं जो विभिन्न उपयोगकर्ता आवश्यकताओं को पूरा करते हैं।

## आवश्यक शर्तें
 आगे बढ़ने से पहले, सुनिश्चित करें कि आपने .NET के लिए Aspose.PDF का नवीनतम संस्करण डाउनलोड किया है[एस्पोज रिलीज](https://releases.aspose.com/pdf/net/) या उनकी वेबसाइट के माध्यम से निःशुल्क परीक्षण प्राप्त करें:[releases.aspose.com](http://releases.aspose.com).

आपको C# की बुनियादी समझ भी होनी चाहिए और आप जिस डेवलपमेंट एनवायरनमेंट का इस्तेमाल कर रहे हैं, उससे परिचित होना चाहिए। इसके अतिरिक्त, अगर आपको अपनी डेवलपमेंट प्रक्रिया के दौरान सीमाओं से बचने की ज़रूरत है, तो Aspose से अस्थायी लाइसेंस प्राप्त करने पर विचार करें।

## आवश्यक पैकेज आयात करना
कोड लिखना शुरू करने के लिए, Aspose.PDF लाइब्रेरी से आवश्यक नेमस्पेस आयात करें:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## चरण 1: मौजूदा पीडीएफ लोड करना
एक मौजूदा PDF दस्तावेज़ लोड करें जिसमें आप इंटरैक्टिव तत्व जोड़ना चाहते हैं:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` अपनी पीडीएफ फाइल के वास्तविक पथ के साथ।

## चरण 2: दस्तावेज़ स्तर पर जावास्क्रिप्ट जोड़ना

 दस्तावेज़ खुलने पर ट्रिगर होने वाली स्क्रिप्ट लागू करने के लिए, एक इंस्टैंसिएट करें`JavascriptAction` वस्तु:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## चरण 3: पेज स्तर पर जावास्क्रिप्ट जोड़ना

 पृष्ठ खुलने या बंद होने के आधार पर विशिष्ट क्रियाएं शुरू करने के लिए, एक इंस्टैंशियट बनाएं`JavascriptAction` प्रत्येक पृष्ठ के लिए ऑब्जेक्ट:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## चरण 4: पीडीएफ दस्तावेज़ को सहेजना

संशोधित PDF दस्तावेज़ को सहेजने के लिए, आउटपुट फ़ाइल पथ निर्दिष्ट करें:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## निष्कर्ष
इस गाइड का पालन करके और .NET के लिए Aspose.PDF का उपयोग करके, आप अपने PDF को इंटरैक्टिव तत्वों के साथ प्रभावी ढंग से बढ़ा सकते हैं। यह लाइब्रेरी गतिशील और आकर्षक दस्तावेज़ बनाने के लिए एक व्यापक समाधान प्रदान करती है जो विभिन्न उपयोगकर्ता आवश्यकताओं को पूरा करती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं PDF में विभिन्न पृष्ठों पर एकाधिक JavaScript क्रियाएँ जोड़ सकता हूँ?
हां, आप अलग-अलग पृष्ठों या संपूर्ण दस्तावेज़ को अलग-अलग जावास्क्रिप्ट क्रियाएं असाइन कर सकते हैं।

### क्या पीडीएफ में जावास्क्रिप्ट जोड़ने के बाद उसे हटाना संभव है?
 हां, आप मौजूदा जावास्क्रिप्ट क्रियाओं को हटा या संशोधित कर सकते हैं`Actions` दस्तावेज़ या पृष्ठ के गुण.

### मैं पीडीएफ में किस प्रकार के जावास्क्रिप्ट फ़ंक्शन का उपयोग कर सकता हूँ?
आप एडोब एक्रोबेट के जावास्क्रिप्ट इंजन द्वारा समर्थित किसी भी जावास्क्रिप्ट का उपयोग कर सकते हैं, जैसे प्रिंटिंग, अलर्ट और फॉर्म मैनीपुलेशन।

### क्या जावास्क्रिप्ट सभी पीडीएफ व्यूअर्स में काम करता है?
अधिकांश जावास्क्रिप्ट क्रियाएँ PDF व्यूअर में काम करेंगी जो Adobe Acrobat जैसे इंटरैक्टिव PDF का समर्थन करते हैं। हालाँकि, कुछ बुनियादी PDF रीडर जावास्क्रिप्ट का समर्थन नहीं कर सकते हैं।