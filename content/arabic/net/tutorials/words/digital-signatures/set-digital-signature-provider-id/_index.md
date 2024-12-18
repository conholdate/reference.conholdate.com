---
title: تعيين معرف مزود التوقيع الرقمي في مستند Word
linktitle: تعيين معرف مزود التوقيع الرقمي في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة توقيع رقمي بشكل آمن إلى مستندات Word الخاصة بك باستخدام معرف موفر التوقيع المحدد باستخدام Aspose.Words لـ .NET.
type: docs
weight: 10
url: /ar/net/tutorials/words/digital-signatures/set-digital-signature-provider-id/
---
## مقدمة

مرحبًا! إذا كنت تبحث عن إضافة توقيع رقمي إلى مستند Word الخاص بك باستخدام معرف موفر توقيع معين، فأنت في المكان المناسب. سواء كان الأمر يتعلق بالاتفاقيات القانونية أو العقود أو أي مستندات مهمة، فإن التوقيع الرقمي الآمن ضروري. في هذا البرنامج التعليمي، سأرشدك خطوة بخطوة خلال عملية تعيين معرف موفر التوقيع في مستند Word باستخدام Aspose.Words for .NET. لنبدأ!

## المتطلبات الأساسية

قبل الغوص، تأكد من أن لديك ما يلي:

1.  Aspose.Words لمكتبة .NET:[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة متوافقة مع C#.
3.  مستند Word: مستند يحتوي على سطر توقيع (على سبيل المثال،`Signature line.docx`).
4.  الشهادة الرقمية: أ`.pfx` ملف الشهادة (على سبيل المثال،`morzal.pfx`).
5. المعرفة الأساسية بلغة C#: ستكون المعرفة بالمفاهيم الأساسية للغة C# مفيدة.

الآن دعونا ننتقل إلى العمل!

## الخطوة 1: استيراد المساحات الأساسية الضرورية

للبدء، قم بتضمين مساحات الأسماء الضرورية في مشروعك. يتيح لك هذا الوصول إلى مكتبة Aspose.Words والفئات ذات الصلة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

## الخطوة 2: قم بتحميل مستند Word الخاص بك

أولاً، ستحتاج إلى تحميل مستند Word الذي يحتوي على سطر التوقيع. وإليك كيفية القيام بذلك:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 تأكد من الاستبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين مستندك فيه.

## الخطوة 3: الوصول إلى خط التوقيع

بعد ذلك، انتقل إلى سطر التوقيع المضمّن في مستندك. يتم تمثيل سطر التوقيع ككائن شكل:

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 يقوم هذا الكود باسترجاع الشكل الأول في نص القسم الأول ويلقيه إلى`SignatureLine` هدف.

## الخطوة 4: إعداد خيارات التوقيع

الآن، دعنا نقوم بإنشاء خيارات التوقيع، والتي تتضمن معرف المزود ومعرف سطر التوقيع:

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

تضمن هذه الخيارات تطبيق معرف موفر التوقيع الصحيح عند التوقيع.

## الخطوة 5: تحميل الشهادة الرقمية

 لتوقيع المستند رقميًا، تحتاج إلى تحميله`.pfx` ملف الشهادة:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "your_certificate_password");
```

 يستبدل`"your_certificate_password"` مع كلمة المرور الفعلية لشهادتك إذا أمكن.

## الخطوة 6: توقيع الوثيقة

أخيرًا، أنت جاهز لتوقيع المستند. استخدم الكود التالي لإجراء عملية التوقيع:

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 سيؤدي هذا إلى توقيع مستندك وحفظه باسم`Digitally signed.docx`.

## خاتمة

تهانينا! لقد نجحت في تعيين معرف موفر التوقيع في مستند Word باستخدام Aspose.Words for .NET. لا تعمل هذه العملية على تأمين مستنداتك فحسب، بل تضمن أيضًا امتثالها لمعايير التوقيع الرقمي. لا تتردد في تجربتها مع مستنداتك الخاصة!

 إذا كانت لديك أي أسئلة أو كنت بحاجة إلى مزيد من المساعدة، فراجع الأسئلة الشائعة أدناه أو قم بزيارة[منتدى دعم Aspose](https://forum.aspose.com/c/words/8).

## الأسئلة الشائعة

### ما هو معرف مزود التوقيع؟

يحدد معرف مزود التوقيع بشكل فريد مزود التوقيع الرقمي، مما يضمن الأصالة والأمان.

### هل يمكنني استخدام أي ملف .pfx للتوقيع؟

نعم، يمكنك استخدام أي شهادة رقمية صالحة. فقط تأكد من أنك تستخدم كلمة المرور الصحيحة إذا كانت محمية.

### كيف يمكنني الحصول على ملف .pfx؟

يمكنك الحصول على ملف .pfx من هيئة إصدار الشهادات (CA) أو إنشاء ملف باستخدام أدوات مثل OpenSSL.

### هل من الممكن التوقيع على عدة مستندات في وقت واحد؟

بالتأكيد! يمكنك التنقل بين عدة مستندات وتطبيق عملية التوقيع على كل منها.

### ماذا لو لم تحتوي مستندي على سطر توقيع؟

سوف تحتاج إلى إدراج سطر توقيع أولاً. يوفر Aspose.Words طرقًا لإضافة أسطر توقيع برمجيًا.