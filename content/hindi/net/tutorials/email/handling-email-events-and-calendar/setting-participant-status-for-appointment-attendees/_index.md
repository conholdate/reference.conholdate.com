---
title: C# के साथ अपॉइंटमेंट अटेंडीज़ के लिए प्रतिभागी स्थिति सेट करना
linktitle: C# के साथ अपॉइंटमेंट अटेंडीज़ के लिए प्रतिभागी स्थिति सेट करना
second_title: Aspose.Email .NET ईमेल प्रोसेसिंग API
description: .NET के लिए C# और Aspose.Email का उपयोग करके अपॉइंटमेंट अटेंडीज़ की स्थिति प्रबंधित करना सीखें। स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका।
type: docs
weight: 16
url: /hi/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## परिचय

.NET के लिए Aspose.Email एक मजबूत और सुविधा संपन्न लाइब्रेरी है जिसे .NET अनुप्रयोगों में ईमेल हैंडलिंग को सरल बनाने के लिए डिज़ाइन किया गया है। यह गाइड अपॉइंटमेंट बनाने और प्रबंधित करने, उपस्थित लोगों को जोड़ने और प्रतिभागियों की स्थिति निर्धारित करने का चरण-दर-चरण वॉकथ्रू प्रदान करता है, जिससे आपके .NET प्रोजेक्ट में कुशल एकीकरण सुनिश्चित होता है।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- Visual Studio या संगत C# IDE की कार्यशील स्थापना.
- .NET लाइब्रेरी के लिए Aspose.Email का नवीनतम संस्करण.
- C# और ऑब्जेक्ट-ओरिएंटेड प्रोग्रामिंग का बुनियादी ज्ञान।

 लाइब्रेरी स्थापना के लिए, देखें[डाउनलोड पृष्ठ](https://releases.aspose.com/).

## आवश्यक नामस्थान आयात करें

आरंभ करने के लिए, अपॉइंटमेंट और ईमेल घटकों के प्रबंधन के लिए कार्यात्मकताओं तक पहुंचने के लिए आवश्यक नामस्थान शामिल करें।

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## अपॉइंटमेंट इंस्टेंस बनाएं

Aspose.Email में अपॉइंटमेंट शेड्यूल किए गए इवेंट जैसे मीटिंग या टास्क को दर्शाते हैं। यहाँ बताया गया है कि आप इसे कैसे बनाते हैं:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- स्थान: यह निर्दिष्ट करता है कि नियुक्ति कहाँ होगी.
- प्रारंभ समय और समाप्ति समय: अपॉइंटमेंट की अवधि निर्धारित करें.
- आयोजक एवं उपस्थितगण: प्रतिभागियों एवं उनकी भूमिकाओं को परिभाषित करें।

## अपॉइंटमेंट में उपस्थित लोगों को जोड़ना

Aspose.Email आपको उपस्थित लोगों को उनके ईमेल पते और भागीदारी की स्थिति के साथ प्रोग्रामेटिक रूप से प्रबंधित करने की अनुमति देता है।

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## प्रतिभागियों की स्थिति प्रबंधित करना

`ParticipantStatus` प्रॉपर्टी यह निर्धारित करने में मदद करती है कि किसी सहभागी ने अपॉइंटमेंट आमंत्रण स्वीकार किया है, अस्वीकार किया है या अस्थायी रूप से स्वीकार किया है। निम्नलिखित गणना मानों का उपयोग करें:

- स्वीकृत
- अस्वीकृत
- अंदाज़न

उदाहरण:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## मीटिंग आमंत्रण के रूप में नियुक्तियाँ भेजना

एक बार नियुक्ति तैयार हो जाने पर, आप इसे आमंत्रण ईमेल के रूप में भेज सकते हैं:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## निष्कर्ष

.NET के लिए Aspose.Email .NET अनुप्रयोगों में नियुक्ति प्रबंधन को सरल बनाता है, शेड्यूल किए गए ईवेंट को कुशलतापूर्वक बनाने, अनुकूलित करने और प्रबंधित करने के लिए उपकरण प्रदान करता है। इसके सहज API के साथ, आप संचार वर्कफ़्लो को सुव्यवस्थित कर सकते हैं और निर्बाध एकीकरण सुनिश्चित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Email क्या है?

Aspose.Email for .NET, .NET अनुप्रयोगों में ईमेल संदेशों, अपॉइंटमेंट्स और अन्य संबंधित कार्यात्मकताओं को संभालने के लिए एक व्यापक लाइब्रेरी है।

### क्या मैं अपॉइंटमेंट गुण अनुकूलित कर सकता हूँ?

हां, स्थान, प्रारंभ समय और प्रतिभागियों जैसी विशेषताओं को पूरी तरह से अनुकूलित किया जा सकता है।

### क्या पुस्तकालय आवर्ती नियुक्तियों का समर्थन करता है?

हां, .NET के लिए Aspose.Email अपने पुनरावृत्ति पैटर्न API का उपयोग करके आवर्ती अपॉइंटमेंट का समर्थन करता है।

### मुझे .NET के लिए Aspose.Email का समर्थन कहां मिल सकता है?

 आप विस्तृत दस्तावेज़ीकरण और सामुदायिक सहायता यहाँ से प्राप्त कर सकते हैं[सहायता पृष्ठ](https://forum.aspose.com/c/email/11).