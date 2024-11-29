---
title: إضافة مكون مربع الاختيار إلى مستند PDF
linktitle: إضافة مكون مربع الاختيار إلى مستند PDF
second_title: GroupDocs.Annotation .NET API
description: اكتشف كيفية إثراء مستندات PDF الخاصة بك عن طريق إضافة مكونات مربع الاختيار التفاعلية باستخدام GroupDocs.Annotation for .NET SDK. يوفر هذا البرنامج التعليمي الشامل دليلاً واضحًا خطوة بخطوة.
type: docs
weight: 11
url: /ar/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## مقدمة

في هذا البرنامج التعليمي، سنوضح لك عملية إضافة مكون مربع الاختيار إلى مستند PDF باستخدام GroupDocs.Annotation for .NET SDK. تتيح لك هذه الميزة تحسين مستندات PDF الخاصة بك باستخدام عناصر تفاعلية، مما يجعلها أكثر جاذبية للمستخدمين.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  GroupDocs.Annotation لـ .NET SDK: قم بتنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير .NET على جهازك.

## الخطوة 1: استيراد المساحات المطلوبة

أولاً، قم بتضمين المساحات الأساسية اللازمة في مشروعك:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## الخطوة 2: تحديد مسار الإخراج

حدد المكان الذي سيتم فيه حفظ مستند PDF المعدل:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 3: تهيئة المشرح

 إنشاء مثيل لـ`Annotator` الفئة التي تحتوي على المسار إلى مستند PDF المدخل الخاص بك:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## الخطوة 4: إنشاء مكون مربع الاختيار

الآن، دعنا نقوم بإنشاء مكون مربع الاختيار وتخصيصه:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // تحديد الموضع والحجم
    PenColor = 65535, // ضبط اللون (في هذه الحالة، الأصفر)
    Style = BoxStyle.Star, // اختر نمطًا لمربع الاختيار
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## الخطوة 5: أضف مربع الاختيار إلى المستند

أضف مكون مربع الاختيار الذي تم إنشاؤه إلى ملف PDF:

```csharp
annotator.Add(checkBox);
```

## الخطوة 6: حفظ المستند المعدل

احفظ مستند PDF المحدث باستخدام مربع الاختيار المضمن:

```csharp
annotator.Save("result.pdf");
```

## الخطوة 7: عرض مسار الإخراج

وأخيرًا، أبلغ المستخدم بمكان حفظ المستند المعدل:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

في هذا البرنامج التعليمي، نجحنا في إضافة مكون مربع اختيار إلى مستند PDF باستخدام GroupDocs.Annotation for .NET. تتيح لك هذه الوظيفة إنشاء ملفات PDF تفاعلية يمكنها تحسين تجربة المستخدم وتفاعله.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر مربع الاختيار؟

بالتأكيد! يمكنك تعديل خصائص مختلفة مثل اللون والأسلوب والحجم لتلبية احتياجاتك المحددة.

### هل GroupDocs.Annotation لـ .NET مناسب للاستخدام التجاري؟

نعم، يوفر GroupDocs.Annotation لـ .NET تراخيص تجارية للشركات.

### هل يمكنني تجربة GroupDocs.Annotation لـ .NET قبل الشراء؟

 نعم، تتوفر نسخة تجريبية مجانية، ويمكنك الوصول إليها[هنا](https://releases.groupdocs.com/).

### أين يمكنني العثور على الدعم لـ GroupDocs.Annotation لـ .NET؟

 الدعم والموارد الإضافية متاحة على[منتدى GroupDocs](https://forum.groupdocs.com/c/annotation/10).

### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟

 يمكنك الحصول على ترخيص مؤقت للاختبار من[هنا](https://purchase.groupdocs.com/temporary-license/).