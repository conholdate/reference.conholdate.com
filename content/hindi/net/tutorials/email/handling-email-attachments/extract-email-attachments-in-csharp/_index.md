---
title: C# में ईमेल अनुलग्नक निकालें - Aspose.Email ट्यूटोरियल
linktitle: C# में ईमेल अनुलग्नक निकालें - Aspose.Email ट्यूटोरियल
second_title: Aspose.Email .NET ईमेल प्रोसेसिंग API
description: .NET के लिए Aspose.Email का उपयोग करके C# में ईमेल अनुलग्नक निकालने का तरीका जानें। PDF, छवियों और अन्य के लिए उदाहरणों के साथ चरण-दर-चरण मार्गदर्शिका।
type: docs
weight: 14
url: /hi/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## परिचय

क्या आपने कभी खुद को ईमेल अटैचमेंट को एक-एक करके मैन्युअल रूप से डाउनलोड करते हुए पाया है? यह न केवल समय लेने वाला है बल्कि त्रुटियों से भी ग्रस्त है। सौभाग्य से, Aspose.Email for .NET इस कार्य को स्वचालित करने का एक शक्तिशाली और कुशल तरीका प्रदान करता है। चाहे आप PDF, इमेज या किसी अन्य फ़ाइल प्रकार के साथ काम कर रहे हों, आप C# का उपयोग करके आसानी से अटैचमेंट निकाल सकते हैं।

इस गाइड में, हम आपको एक संपूर्ण ट्यूटोरियल दिखाएंगे, जिसमें आवश्यक शर्तों से लेकर पूरी तरह से काम करने वाले उदाहरण तक सब कुछ बताया जाएगा। क्या आप घंटों तक मैन्युअल काम करने से बचने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

कोडिंग शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें हैं:

