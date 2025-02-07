---
title: ترتيب المعلومات المخصص في MHTML مع Aspose.Email
linktitle: ترتيب المعلومات المخصص في MHTML مع Aspose.Email
second_title: واجهة برمجة تطبيقات معالجة البريد الإلكتروني Aspose.Email .NET
description: تعرف على كيفية تعريف ترتيب المعلومات المخصص في MHTML باستخدام Aspose.Email لـ .NET في هذا البرنامج التعليمي خطوة بخطوة.
type: docs
weight: 14
url: /ar/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## مقدمة

إن إنشاء تنسيقات بريد إلكتروني غنية يمكن أن يعزز التواصل بشكل كبير، وخاصة عند تصدير رسائل البريد الإلكتروني إلى تنسيقات ملفات مختلفة مثل MHTML. يوفر Aspose.Email for .NET للمطورين مجموعة أدوات قوية للتعامل مع رسائل البريد الإلكتروني، والتي تتضمن تحديد ترتيب مخصص لكيفية عرض المعلومات عند التصدير إلى MHTML. في هذا الدليل، سنوضح الخطوات اللازمة لتحقيق ذلك، مما يجعل من السهل اتباعها سواء كنت مطورًا متمرسًا أو مبتدئًا. لذا، دعنا ننتقل مباشرة إلى الأمر!

## المتطلبات الأساسية

قبل أن تتعمق في تحديد الترتيب المخصص للمعلومات في MHTML، هناك بعض المتطلبات الأساسية التي تحتاج إلى التحقق منها من قائمتك:

1. بيئة تطوير .NET: تأكد من إعداد بيئة تطوير .NET. يمكنك استخدام Visual Studio أو Visual Studio Code أو أي بيئة تطوير متكاملة أخرى متوافقة.

