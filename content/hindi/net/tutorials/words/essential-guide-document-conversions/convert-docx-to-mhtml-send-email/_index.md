---
title: .NET के लिए Aspose.Words का उपयोग करके DOCX को MHTML में बदलें और ईमेल भेजें
linktitle: .NET के लिए Aspose.Words का उपयोग करके DOCX को MHTML में बदलें और ईमेल भेजें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: यह व्यापक मार्गदर्शिका DOCX दस्तावेजों को MHTML प्रारूप में परिवर्तित करने और .NET में Aspose.Words और Aspose.Email लाइब्रेरी का उपयोग करके उन्हें ईमेल करने पर चरण-दर-चरण ट्यूटोरियल प्रदान करती है।
type: docs
weight: 10
url: /hi/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## परिचय

आज के डिजिटल परिदृश्य में, दस्तावेज़ों को फ़ॉर्मेट के बीच बदलना और उन्हें ईमेल करना एक आम काम है। यह गाइड आपको DOCX फ़ाइल को MHTML फ़ॉर्मेट में बदलने और .NET के लिए शक्तिशाली Aspose.Words और Aspose.Email लाइब्रेरी का उपयोग करके ईमेल के ज़रिए भेजने के बारे में बताएगी। हम प्रत्येक चरण को स्पष्ट रूप से समझाएँगे, ताकि आप आसानी से उसका पालन कर सकें। चलिए शुरू करते हैं!

## आवश्यक शर्तें

प्रक्रिया में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित व्यवस्था है:

1.  Aspose.Words for .NET: लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें[Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
2.  .NET के लिए Aspose.Email: इस लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें[Aspose रिलीज़ पेज](https://releases.aspose.com/email/net/).
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके मशीन पर .NET फ्रेमवर्क स्थापित है।
4. एसएमटीपी सर्वर: ईमेल भेजने के लिए आपको एसएमटीपी सर्वर तक पहुंच की आवश्यकता होगी।

## आवश्यक नामस्थान आयात करना

अपने प्रोजेक्ट में Aspose.Words और Aspose.Email का उपयोग करने के लिए, आपको आवश्यक नामस्थान आयात करने होंगे। अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using निर्देश जोड़ें:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## चरण 1: DOCX दस्तावेज़ लोड करें

 उस DOCX दस्तावेज़ को लोड करके शुरू करें जिसे आप कनवर्ट करना चाहते हैं।`Document` इसे पूरा करने के लिए Aspose.Words से क्लास का उपयोग करें।

```csharp
// अपने दस्तावेज़ निर्देशिका का पथ निर्दिष्ट करें.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## चरण 2: दस्तावेज़ को MHTML के रूप में सहेजें

 इसके बाद, लोड किए गए दस्तावेज़ को MHTML फ़ॉर्मेट में बदलें। यह काम करने के लिए`Save` की विधि`Document` कक्षा।

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // पढ़ने के लिए स्ट्रीम की स्थिति को आरंभ में रीसेट करें।
    stream.Position = 0;
}
```

## चरण 3: एक ईमेल संदेश बनाएँ

अब, Aspose.Email का उपयोग करके MHTML स्ट्रीम से एक ईमेल संदेश बनाएँ। आप इसका उपयोग करेंगे`MailMessage` इस उद्देश्य के लिए कक्षा.

```csharp
// MHTML स्ट्रीम को Aspose.Email MIME ईमेल संदेश में लोड करें।
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## चरण 4: ईमेल भेजें

 अंत में, SMTP क्लाइंट का उपयोग करके ईमेल भेजें। अपने सर्वर विवरण के साथ SMTP क्लाइंट को कॉन्फ़िगर करें और इसका उपयोग करें`Send` संदेश भेजने की विधि.

```csharp
// Aspose.Email का उपयोग करके संदेश कॉन्फ़िगर करें और भेजें।
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## निष्कर्ष

बधाई हो! आपने सफलतापूर्वक एक DOCX दस्तावेज़ को MHTML में परिवर्तित कर लिया है और इसे Aspose.Words और Aspose.Email for .NET का उपयोग करके ईमेल के माध्यम से भेज दिया है। इस प्रक्रिया में दस्तावेज़ को लोड करना, इसे MHTML में परिवर्तित करना, एक ईमेल संदेश बनाना और इसे SMTP क्लाइंट के माध्यम से भेजना शामिल है। इन चरणों के साथ, आप अपने अनुप्रयोगों में दस्तावेज़ों के रूपांतरण और ईमेल को सहजता से स्वचालित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं अन्य दस्तावेज़ प्रारूपों को परिवर्तित करने के लिए इस विधि का उपयोग कर सकता हूँ?
बिल्कुल! Aspose.Words कई प्रकार के प्रारूपों का समर्थन करता है, जिससे आप DOC, DOCX, RTF, और अधिक को MHTML में परिवर्तित कर सकते हैं।

### मैं ईमेल में अनुलग्नक कैसे जोड़ सकता हूँ?
 आप आसानी से अनुलग्नक जोड़ सकते हैं`Attachments` की संपत्ति`MailMessage` कक्षा।

### क्या Aspose.Words .NET कोर के साथ संगत है?
हां, Aspose.Words .NET Core के साथ संगत है, जो इसे .NET Core अनुप्रयोगों में उपयोग के लिए उपयुक्त बनाता है।

### क्या मुझे Aspose.Words और Aspose.Email के लिए लाइसेंस की आवश्यकता है?
 हां, दोनों पुस्तकालयों को लाइसेंस की आवश्यकता होती है। आप मूल्यांकन उद्देश्यों के लिए अस्थायी लाइसेंस प्राप्त कर सकते हैं[Aspose खरीद पृष्ठ](https://purchase.conholdate.com/temporary-license/).

### मैं अधिक दस्तावेज कहां पा सकता हूं?
 विस्तृत दस्तावेज़ीकरण के लिए, Aspose.Words देखें[यहाँ](https://reference.aspose.com/words/net/) और Aspose.Email[यहाँ](https://reference.aspose.com/email/net/).