- आपके मशीन पर Visual Studio स्थापित है.
-  .NET लाइब्रेरी के लिए Aspose.Email. आप कर सकते हैं[यहाँ पर डाउनलोड करो](https://releases.aspose.com/email/net/) या इसे NuGet के माध्यम से स्थापित करें।
- एक वैध ईमेल खाता (IMAP/POP3 समर्थित).
- C# प्रोग्रामिंग की बुनियादी समझ.

 यदि आप Aspose.Email पर नए हैं, तो अनुरोध करने पर विचार करें[मुफ्त परीक्षण](https://releases.aspose.com/) या एक[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) सम्पूर्ण सुविधाओं को अनलॉक करने के लिए.

## पैकेज आयात करें

कोड में आगे बढ़ने से पहले, सुनिश्चित करें कि आपने आवश्यक नेमस्पेस आयात कर लिए हैं। अपनी C# फ़ाइल के शीर्ष पर निम्न जोड़ें:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

आइए इस प्रक्रिया को आसानी से समझ में आने वाले चरणों में तोड़ें। सुचारू निष्पादन सुनिश्चित करने के लिए प्रत्येक चरण का सावधानीपूर्वक पालन करें।


## चरण 1: अपना IMAP क्लाइंट सेट करें

पहला कदम IMAP प्रोटोकॉल का उपयोग करके अपने ईमेल सर्वर से कनेक्ट होना है। IMAP हमें सर्वर से ईमेल संदेशों तक पहुँचने और उन्हें प्राप्त करने की अनुमति देता है।

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  प्रतिस्थापित करें`imap.example.com` आपके ईमेल प्रदाता के IMAP सर्वर पते के साथ (उदाहरण के लिए,`imap.gmail.com` (जीमेल के लिए)
-  अपना वास्तविक ईमेल उपयोग करें`username` और`password`.
- `SelectFolder(ImapFolderInfo.InBox)`यह निर्दिष्ट करता है कि हम इनबॉक्स के साथ काम करना चाहते हैं।


## चरण 2: इनबॉक्स से ईमेल पुनर्प्राप्त करें

एक बार कनेक्ट होने के बाद, आपको इनबॉक्स से ईमेल संदेश लाने की आवश्यकता है। Aspose.Email सभी संदेशों को सूचीबद्ध करने के लिए एक सरल विधि प्रदान करता है।

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` इनबॉक्स में सभी ईमेल के लिए मेटाडेटा पुनर्प्राप्त करता है.
- `ImapMessageInfoCollection` ऑब्जेक्ट में प्रेषक, विषय और विशिष्ट आईडी जैसे विवरण शामिल होते हैं।


## चरण 3: प्रत्येक ईमेल संदेश प्राप्त करें

सामग्री और अनुलग्नकों तक पहुंचने के लिए, आपको प्रत्येक ईमेल को उसकी विशिष्ट आईडी का उपयोग करके प्राप्त करना होगा।


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

- `foreach` लूप सभी संदेशों के माध्यम से पुनरावृत्त होता है।
- `FetchMessage()` किसी दिए गए संदेश आईडी के लिए वास्तविक ईमेल सामग्री पुनर्प्राप्त करता है।


## चरण 4: अनुलग्नकों के माध्यम से लूप करें

 अब जब आपके पास ईमेल की सामग्री आ गई है, तो अनुलग्नकों को निकालने का समय आ गया है।`MailMessage` ऑब्जेक्ट में अनुलग्नकों का एक संग्रह शामिल है.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

- `Attachments` प्रॉपर्टी ईमेल में सभी अनुलग्नकों को सूचीबद्ध करती है.
-  उपयोग`attachment.Name` फ़ाइल नाम प्राप्त करने के लिए.


## चरण 5: अनुलग्नकों को डिस्क पर सहेजें

अंत में, अनुलग्नकों को अपनी स्थानीय मशीन पर सहेजें। आप फ़ाइलों को प्रकार, आकार या अन्य मानदंडों के आधार पर फ़िल्टर कर सकते हैं।

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  प्रतिस्थापित करें`"C:\\Attachments"`अपने इच्छित फ़ोल्डर पथ के साथ.
- `attachment.Save()` विधि फ़ाइल को डिस्क पर लिखती है.


## चरण 6: अनुलग्नकों को प्रकार के अनुसार संसाधित करें

यदि आपको अनुलग्नकों को उनके प्रकार के आधार पर अलग-अलग तरीके से संभालने की आवश्यकता है (जैसे, पीडीएफ बनाम जेपीईजी), तो Aspose.Email इसे आसान बनाता है।

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` फ़ाइल प्रकार की पहचान करता है (उदाहरण के लिए,`application/pdf` पीडीएफ के लिए,`image/jpeg` (छवियों के लिए)
- आवश्यकतानुसार विभिन्न फ़ाइल प्रकारों के लिए कस्टम तर्क जोड़ें.


## निष्कर्ष

और अब यह हो गया! ईमेल से अटैचमेंट निकालना अब कोई मुश्किल काम नहीं रह गया है। .NET के लिए Aspose.Email के साथ, आप कोड की कुछ ही लाइनों में इस प्रक्रिया को स्वचालित कर सकते हैं। IMAP क्लाइंट को सेट अप करने से लेकर अटैचमेंट को स्थानीय रूप से सहेजने तक, इस गाइड में वह सब कुछ शामिल है जो आपको शुरू करने के लिए चाहिए। 

 तो फिर इंतज़ार क्यों?[Aspose.Email डाउनलोड करें](https://releases.aspose.com/email/net/) और आज ही अपने ईमेल वर्कफ़्लो को सुव्यवस्थित करना शुरू करें!


## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं इस कोड का उपयोग जीमेल या आउटलुक के साथ कर सकता हूँ?
 हाँ! बदलें`imap.example.com` जीमेल के साथ (`imap.gmail.com`) या आउटलुक का (`outlook.office365.com`) IMAP सर्वर पता.

### क्या Aspose.Email का उपयोग निःशुल्क है?
 Aspose.Email को पूर्ण सुविधाओं के लिए लाइसेंस की आवश्यकता होती है। आप अनुरोध कर सकते हैं[मुफ्त परीक्षण](https://releases.aspose.com/) या एक[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).

### मैं पासवर्ड सुरक्षा कैसे संभाल सकता हूँ?
पासवर्ड को हार्डकोड करने के स्थान पर पर्यावरण चर या सुरक्षित क्रेडेंशियल भंडारण का उपयोग करने पर विचार करें।

### क्या मैं भेजे गए आइटम से अनुलग्नक निकाल सकता हूँ?
 हाँ, बस उपयोग करें`SelectFolder(ImapFolderInfo.Sent)` इनबॉक्स के बजाय.

### क्या Aspose.Email POP3 का समर्थन करता है?
बिल्कुल! IMAP के अलावा, यह POP3 और SMTP का भी समर्थन करता है।