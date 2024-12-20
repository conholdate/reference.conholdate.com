---
title: दस्तावेज़ फ़ाइल प्रारूप का पता लगाना
linktitle: दस्तावेज़ फ़ाइल प्रारूप का पता लगाना
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके विभिन्न दस्तावेज़ फ़ाइल स्वरूपों का पता लगाना और उन्हें प्रबंधित करना सीखें। व्यावहारिक उदाहरणों, युक्तियों और अक्सर पूछे जाने वाले प्रश्नों के साथ हमारी विस्तृत मार्गदर्शिका का पालन करें।
type: docs
weight: 10
url: /hi/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## परिचय

आज के डिजिटल परिदृश्य में विभिन्न दस्तावेज़ प्रारूपों को कुशलतापूर्वक प्रबंधित और व्यवस्थित करना महत्वपूर्ण है। Aspose.Words for .NET विभिन्न फ़ाइल प्रकारों का पता लगाने और उन्हें संसाधित करने के लिए एक मजबूत समाधान प्रदान करता है। इस गाइड में, हम दस्तावेज़ प्रारूपों का पता लगाने, सटीकता सुनिश्चित करने और मूल्यवान समय बचाने की चरण-दर-चरण प्रक्रिया में तल्लीन हैं।

## दस्तावेज़ पहचान के लिए पूर्वापेक्षाएँ

शुरू करने से पहले, सुनिश्चित करें कि निम्नलिखित आवश्यकताएं पूरी हों:

1. .NET लाइब्रेरी के लिए Aspose.Words  
    लाइब्रेरी को यहां से डाउनलोड करें[एस्पोज वर्ड्स रिलीज़](https://releases.aspose.com/words/net/)और वैध लाइसेंस का उपयोग करके इसे सक्रिय करें। अस्थायी लाइसेंस के लिए, यहाँ जाएँ[Aspose अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).

2. विकास पर्यावरण  
   .NET फ्रेमवर्क स्थापित करके Visual Studio (कोई भी नवीनतम संस्करण) का उपयोग करें।

3. मूल फ़ाइल सेटअप  
   अपनी इनपुट फ़ाइलों को व्यवस्थित करें और पता लगाए गए प्रारूपों को क्रमबद्ध करने के लिए निर्देशिकाएँ तैयार करें।

## आवश्यक नामस्थान आयात करें

अपने प्रोग्राम के आरंभ में इन नामस्थानों को शामिल करें:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

ये आयात फ़ाइल प्रारूप पहचान के लिए आवश्यक वर्गों और विधियों तक पहुंच प्रदान करते हैं।

## चरण 1: संगठित आउटपुट के लिए निर्देशिकाएँ आरंभ करें

फ़ाइलों को उनके ज्ञात प्रारूप के आधार पर संग्रहीत करने के लिए निर्देशिकाएँ बनाएँ।

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

// सुनिश्चित करें कि निर्देशिकाएं मौजूद हों
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

यह संरचना फ़ाइल प्रबंधन को सरल बनाती है।

## चरण 2: फ़ाइल सूची पुनर्प्राप्त करें

प्रसंस्करण को सुव्यवस्थित करने के लिए दूषित या असमर्थित दस्तावेज़ों को फ़िल्टर करें।

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

फ़िल्टर की गई सूची यह सुनिश्चित करती है कि आप केवल वैध फ़ाइलों के साथ ही काम करें।

## चरण 3: फ़ाइल स्वरूपों का पता लगाएं और उन्हें वर्गीकृत करें

प्रत्येक फ़ाइल के प्रारूप को पहचानने के लिए उसे लूप करें और उचित निर्देशिका में ले जाएं।

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    // आउटपुट का पता लगाया गया प्रारूप
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

`FileFormatUtil.DetectFileFormat`दस्तावेज़ की विशेषताओं को पहचानने के लिए यह विधि केंद्रीय है।

## निष्कर्ष

.NET के लिए Aspose.Words का लाभ उठाकर, दस्तावेज़ फ़ाइल स्वरूपों का पता लगाना एक आसान काम बन जाता है। विभिन्न स्वरूपों की पहचान करने और उन्हें वर्गीकृत करने की क्षमता निर्बाध दस्तावेज़ प्रबंधन सुनिश्चित करती है, जिससे उत्पादकता और वर्कफ़्लो दक्षता बढ़ती है।

## अक्सर पूछे जाने वाले प्रश्न

### दस्तावेज़ प्रारूपों का पता लगाने का मुख्य उद्देश्य क्या है?  
प्रारूपों का पता लगाने से विशिष्ट कार्यप्रवाहों या अनुप्रयोगों के लिए फ़ाइलों को वर्गीकृत करके दस्तावेज़ प्रबंधन को सुव्यवस्थित करने में मदद मिलती है।

### क्या Aspose.Words एन्क्रिप्टेड फ़ाइलों का समर्थन करता है?  
हां, यह एन्क्रिप्शन का पता लगा सकता है और एन्क्रिप्टेड दस्तावेजों को तदनुसार संसाधित कर सकता है।

### क्या मैं इस समाधान को अन्य फ़ाइल प्रकारों के लिए विस्तारित कर सकता हूँ?  
हां, आप अतिरिक्त प्रारूपों को शामिल करने या अन्य Aspose लाइब्रेरीज़ को एकीकृत करने के लिए कोड को संशोधित कर सकते हैं।

### मैं अज्ञात प्रारूपों को कैसे संभालूँ?  
अज्ञात प्रारूपों को मैन्युअल निरीक्षण या विशेष उपकरणों के साथ आगे की प्रक्रिया के लिए अलग से संग्रहीत करें।

### मुझे अतिरिक्त दस्तावेज़ कहां मिल सकते हैं?  
 दौरा करना[Aspose.Words दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) विस्तृत मार्गदर्शिका और उदाहरण के लिए.
