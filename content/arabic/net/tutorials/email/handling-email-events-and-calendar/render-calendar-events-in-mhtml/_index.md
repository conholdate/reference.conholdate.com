---
title: عرض أحداث التقويم في MHTML باستخدام Aspose.Email
linktitle: عرض أحداث التقويم في MHTML باستخدام Aspose.Email
second_title: واجهة برمجة تطبيقات معالجة البريد الإلكتروني Aspose.Email .NET
description: قم بتقديم أحداث التقويم بتنسيق MHTML باستخدام Aspose.Email لـ .NET. تعرّف خطوة بخطوة على كيفية تخصيص ملفات MSG وحفظها باستخدام C#.
type: docs
weight: 15
url: /ar/net/tutorials/email/handling-email-events-and-calendar/render-calendar-events-in-mhtml/
---
## مقدمة

Aspose.Email for .NET هي مكتبة قوية للتعامل مع المهام المتعلقة بالبريد الإلكتروني في تطبيقات .NET. إحدى حالات الاستخدام الرائعة هي عرض أحداث التقويم برمجيًا باستخدام C#. سواء كنت تقوم ببناء ميزة تكامل التقويم أو إنشاء عارضات بريد إلكتروني مخصصة، فسيرشدك هذا البرنامج التعليمي خلال عرض أحداث التقويم بتنسيق MHTML بدقة وتخصيص.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن كل شيء جاهز لمتابعة هذا البرنامج التعليمي:

1.  Aspose.Email لمكتبة .NET: قم بتنزيل أحدث إصدار من المكتبة من[صفحة تنزيل Aspose.Email لـ .NET](https://releases.aspose.com/email/net/).
2. بيئة التطوير: Visual Studio (أو C# IDE المفضل لديك) مثبتًا على نظامك.
3. الترخيص: احصل على ترخيص صالح لـ Aspose.Email. لأغراض التقييم، يمكنك استخدام[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).
4.  ملف MSG للعينة: ملف MSG لحدث التقويم. يمكنك استخدام أي`.msg` ملف يحتوي على أحداث التقويم، مثل "اجتماع مع الأحداث المتكررة.msg".

## استيراد الحزم

للبدء، قم بتضمين المساحات الأساسية اللازمة في مشروعك. 

```csharp
using System;
using Aspose.Email;
using Aspose.Email.Mht;
```

الآن، دعونا ننتقل إلى الدليل خطوة بخطوة!

## الخطوة 1: تحميل ملف MSG لحدث التقويم

أولاً، نقوم بتحميل ملف MSG الذي يحتوي على حدث التقويم. هذه الخطوة ضرورية لأنها تعمل كمدخل لعرض الحدث بتنسيق MHTML.


```csharp
string dataDir = "Your Data Directory";
string fileName = "Meeting with Recurring Occurrences.msg";

// تحميل ملف MSG
MailMessage msg = MailMessage.Load(dataDir + fileName);
```

- `dataDir`:يحدد الدليل الذي يتم تخزين ملف MSG الخاص بك فيه.
- `fileName`:اسم ملف حدث التقويم.
- `MailMessage.Load` :يقرأ الملف ويحمله إلى`MailMessage` هدف.

## الخطوة 2: تكوين خيارات حفظ MHTML

بعد ذلك، نقوم بتكوين الخيارات لعرض حدث التقويم بتنسيق MHTML. ويتضمن ذلك تمكين تنسيقات ورؤوس وخصائص أخرى محددة للتخصيص.

```csharp
MhtSaveOptions options = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent
};
```

- `MhtSaveOptions`:يمثل الإعدادات لحفظ ملفات MHTML.
- `MhtFormatOptions`:تكوين خيارات مثل تضمين الرؤوس وعرض أحداث التقويم.

## الخطوة 3: تخصيص قوالب العرض

هنا، نقوم بتحديد كيفية ظهور خصائص معينة، مثل وقت بدء الحدث، في الإخراج. تتيح هذه الخطوة إخراجًا قابلًا للتخصيص وقابلًا للقراءة بدرجة كبيرة.


```csharp
if (options.FormatTemplates.ContainsKey(MhtTemplateName.Start))
    options.FormatTemplates[MhtTemplateName.Start] = @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>";
else
    options.FormatTemplates.Add(MhtTemplateName.Start, @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>");
```

- `MhtTemplateName.Start`:يشير إلى خاصية "البدء" لحدث التقويم.
- `options.FormatTemplates`:تخصيص قالب العرض لخصائص محددة.

## الخطوة 4: حفظ حدث التقويم بصيغة MHTML

وأخيرًا، قم بحفظ حدث التقويم في ملف MHTML باستخدام الخيارات التي تم تكوينها.


```csharp
msg.Save(dataDir + "Meeting with Recurring Occurrences.mhtml", options);
```

- `msg.Save`:يحفظ الرسالة بالتنسيق والموقع المحددين.
- `Meeting with Recurring Occurrences.mhtml`: اسم ملف الإخراج.

## خاتمة

إن عرض أحداث التقويم باستخدام Aspose.Email لـ .NET يعد فعالاً وقابلاً للتخصيص بدرجة كبيرة. باتباع الخطوات المذكورة أعلاه، يمكنك تحويل أحداث التقويم بسلاسة إلى ملف MHTML، مع تنسيق مخصص.

## الأسئلة الشائعة

### ما هو MHTML؟
MHTML هو تنسيق ملف أرشيف ويب يحتوي على HTML والموارد ذات الصلة مثل الصور، مما يجعله مناسبًا لعرض ومشاركة أحداث التقويم.

### هل يمكنني تقديم الأحداث المتكررة؟
نعم! يدعم Aspose.Email عرض الأحداث المتكررة، مما يضمن التقاط كافة التفاصيل بدقة.

### هل هناك حاجة إلى ترخيص؟
 نعم، يلزم الحصول على ترخيص ساري المفعول. يمكنك طلب[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### هل يمكنني إضافة خصائص مخصصة إلى المخرجات؟
 بالتأكيد! يمكنك تخصيص قوالب للخصائص الإضافية باستخدام`FormatTemplates` مجموعة.

### كيف يمكنني استكشاف المشكلات وإصلاحها؟
 قم بزيارة[منتدى دعم البريد الإلكتروني Aspose.](https://forum.aspose.com/c/email/12/) للحصول على مساعدة الخبراء.