---
title: تحويل DOCX إلى MHTML وإرسال البريد الإلكتروني باستخدام Aspose.Words لـ .NET
linktitle: تحويل DOCX إلى MHTML وإرسال البريد الإلكتروني باستخدام Aspose.Words لـ .NET
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: يوفر هذا الدليل الشامل برنامجًا تعليميًا خطوة بخطوة حول تحويل مستندات DOCX إلى تنسيق MHTML وإرسالها عبر البريد الإلكتروني باستخدام مكتبات Aspose.Words وAspose.Email في .NET.
type: docs
weight: 10
url: /ar/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## مقدمة

في عالم اليوم الرقمي، يعد تحويل المستندات بين التنسيقات المختلفة وإرسالها عبر البريد الإلكتروني مهمة شائعة. سيرشدك هذا الدليل خلال تحويل ملف DOCX إلى تنسيق MHTML وإرساله عبر البريد الإلكتروني باستخدام مكتبات Aspose.Words وAspose.Email القوية لـ .NET. سنوضح كل خطوة بوضوح، لضمان قدرتك على المتابعة بسهولة. لنبدأ!

## المتطلبات الأساسية

قبل الخوض في العملية، تأكد من إعداد ما يلي:

1.  Aspose.Words for .NET: قم بتنزيل المكتبة وتثبيتها من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email لـ .NET: قم بتنزيل هذه المكتبة وتثبيتها من[صفحة إصدارات Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
4. خادم SMTP: ستحتاج إلى الوصول إلى خادم SMTP لإرسال رسائل البريد الإلكتروني.

## استيراد المساحات الأساسية الضرورية

للاستفادة من Aspose.Words وAspose.Email في مشروعك، يجب عليك استيراد مساحات الأسماء المطلوبة. أضف التعليمات التالية باستخدام أعلى ملف C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## الخطوة 1: تحميل مستند DOCX

 ابدأ بتحميل مستند DOCX الذي ترغب في تحويله. استخدم`Document` استخدم فئة من Aspose.Words لإنجاز هذا.

```csharp
// حدد المسار إلى دليل المستند الخاص بك.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## الخطوة 2: حفظ المستند بصيغة MHTML

 بعد ذلك، قم بتحويل المستند المحمّل إلى تنسيق MHTML. يتم ذلك باستخدام`Save` طريقة`Document`فصل.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // إعادة تعيين موضع البث إلى البداية للقراءة.
    stream.Position = 0;
}
```

## الخطوة 3: إنشاء رسالة بريد إلكتروني

الآن، قم بإنشاء رسالة بريد إلكتروني من دفق MHTML باستخدام Aspose.Email. ستستخدم`MailMessage` صف لهذا الغرض.

```csharp
// قم بتحميل دفق MHTML إلى رسالة بريد إلكتروني MIME لـ Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## الخطوة 4: إرسال البريد الإلكتروني

 أخيرًا، أرسل البريد الإلكتروني باستخدام عميل SMTP. قم بتكوين عميل SMTP باستخدام تفاصيل الخادم لديك واستخدم`Send` طريقة لإرسال الرسالة.

```csharp
// قم بتكوين الرسالة وإرسالها باستخدام Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## خاتمة

تهانينا! لقد نجحت في تحويل مستند DOCX إلى MHTML وإرساله عبر البريد الإلكتروني باستخدام Aspose.Words وAspose.Email لـ .NET. تتضمن هذه العملية تحميل المستند وتحويله إلى MHTML وإنشاء رسالة بريد إلكتروني وإرسالها عبر عميل SMTP. من خلال هذه الخطوات، يمكنك أتمتة تحويل المستندات وإرسالها عبر البريد الإلكتروني بسلاسة في تطبيقاتك.

## الأسئلة الشائعة

### هل يمكنني استخدام هذه الطريقة لتحويل تنسيقات المستندات الأخرى؟
بالتأكيد! يدعم Aspose.Words مجموعة واسعة من التنسيقات، مما يسمح لك بتحويل DOC وDOCX وRTF والمزيد إلى MHTML.

### كيف يمكنني إضافة المرفقات إلى البريد الإلكتروني؟
 يمكنك بسهولة إضافة المرفقات باستخدام`Attachments` ممتلكات`MailMessage`فصل.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، Aspose.Words متوافق مع .NET Core، مما يجعله مناسبًا للاستخدام في تطبيقات .NET Core.

### هل أحتاج إلى ترخيص لـ Aspose.Words و Aspose.Email؟
 نعم، تتطلب كلتا المكتبتين ترخيصًا. يمكنك الحصول على ترخيص مؤقت لأغراض التقييم من[صفحة شراء Aspose](https://purchase.conholdate.com/temporary-license/).

### أين يمكنني العثور على مزيد من الوثائق؟
 للحصول على توثيق مفصل، راجع Aspose.Words[هنا](https://reference.aspose.com/words/net/) و Aspose.Email[هنا](https://reference.aspose.com/email/net/).