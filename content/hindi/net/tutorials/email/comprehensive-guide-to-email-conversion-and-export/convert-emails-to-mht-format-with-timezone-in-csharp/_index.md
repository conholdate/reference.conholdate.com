---
title: C# में टाइमज़ोन के साथ ईमेल को MHT प्रारूप में बदलें
linktitle: C# में टाइमज़ोन के साथ ईमेल को MHT प्रारूप में बदलें
second_title: Aspose.Email .NET ईमेल प्रोसेसिंग API
description: यह विस्तृत मार्गदर्शिका, Aspose.Email for .NET लाइब्रेरी का उपयोग करके समयक्षेत्र जानकारी को सटीक रूप से प्रबंधित करते हुए ईमेल संदेशों को MHT प्रारूप में परिवर्तित करने के बारे में स्पष्ट निर्देश प्रदान करती है।
type: docs
weight: 12
url: /hi/net/tutorials/email/comprehensive-guide-to-email-conversion-and-export/convert-emails-to-mht-format-with-timezone-in-csharp/
---
## परिचय

ईमेल संदेशों को विभिन्न प्रारूपों में परिवर्तित करना सॉफ़्टवेयर अनुप्रयोगों में एक सामान्य कार्य है, विशेष रूप से ऐसे परिदृश्यों में जहाँ समय और समयक्षेत्र डेटा महत्वपूर्ण होते हैं। यह मार्गदर्शिका आपको ईमेल को MHT प्रारूप में परिवर्तित करने की प्रक्रिया से गुजारेगी, जबकि यह सुनिश्चित करेगी कि समयक्षेत्र की जानकारी सटीक रूप से संरक्षित है।

## अपना विकास वातावरण स्थापित करना

आरंभ करने के लिए, सुनिश्चित करें कि आपके पास उपयुक्त विकास वातावरण है:

1. विज़ुअल स्टूडियो स्थापित करें: सुनिश्चित करें कि आपके मशीन पर विज़ुअल स्टूडियो का संगत संस्करण स्थापित है।
2. एक नया C# प्रोजेक्ट बनाएं: Visual Studio लॉन्च करें और अपने ईमेल रूपांतरण एप्लिकेशन के लिए एक नया C# प्रोजेक्ट बनाएं।

## .NET के लिए Aspose.Email स्थापित करना

Aspose.Email for .NET एक शक्तिशाली लाइब्रेरी है जो ईमेल प्रोसेसिंग कार्यों को सरल बनाती है। इसे स्थापित करने के लिए इन चरणों का पालन करें:

1. अपना प्रोजेक्ट Visual Studio में खोलें.
2. टूल्स > NuGet पैकेज मैनेजर > समाधान के लिए NuGet पैकेज प्रबंधित करें पर जाएँ।
3. Aspose.Email खोजें और पैकेज स्थापित करें।
```csharp
// आवश्यक उपयोग कथन जोड़ें
using Aspose.Email;
```
## ईमेल संदेश लोड करना और पार्स करना

इसके बाद, आपको उस ईमेल संदेश को लोड और पार्स करना होगा जिसे आप कनवर्ट करना चाहते हैं। निम्नलिखित कोड स्निपेट का उपयोग करें:

```csharp
// ईमेल संदेश लोड करें
var message = MailMessage.Load("path/to/your/email.eml");

// संदेश गुण तक पहुँचें
var subject = message.Subject;
var sender = message.From.Address;
// ... अन्य गुण आवश्यकतानुसार
```

## समयक्षेत्र जानकारी संभालना

टाइमज़ोन जानकारी का सटीक प्रबंधन करना महत्वपूर्ण है। निम्न कोड स्निपेट दर्शाता है कि ईमेल संदेश से टाइमज़ोन डेटा कैसे निकाला और प्रबंधित किया जाए:

```csharp
var timezone = message.TimezoneOffset;
var timezoneId = Timezone.GetIdFromOffset(timezone);
var timezoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timezoneId);
// अब आप टाइमज़ोन रूपांतरणों को संभालने के लिए timezoneInfo का उपयोग कर सकते हैं
```

## ईमेल को MHT प्रारूप में परिवर्तित करना

अब, आइए Aspose.Email का उपयोग करके MHT प्रारूप में मूल रूपांतरण करें:

```csharp
// MHT सेव विकल्प सेट करें
var mhtOptions = MhtSaveOptions.DefaultMhtml;

// MHT आउटपुट के लिए मेमोरी स्ट्रीम बनाएं
using var mhtStream = new MemoryStream();
message.Save(mhtStream, mhtOptions);
```

## MHT फ़ाइल को सहेजना

ईमेल संदेश को MHT प्रारूप में परिवर्तित करने के बाद, अब इसे फ़ाइल के रूप में सहेजने का समय है:

```csharp
// MHT स्ट्रीम को फ़ाइल में सहेजें
using var fileStream = new FileStream("output.mht", FileMode.Create);
mhtStream.Seek(0, SeekOrigin.Begin);
mhtStream.CopyTo(fileStream);
```

## निष्कर्ष

इस गाइड में, आपने सीखा है कि .NET के लिए Aspose.Email का उपयोग करके टाइमज़ोन जानकारी को प्रभावी ढंग से संभालते हुए ईमेल संदेशों को MHT प्रारूप में कैसे परिवर्तित किया जाए। इन चरणों का पालन करके और अतिरिक्त अनुकूलन विकल्पों की खोज करके, आप अपने अनुप्रयोगों में ईमेल रूपांतरण कार्यक्षमता को सहजता से एकीकृत कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### ईमेल रूपांतरण के दौरान मैं अनुलग्नकों को कैसे संभालूँ?

 अनुलग्नकों को प्रबंधित करने के लिए, का उपयोग करें`Attachments` की संपत्ति`MailMessage` वर्ग। अनुलग्नकों के माध्यम से पुनरावृति करें और रूपांतरण प्रक्रिया के दौरान आवश्यकतानुसार उन्हें सहेजें।

### क्या मैं .NET के लिए Aspose.Email का उपयोग करके ईमेल को अन्य प्रारूपों में परिवर्तित कर सकता हूं?

बिलकुल! .NET के लिए Aspose.Email विभिन्न प्रारूपों का समर्थन करता है, जिसमें MSG, EML, PST, और बहुत कुछ शामिल है। आप अपने इच्छित आउटपुट प्रारूप के अनुरूप प्रदान किए गए कोड उदाहरणों को अनुकूलित कर सकते हैं।

### क्या समयक्षेत्र की जानकारी MHT प्रारूप में संरक्षित है?

 हां, रूपांतरण प्रक्रिया के दौरान समय क्षेत्र की जानकारी संरक्षित रहती है। समय क्षेत्र ऑफसेट को संभालकर और उचित उपयोग करके`TimeZoneInfo`विधियों का उपयोग करके, आप MHT फ़ाइल में सटीक समयक्षेत्र प्रतिनिधित्व सुनिश्चित कर सकते हैं।

### मैं .NET के लिए Aspose.Email के बारे में आगे के दस्तावेज़ और अपडेट कहां पा सकता हूं?

 विस्तृत जानकारी और अद्यतन के लिए, दस्तावेज़ देखें:[.NET API संदर्भ के लिए Aspose.Email](https://reference.aspose.com/email/net/)

### मैं .NET के लिए Aspose.Email का नवीनतम संस्करण कैसे डाउनलोड कर सकता हूं?

 आप नवीनतम संस्करण रिलीज़ पृष्ठ से डाउनलोड कर सकते हैं:[.NET के लिए Aspose.Email डाउनलोड करें](https://releases.aspose.com/email/net/)