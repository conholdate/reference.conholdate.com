---
title: C# का उपयोग करके MHT फ़ॉन्ट अनुकूलन बदलना
linktitle: C# का उपयोग करके MHT फ़ॉन्ट अनुकूलन बदलना
second_title: Aspose.Email .NET ईमेल प्रोसेसिंग API
description: .NET के लिए Aspose.Email का उपयोग करके MHT रूपांतरण के दौरान फ़ॉन्ट बदलने का तरीका जानें। आसान अनुकूलन के लिए इस चरण-दर-चरण मार्गदर्शिका का पालन करें।
type: docs
weight: 11
url: /hi/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## परिचय

वेब संचार की दुनिया में, MHT (MHTML) फ़ाइलें वेब सामग्री को संग्रहीत करने और साझा करने का एक आसान तरीका है, जिसमें छवियाँ, लिंक और शैलियाँ शामिल हैं। लेकिन क्या होता है जब आपको फ़ॉन्ट बदलकर उन MHT फ़ाइलों को बेहतर बनाने की आवश्यकता होती है? Aspose.Email for .NET की बदौलत, यह कार्य आसान हो जाता है। इस ट्यूटोरियल में, हम आपको MHT रूपांतरण के दौरान फ़ॉन्ट बदलने की प्रक्रिया के बारे में चरण-दर-चरण बताएँगे। चाहे आप कोई ऐसा एप्लिकेशन विकसित कर रहे हों जो ईमेल फ़ॉर्मेटिंग को संभालता हो या बस अपने व्यवसाय के लिए दस्तावेज़ों को कस्टमाइज़ करना चाहते हों, यह गाइड आपको वह ज्ञान प्रदान करेगा जिसकी आपको आवश्यकता है।

## आवश्यक शर्तें

कोड में उतरने से पहले, कुछ आवश्यक चीजें हैं जिन्हें आपको तैयार कर लेना चाहिए:

