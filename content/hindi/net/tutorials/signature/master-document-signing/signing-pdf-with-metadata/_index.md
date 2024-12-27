---
title: GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ PDF पर हस्ताक्षर करने के लिए मार्गदर्शिका
linktitle: मेटाडेटा के साथ PDF पर हस्ताक्षर करने के लिए मार्गदर्शिका
second_title: GroupDocs.Signature .NET एपीआई
description: .NET के लिए GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ हस्ताक्षर करके अपने PDF दस्तावेज़ों को बेहतर सुरक्षा और पता लगाने की क्षमता के साथ सुदृढ़ करना सीखें। यह व्यापक ट्यूटोरियल एक स्पष्ट प्रदान करता है।
type: docs
weight: 11
url: /hi/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## परिचय

इस ट्यूटोरियल में, हम सीखेंगे कि PDF दस्तावेज़ पर हस्ताक्षर कैसे करें और .NET के लिए GroupDocs.Signature का उपयोग करके मेटाडेटा कैसे जोड़ें। मेटाडेटा जोड़ने से लेखकत्व, निर्माण तिथि, दस्तावेज़ आईडी, और अधिक जैसी आवश्यक जानकारी प्रदान करके दस्तावेज़ को बेहतर बनाया जाता है।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  .NET के लिए GroupDocs.Signature: इसे यहाँ से डाउनलोड करें[यहाँ](https://releases.groupdocs.com/signature/net/).
2. एक पीडीएफ दस्तावेज़: हस्ताक्षर के लिए एक नमूना पीडीएफ फाइल तैयार रखें।
3. C# प्रोग्रामिंग का बुनियादी ज्ञान: कोड उदाहरणों को समझने के लिए C# सिंटैक्स से परिचित होना आवश्यक है।

## नामस्थान आयात करें

आवश्यक वर्गों और विधियों तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करके प्रारंभ करें:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## चरण 1: पीडीएफ दस्तावेज़ लोड करें

उस PDF दस्तावेज़ का पथ निर्दिष्ट करें जिस पर आप हस्ताक्षर करना चाहते हैं:

```csharp
string filePath = "sample.pdf";
```

## चरण 2: आउटपुट फ़ाइल पथ निर्दिष्ट करें

मेटाडेटा के साथ हस्ताक्षरित PDF को कहाँ सहेजा जाएगा, यह निर्धारित करें:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## चरण 3: हस्ताक्षर इंस्टेंस बनाएँ

 आरंभ करें`Signature` पीडीएफ दस्तावेज़ के पथ के साथ उदाहरण:

```csharp
using (Signature signature = new Signature(filePath))
{
    // हस्ताक्षर से संबंधित कोड यहां जाएगा
}
```

## चरण 4: मेटाडेटा विकल्प परिभाषित करें

 बनाएं`MetadataSignOptions` और मेटाडेटा फ़ील्ड को उनके मानों के साथ जोड़ें:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // स्ट्रिंग वैल्यू
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // दिनांकसमय मान
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // पूर्णांक मान
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // दोहरा मूल्य
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // दशमलव मान
    .Add(new PdfMetadataSignature("Total", 123.456F));              // फ्लोट मूल्य
```

## चरण 5: दस्तावेज़ पर हस्ताक्षर करें

निर्दिष्ट मेटाडेटा विकल्पों के साथ PDF दस्तावेज़ पर हस्ताक्षर करें और हस्ताक्षरित दस्तावेज़ को सहेजें:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Signature का उपयोग करके मेटाडेटा के साथ PDF दस्तावेज़ पर हस्ताक्षर करने का तरीका बताया। इन चरणों का पालन करके, आप आसानी से अपनी PDF फ़ाइलों को मूल्यवान मेटाडेटा से समृद्ध कर सकते हैं, उनकी ट्रेसबिलिटी और उपयोगिता में सुधार कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं अपने PDF दस्तावेज़ों में कस्टम मेटाडेटा फ़ील्ड जोड़ सकता हूँ?

हां, आप .NET के लिए GroupDocs.Signature का उपयोग करके फ़ील्ड नाम और उसके संबंधित मान निर्दिष्ट करके कस्टम मेटाडेटा फ़ील्ड जोड़ सकते हैं।

### क्या GroupDocs.Signature for .NET .NET फ्रेमवर्क के सभी संस्करणों के साथ संगत है?

.NET के लिए GroupDocs.Signature .NET फ्रेमवर्क के विभिन्न संस्करणों के साथ संगत है, जो लचीलापन और एकीकरण की आसानी सुनिश्चित करता है।

### क्या GroupDocs.Signature PDF के अलावा अन्य दस्तावेज़ प्रारूपों पर हस्ताक्षर करने का समर्थन करता है?

हां, GroupDocs.Signature Word, Excel, PowerPoint और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।

### क्या मैं .NET के लिए GroupDocs.Signature का उपयोग करके कई दस्तावेजों पर सामूहिक रूप से हस्ताक्षर कर सकता हूं?

बिल्कुल! आप फ़ाइलों की सूची के माध्यम से पुनरावृत्ति करके और हस्ताक्षर प्रक्रिया को प्रोग्रामेटिक रूप से लागू करके कई दस्तावेज़ों पर थोक में हस्ताक्षर कर सकते हैं।

### क्या GroupDocs.Signature उपयोगकर्ताओं के लिए तकनीकी सहायता उपलब्ध है?

 हां, GroupDocs अपने मंचों के माध्यम से समर्पित तकनीकी सहायता प्रदान करता है। आप सहायता फ़ोरम तक पहुँच सकते हैं[यहाँ](https://forum.groupdocs.com/c/signature/13).