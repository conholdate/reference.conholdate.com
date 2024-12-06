---
title: إنشاء سطر توقيع رقمي جديد وتعيين معرف المزود
linktitle: إنشاء سطر توقيع رقمي جديد وتعيين معرف المزود
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: اكتشف كيفية إضافة أسطر التوقيع برمجيًا إلى مستندات Word باستخدام Aspose.Words for .NET. يغطي هذا الدليل الشامل كل شيء بدءًا من إعداد بيئة التطوير الخاصة بك إلى إدراج أسطر التوقيع وتوقيع المستندات بشكل آمن.
type: docs
weight: 10
url: /ar/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## مقدمة

مرحبًا بكم أيها المتحمسون للتكنولوجيا! هل أردتم يومًا أتمتة تضمين أسطر التوقيع في مستندات Word الخاصة بكم؟ اليوم، سنتعرف على كيفية تحقيق ذلك باستخدام Aspose.Words for .NET. سيرشدك هذا الدليل خطوة بخطوة خلال إنشاء سطر توقيع وتعيين معرف المزود، مما يجعل مهام معالجة المستندات الخاصة بكم أكثر كفاءة وتبسيطًا.

## المتطلبات الأساسية

قبل أن نبدأ، دعنا نتأكد من إعداد كل شيء:

1.  Aspose.Words لـ .NET: إذا لم تقم بتثبيته بعد، قم بتنزيله[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: استخدم Visual Studio أو أي إعداد تطوير C#.
3. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
4. شهادة PFX: ستحتاج إلى شهادة PFX لتوقيع المستندات، والتي يمكن الحصول عليها من هيئة شهادة موثوقة.

## استيراد المساحات الأساسية الضرورية

للبدء، قم باستيراد المساحات المطلوبة إلى مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

الآن، دعنا نتعمق في تفاصيل إنشاء سطر توقيع جديد وتعيين معرف المزود.

## الخطوة 1: إنشاء مستند جديد

أولاً، نحتاج إلى إنشاء مستند Word جديد، والذي سيكون بمثابة لوحة رسم لسطر توقيعنا:

```csharp
// حدد المسار إلى دليل المستندات الخاص بك.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 هنا، نقوم بتهيئة ملف جديد`Document` و أ`DocumentBuilder`، مما يسمح لنا بإضافة العناصر بسهولة.

## الخطوة 2: تحديد خيارات سطر التوقيع

بعد ذلك، سنقوم بتحديد الخيارات لسطر التوقيع الخاص بنا، بما في ذلك اسم المُوقّع، والمسمى الوظيفي، والبريد الإلكتروني، والتفاصيل الأخرى ذات الصلة:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

تساعد هذه الخيارات على تخصيص خط التوقيع، مما يجعله واضحًا واحترافيًا.

## الخطوة 3: أدخل سطر التوقيع

بعد أن أصبحت خياراتنا جاهزة، يمكننا الآن إدراج سطر التوقيع في المستند:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 ال`InsertSignatureLine`تضيف الطريقة سطر التوقيع، ونقوم بتعيين معرف مزود فريد له.

## الخطوة 4: حفظ المستند

بعد إدراج سطر التوقيع، دعونا نحفظ المستند:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

سيؤدي هذا إلى حفظ مستندك بسطر التوقيع المضاف حديثًا.

## الخطوة 5: إعداد خيارات التوقيع

الآن، سنقوم بتكوين خيارات التوقيع، بما في ذلك معرف سطر التوقيع، ومعرف المزود، والتعليقات، ووقت التوقيع:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

تضمن هذه الإعدادات توقيع المستند بالتفاصيل الصحيحة.

## الخطوة 6: إنشاء حامل الشهادة

لتوقيع المستند، نحتاج إلى إنشاء حامل شهادة باستخدام شهادة PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 يستبدل`"morzal.pfx"` مع اسم ملف الشهادة الفعلي الخاص بك و`"aw"` مع كلمة المرور الخاصة بشهادتك.

## الخطوة 7: توقيع الوثيقة

وأخيرًا، سنقوم بتوقيع المستند باستخدام أداة التوقيع الرقمي:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

تقوم هذه العملية بتوقيع المستند وحفظه كملف جديد.

## خاتمة

تهانينا! لقد نجحت في إنشاء سطر توقيع وتعيين معرف مقدم الخدمة في مستند Word باستخدام Aspose.Words for .NET. تعمل هذه المكتبة القوية على تبسيط مهام معالجة المستندات، مما يجعل سير عملك أكثر كفاءة. جربها وشاهد كيف يمكنها تحسين مشاريعك!

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر خط التوقيع؟
 بالتأكيد! يمكنك تعديل خيارات مختلفة في`SignatureLineOptions` لتناسب أسلوبك ومتطلباتك.

### ماذا لو لم يكن لدي شهادة PFX؟
سوف تحتاج إلى الحصول على واحدة من هيئة إصدار شهادات موثوقة، حيث أنها ضرورية للتوقيع الرقمي على المستندات.

### هل يمكنني إضافة أسطر توقيع متعددة إلى مستند؟
نعم، يمكنك إضافة أسطر توقيع متعددة عن طريق تكرار عملية الإدراج باستخدام خيارات مختلفة.

### هل Aspose.Words for .NET متوافق مع .NET Core؟
نعم، يدعم Aspose.Words for .NET .NET Core، مما يجعله متعدد الاستخدامات لبيئات التطوير المختلفة.

### ما مدى أمان التوقيعات الرقمية؟
التوقيعات الرقمية التي تم إنشاؤها باستخدام Aspose.Words آمنة للغاية، بشرط استخدام شهادة صالحة وموثوقة.