---
title: GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ छवियों पर हस्ताक्षर करने के लिए मार्गदर्शिका
linktitle: मेटाडेटा के साथ छवियों पर हस्ताक्षर करने के लिए मार्गदर्शिका
second_title: GroupDocs.Signature .NET एपीआई
description: GroupDocs.Signature का उपयोग करके अपने .NET अनुप्रयोगों में मेटाडेटा के साथ छवियों पर कुशलतापूर्वक हस्ताक्षर करना सीखें। यह चरण-दर-चरण ट्यूटोरियल इंस्टॉलेशन से लेकर कार्यान्वयन तक सब कुछ कवर करता है, जिससे आप अपने दस्तावेज़ों को मेटाडेटा हस्ताक्षरों के साथ आसानी से बढ़ा सकते हैं।
type: docs
weight: 10
url: /hi/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## परिचय

GroupDocs.Signature for .NET एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को मेटाडेटा के साथ छवियों पर कुशलतापूर्वक हस्ताक्षर करने की अनुमति देती है। यह ट्यूटोरियल आपको चरण दर चरण प्रक्रिया के माध्यम से मार्गदर्शन करेगा।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें हैं:

1.  .NET के लिए GroupDocs.Signature: अपने .NET प्रोजेक्ट में GroupDocs.Signature पैकेज स्थापित करें। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/signature/net/).
2. छवि फ़ाइल: वह छवि फ़ाइल तैयार करें जिस पर आप मेटाडेटा के साथ हस्ताक्षर करना चाहते हैं.

## आवश्यक नामस्थान आयात करें

अपने C# कोड में, निम्नलिखित नामस्थान आयात करें:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## चरण 1: अपनी छवि फ़ाइल लोड करें

अपनी छवि फ़ाइल का पथ और हस्ताक्षरित छवि के लिए आउटपुट निर्देशिका निर्दिष्ट करके आरंभ करें:

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## चरण 2: मेटाडेटा हस्ताक्षर बनाएँ

इसके बाद, मेटाडेटा हस्ताक्षर बनाएं और उन्हें हस्ताक्षर विकल्पों में जोड़ें:

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; // मेटाडेटा के लिए आरंभिक आईडी
    MetadataSignOptions options = new MetadataSignOptions();

    //विभिन्न प्रकार के मेटाडेटा हस्ताक्षर जोड़ें
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) // स्ट्रिंग वैल्यू
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          // दिनांकसमय मान
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                // पूर्णांक मान
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              // दोहरा मूल्य
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              // दशमलव मान
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             // फ्लोट मूल्य

    // दस्तावेज़ पर हस्ताक्षर करें और परिणाम सहेजें
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## निष्कर्ष

इस ट्यूटोरियल में, आपने .NET के लिए GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ छवि पर हस्ताक्षर करना सीखा। इन चरणों का पालन करके, आप आसानी से अपने .NET अनुप्रयोगों में मेटाडेटा हस्ताक्षर जोड़ सकते हैं, जिससे आपकी छवियों की कार्यक्षमता और अखंडता बढ़ जाती है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं .NET के लिए GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ कई छवियों पर हस्ताक्षर कर सकता हूं?
हां, आप प्रत्येक छवि फ़ाइल को दोहराकर और मेटाडेटा हस्ताक्षर लागू करके एकाधिक छवियों पर हस्ताक्षर कर सकते हैं।

### क्या .NET के लिए GroupDocs.Signature का कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप परीक्षण संस्करण यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).

### क्या GroupDocs.Signature for .NET छवियों के अलावा अन्य फ़ाइल स्वरूपों का समर्थन करता है?
बिल्कुल! GroupDocs.Signature पीडीएफ, वर्ड, एक्सेल और अधिक सहित विभिन्न प्रारूपों का समर्थन करता है।

### क्या मैं मेटाडेटा हस्ताक्षर के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप फ़ॉन्ट आकार, रंग और मेटाडेटा हस्ताक्षर की स्थिति जैसे पहलुओं को अनुकूलित कर सकते हैं।

### मुझे .NET के लिए GroupDocs.Signature का समर्थन कहां से मिल सकता है?
 सहायता के लिए, GroupDocs.Signature फ़ोरम पर जाएँ[यहाँ](https://forum.groupdocs.com/c/signature/13).