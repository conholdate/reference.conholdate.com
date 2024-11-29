---
title: .NET के लिए Aspose.CAD में DGN को PDF में बदलें
linktitle: .NET के लिए Aspose.CAD में DGN को PDF में बदलें
second_title: Aspose.CAD .NET - CAD और BIM फ़ाइल प्रारूप
description: .NET के लिए शक्तिशाली Aspose.CAD लाइब्रेरी का उपयोग करके DGN फ़ाइलों को आसानी से PDF में कनवर्ट करना सीखें। यह चरण-दर-चरण मार्गदर्शिका सभी स्तरों के डेवलपर्स के लिए डिज़ाइन की गई है।
type: docs
weight: 12
url: /hi/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## परिचय

CAD फ़ाइलों की दुनिया में नेविगेट करना चुनौतीपूर्ण हो सकता है, लेकिन Aspose.CAD for .NET के साथ, डेवलपर्स आसानी से विभिन्न CAD प्रारूपों में हेरफेर और रूपांतरण कर सकते हैं। एक आम ज़रूरत DGN फ़ाइलों को PDF में बदलना है, जिसे हम इस ट्यूटोरियल में चरण दर चरण समझेंगे।

## आवश्यक शर्तें

साथ चलने के लिए, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- C# और .NET फ्रेमवर्क में बुनियादी दक्षता।
-  Aspose.CAD for .NET लाइब्रेरी स्थापित है। आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/cad/net/).
- एक नमूना DGN फ़ाइल (जैसे, Nikon_D90_Camera.dgn)। 

## चरण 1: आवश्यक नामस्थान आयात करें

अपने C# प्रोजेक्ट में प्रासंगिक नामस्थानों को आयात करके प्रारंभ करें:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## चरण 2: DGN फ़ाइल लोड करें

अपनी DGN फ़ाइल के लिए निर्देशिका निर्दिष्ट करें और उसे निम्नलिखित कोड का उपयोग करके लोड करें:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // अतिरिक्त प्रसंस्करण यहां किया जाएगा...
}
```

## चरण 3: रास्टराइज़ेशन विकल्प कॉन्फ़िगर करें

इसके बाद, यह निर्धारित करने के लिए कि आपका DGN PDF में किस प्रकार प्रस्तुत किया जाएगा, रास्टराइज़ेशन विकल्प सेट करें:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // आवश्यकतानुसार चौड़ाई समायोजित करें
    PageHeight = 300, // आवश्यकतानुसार ऊंचाई समायोजित करें
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## चरण 4: पीडीएफ विकल्प बनाएँ

पहले से कॉन्फ़िगर की गई रास्टराइजेशन सेटिंग्स को एकीकृत करते हुए, PDF विकल्प परिभाषित करें:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## चरण 5: DGN को PDF के रूप में सहेजें

अंत में, आपके द्वारा कॉन्फ़िगर किए गए विकल्पों का उपयोग करके DGN फ़ाइल को PDF के रूप में सहेजें:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.CAD का उपयोग करके DGN फ़ाइल को सफलतापूर्वक PDF में परिवर्तित कर लिया है। इस सरल ट्यूटोरियल ने आपको DGN फ़ाइल लोड करने, रास्टराइज़ेशन विकल्प सेट करने और आउटपुट को PDF के रूप में सहेजने के बारे में मार्गदर्शन किया।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मुझे Aspose.CAD का उपयोग करने के लिए पूर्व CAD ज्ञान की आवश्यकता है?  
बिल्कुल! Aspose.CAD को जटिल CAD कार्यों को सरल बनाने के लिए डिज़ाइन किया गया है, जिससे यह सभी डेवलपर्स के लिए सुलभ हो जाता है, चाहे उनके CAD ज्ञान की परवाह किए बिना।

### मैं Aspose.CAD के लिए अधिक संसाधन और दस्तावेज़ कहां पा सकता हूं?  
 आप विस्तृत मार्गदर्शिकाएँ और उदाहरण देख सकते हैं[Aspose.CAD दस्तावेज़ीकरण](https://reference.aspose.com/cad/net/).

### क्या Aspose.CAD के लिए कोई निःशुल्क परीक्षण उपलब्ध है?  
 हां, निःशुल्क परीक्षण प्राप्त किया जा सकता है[यहाँ](https://releases.aspose.com/).

### मैं Aspose.CAD के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?  
 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.conholdate.com/temporary-license/).

### क्या आपको सहायता चाहिए या आपके पास प्रश्न हैं?  
 बातचीत में शामिल हों[Aspose.CAD मंच](https://forum.aspose.com/c/cad/19) सामुदायिक सहायता और पूछताछ के लिए।