1. विजुअल स्टूडियो: आपको अपने C# प्रोजेक्ट पर काम करने के लिए एक एकीकृत विकास वातावरण (IDE) की आवश्यकता होगी।
2.  .NET लाइब्रेरी के लिए Aspose.Email: सुनिश्चित करें कि आपके पास लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं[जोड़ना](https://releases.aspose.com/email/net/).
3. .NET फ्रेमवर्क: आपका प्रोजेक्ट .NET फ्रेमवर्क के साथ संगत होना चाहिए; आमतौर पर, .NET Core या बाद के संस्करण अच्छी तरह से काम करते हैं।

क्या आपने ये सब तैयार कर लिया है? बहुत बढ़िया! चलिए शुरू करते हैं।

## पैकेज आयात करना

सबसे पहले, सुनिश्चित करें कि आपका प्रोजेक्ट आवश्यक नेमस्पेस का उपयोग करने के लिए सेट है। आप अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित को शामिल करना चाहेंगे:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

ये पैकेज आपको MHT फ़ाइलों के साथ काम करने और उनकी सामग्री को संशोधित करने के लिए आवश्यक कार्यक्षमता तक पहुंच प्रदान करेंगे।

अब, आइए MHT रूपांतरण के दौरान फ़ॉन्ट बदलने में शामिल चरणों का विश्लेषण करें।

## चरण 1: MHT फ़ाइल लोड करें

 पहली चीज़ जो आपको करने की ज़रूरत होगी वह है अपनी MHT फ़ाइल को एक में लोड करना`MailMessage` यह वह जगह है जहाँ आप इसकी सामग्री तक पहुँच सकते हैं और उसमें हेरफेर कर सकते हैं।

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 स्पष्टीकरण: यहाँ,`"input.mht"` यह आपकी MHT फ़ाइल का पथ है।`MhtmlLoadOptions()`आपको फ़ाइल को लोड करने के तरीके को कॉन्फ़िगर करने की अनुमति देता है, उदाहरण के लिए, अनुलग्नकों या लिंक किए गए संसाधनों को अलग तरीके से प्रबंधित करना।

## चरण 2: वैकल्पिक दृश्यों के माध्यम से पुनरावृति करें

MHT फ़ाइलों में अक्सर कई वैकल्पिक दृश्य होते हैं, खासकर अगर उनमें HTML सामग्री शामिल हो। आपको जिस दृश्य को संशोधित करना है उसे खोजने के लिए इन दृश्यों के माध्यम से लूप करना होगा।

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 स्पष्टीकरण: आप प्रत्येक की जाँच कर रहे हैं`AlternateView` यह देखने के लिए कि क्या यह HTML प्रकार का है। यदि यह है, तो आप एक्सेस कर सकते हैं`LinkedResources`, जहां HTML में लिंक किए गए किसी भी फ़ॉन्ट को आमतौर पर संग्रहीत किया जाता है।

## चरण 3: फ़ॉन्ट पहचानें और अनुकूलित करें

अब जब आपके पास लिंक किए गए संसाधनों तक पहुंच है, तो आप पहचान सकते हैं कि कौन से संसाधन फ़ॉन्ट हैं और उन्हें आवश्यकतानुसार अनुकूलित कर सकते हैं।

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // इच्छित फ़ॉन्ट में बदलें
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // सुनिश्चित करें कि यह ठीक से एनकोड किया गया है
    }
}
```

 स्पष्टीकरण: यह लूप जाँचता है कि लिंक किए गए संसाधन का कंटेंट टाइप ट्रू टाइप फ़ॉन्ट है या नहीं। अगर यह मेल खाता है, तो आप फ़ॉन्ट का नाम अपनी इच्छानुसार बदल सकते हैं (जैसे इस उदाहरण में "Arial")।`TransferEncoding`यह भी सुनिश्चित करने के लिए सेट किया जाना चाहिए कि दस्तावेज़ को सहेजते समय फ़ॉन्ट डेटा सही ढंग से एनकोड किया गया है।

## चरण 4: अपडेट की गई MHT फ़ाइल को सेव करें

फ़ॉन्ट को कस्टमाइज़ करने के बाद, अब अपनी संशोधित MHT फ़ाइल को सेव करने का समय है। आपको यह सुनिश्चित करना होगा कि आप अपनी फ़ाइल की अखंडता बनाए रखने के लिए सही सेविंग विकल्पों का उपयोग करें।

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 स्पष्टीकरण: कोड की इस पंक्ति में,`"output.mht"` यह उस फ़ाइल का नाम है जहाँ आप अपडेट की गई सामग्री को सहेजना चाहते हैं।`SaveOptions.DefaultMhtml` यह सुनिश्चित करता है कि नई फ़ाइल MHT प्रारूप को बनाए रखे।

## निष्कर्ष

MHT फ़ाइलों में फ़ॉन्ट बदलने से आपके दस्तावेज़ों का लुक और फील काफ़ी हद तक बेहतर हो सकता है। .NET के लिए Aspose.Email का लाभ उठाकर, आप आसानी से MHT फ़ाइलें लोड कर सकते हैं, उनकी सामग्री को संशोधित कर सकते हैं, और कोड की कुछ पंक्तियों का उपयोग करके परिवर्तनों को सहेज सकते हैं। चाहे आप किसी व्यक्तिगत प्रोजेक्ट या किसी बड़े एप्लिकेशन पर काम कर रहे हों, इन कौशलों में महारत हासिल करने से आप जानकारी प्रस्तुत करने के तरीके में सुधार कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### एमएचटी प्रारूप क्या है?
एमएचटी एक वेब पेज संग्रह प्रारूप है जो HTML दस्तावेज़ों, छवियों और अन्य संसाधनों को एक ही फ़ाइल में संग्रहीत करता है।

### क्या मैं Aspose का उपयोग करके MHT फ़ाइलों के अन्य पहलुओं को बदल सकता हूँ?
बिल्कुल! Aspose.Email आपको MHT फ़ाइलों के लगभग हर पहलू को संशोधित करने की अनुमति देता है, जिसमें अनुलग्नक, हेडर और बहुत कुछ शामिल है।

### क्या .NET के लिए Aspose.Email निःशुल्क है?
 Aspose एक निःशुल्क परीक्षण प्रदान करता है, लेकिन पूर्ण संस्करण के लिए लाइसेंस की आवश्यकता होती है। आप यहाँ से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### मैं Aspose.Email पर अधिक दस्तावेज़ कहां पा सकता हूं?
 आप यहां पर विस्तृत दस्तावेज और उदाहरण पा सकते हैं[Aspose ईमेल दस्तावेज़ पृष्ठ](https://reference.aspose.com/email/net/).

### यदि मुझे Aspose का उपयोग करते समय कोई समस्या आती है तो क्या होगा?
 यदि आपको कोई समस्या आती है, तो आप सहायता के लिए संपर्क कर सकते हैं[Aspose समर्थन मंच](https://forum.aspose.com/c/email/12/).