2.  مكتبة Aspose.Email: يجب أن يكون لديك مكتبة Aspose.Email لـ .NET مثبتة. يمكنك تنزيل أحدث إصدار من[صفحة إصدارات Aspose](https://releases.aspose.com/email/net/).

3. الفهم الأساسي للغة C#: إن الإلمام ببرمجة C# سيساعدك على فهم الكود بشكل أفضل.

4.  ملف البريد الإلكتروني النموذجي: ستحتاج إلى عينة`.eml` ملف (على سبيل المثال،`Attachments.eml`) لأغراض الاختبار.

بمجرد حصولك على هذه المتطلبات الأساسية، ستكون جاهزًا تمامًا لمتابعة البرنامج التعليمي!

## استيراد الحزم

للبدء في استخدام الكود الخاص بك، ستحتاج إلى استيراد مساحات الأسماء الضرورية من مكتبة Aspose.Email. يعد هذا أمرًا ضروريًا للوصول إلى جميع الفئات والطرق اللازمة للتعامل مع ملفات البريد الإلكتروني.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

قم بتضمين هذه العناصر في أعلى ملف C# الخاص بك. أنت الآن جاهز للتعمق في البرمجة!

الآن بعد أن قمت بإعداد كل شيء، دعنا نقوم بتقسيم البرنامج التعليمي إلى خطوات قابلة للإدارة.

## الخطوة 1: قم بتعيين دليل البيانات الخاص بك

أول شيء عليك فعله هو إنشاء دليل لتخزين ملفات البريد الإلكتروني الخاصة بك. يمكن أن يكون هذا الدليل أي مسار على جهازك المحلي.

```csharp
string dataDir = "Your Data Directory";
```

 يستبدل`"Your Data Directory"` مع المسار الفعلي الذي تريده`.eml` يوجد الملف. على سبيل المثال، إذا كان الملف موجودًا في`C:\Emails`، ستكتب:

```csharp
string dataDir = @"C:\Emails\";
```

## الخطوة 2: تحميل رسالة البريد الإلكتروني

بعد ذلك، تحتاج إلى تحميل`.eml` ملف في`MailMessage` الكائن. يتيح لك هذا إمكانية معالجة محتوى البريد الإلكتروني والبيانات الوصفية.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

تأكد من أن اسم الملف يتطابق مع الاسم الموجود في الدليل المحدد. إذا كان اسم الملف مختلفًا، فقم بتحديث اسم الملف وفقًا لذلك.

## الخطوة 3: إعداد خيارات حفظ MHTML

بعد تحميل بريدك الإلكتروني، حان الوقت لتحديد كيفية حفظه بتنسيق MHTML. يمكنك البدء بالخيارات الافتراضية.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

يقوم هذا السطر بتهيئة خيارات حفظ MHTML، مما يمهد الطريق لتخصيص الرؤوس لاحقًا.

## الخطوة 4: حفظ MHTML بالترتيب الافتراضي

دعنا نحفظ البريد الإلكتروني بتنسيق MHTML باستخدام الترتيب الافتراضي. سيمنحك هذا أساسًا للمقارنة به بعد التخصيص.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

 قم بتشغيل هذا السطر، وتحقق من الدليل المحدد. يجب أن ترى الآن ملف MHTML جديدًا باسم`CustomOrderOfInformationInMHTML_1.mhtml`افتحه لترى كيفية عرض المعلومات بشكل افتراضي.

## الخطوة 5: تخصيص ترتيب الرأس

الآن يأتي الجزء الممتع! يمكنك تحديد العناوين التي تريد تضمينها في مخرجات MHTML وبأي ترتيب. سنبدأ ببعض العناوين الشائعة.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

من خلال إضافة هذه العناوين، فأنت تخبر Aspose بكيفية عرض البريد الإلكتروني.

## الخطوة 6: حفظ MHTML باستخدام ترتيب مخصص

بعد تخصيص الرؤوس، يتعين عليك حفظ البريد الإلكتروني مرة أخرى بتنسيق MHTML لترى كيف يؤثر الطلب الجديد على الناتج.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

 قم بتشغيل هذا الكود، ثم افتح`CustomOrderOfInformationInMHTML_2.mhtml`قارنه بالأول لترى كيف تغيرت المعلومات بناءً على ترتيب رأس الصفحة.

## الخطوة 7: مسح وإضافة ترتيب رأسي جديد

ماذا لو كنت تريد ترتيبًا مختلفًا تمامًا؟ يمكنك البدء من جديد عن طريق مسح إعدادات الرأس الحالية.

```csharp
opt.RenderingHeaders.Clear();
```

الآن حان الوقت لتحديد ترتيب جديد للعناوين. على سبيل المثال، إذا كنت تريد إعطاء الأولوية للمرفقات ونسخ المستلمين:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## الخطوة 8: حفظ MHTML باستخدام طلب مخصص جديد

وأخيرًا، احفظ البريد الإلكتروني للمرة الأخيرة باستخدام إعدادات الرأس الجديدة.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

 بعد تشغيل هذا الخط، افتح`CustomOrderOfInformationInMHTML_3.mhtml`وتحقق من كيفية عرض المعلومات بناءً على التخصيص الجديد الخاص بك.

## خاتمة

والآن لديك دليل واضح لتحديد ترتيب مخصص للمعلومات في MHTML باستخدام Aspose.Email لـ .NET. باتباع هذه الخطوات، يمكنك التحكم في كيفية تمثيل رسائل البريد الإلكتروني الخاصة بك بتنسيق MHTML، مما يضمن تقديم المعلومات الأكثر أهمية بطريقة تناسب احتياجاتك. 

## الأسئلة الشائعة

### ما هو MHTML؟
MHTML تعني "MIME HTML"، وهو تنسيق أرشيف صفحة الويب الذي يجمع HTML وموارد أخرى مثل الصور.

### هل يمكنني استخدام Aspose.Email مجانًا؟
 نعم، يوفر Aspose إصدارًا تجريبيًا مجانيًا للمطورين لاستكشافه. يمكنك العثور عليه[هنا](https://releases.aspose.com/).

### ماذا لو واجهت مشاكل أثناء استخدام Aspose.Email؟
 يمكنك الحصول على الدعم من المجتمع عبر[منتدى اسبوس](https://forum.aspose.com/c/email/12/).

### هل يتوفر ترخيص مؤقت لـ Aspose.Email؟
 نعم يمكنك التقدم بطلب للحصول على رخصة مؤقتة[هنا](https://purchase.aspose.com/temporary-license/).

### أين يمكنني شراء Aspose.Email؟
 يمكنك شراء المكتبة من هنا[وصلة](https://purchase.aspose.com/buy).