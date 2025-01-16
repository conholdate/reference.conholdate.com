---
title: احصل على استخراج بيانات الرسم البياني في PowerPoint باستخدام Aspose.Slides
linktitle: احصل على استخراج بيانات الرسم البياني في PowerPoint باستخدام Aspose.Slides
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: اكتشف قوة Aspose.Slides لـ .NET من خلال تعلم كيفية استخراج نطاق البيانات من المخططات في عروض PowerPoint التقديمية برمجيًا. يوفر هذا الدليل خطوة بخطوة تعليمات واضحة.
type: docs
weight: 11
url: /ar/net/tutorials/slides/master-additional-chart-features/get-chart-data-extraction/
---
## مقدمة

هل تبحث عن استخراج نطاق البيانات من مخطط في عرض تقديمي على PowerPoint باستخدام Aspose.Slides لـ .NET؟ أنت في المكان الصحيح! سيوضح لك هذا الدليل خطوة بخطوة كيفية الحصول على نطاق بيانات المخطط برمجيًا، والاستفادة من الميزات القوية لـ Aspose.Slides.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Slides لـ .NET: قم بتنزيله وتثبيته من[هنا](https://releases.aspose.com/slides/net/).
2. بيئة التطوير: قم بإعداد IDE مثل Visual Studio.

## الخطوة 1: استيراد المساحات الأساسية الضرورية

ابدأ باستيراد المساحات المطلوبة للوصول إلى فئات وطرق Aspose.Slides:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using System;
```

## الخطوة 2: إنشاء كائن عرض تقديمي

بعد ذلك، قم بإنشاء كائن عرض تقديمي يمثل ملف PowerPoint الخاص بك:

```csharp
using (Presentation pres = new Presentation())
{
    // سيتم وضع الكود لإضافة الرسم البياني هنا
}
```

## الخطوة 3: إضافة مخطط إلى شريحة

الآن، دعنا نضيف مخططًا إلى الشريحة الأولى من العرض التقديمي الخاص بك. يمكنك اختيار نوع المخطط وتحديد موضعه وحجمه:

```csharp
IChart chart = pres.Slides[0].Shapes.AddChart(ChartType.ClusteredColumn, 10, 10, 400, 300);
```

## الخطوة 4: استرداد نطاق بيانات الرسم البياني

للحصول على نطاق البيانات الذي يعتمد عليه الرسم البياني، استخدم الكود التالي:

```csharp
string result = chart.ChartData.GetRange();
```

## الخطوة 5: عرض النتيجة

وأخيرًا، قم بطباعة نطاق بيانات الرسم البياني على وحدة التحكم:

```csharp
Console.WriteLine("Chart Data Range: {0}", result);
```

## خاتمة

في هذا البرنامج التعليمي، تعلمت كيفية استخراج نطاق بيانات الرسم البياني من عرض تقديمي على PowerPoint باستخدام Aspose.Slides لـ .NET. باستخدام بضعة أسطر فقط من التعليمات البرمجية، يمكنك الوصول بكفاءة إلى البيانات الموجودة خلف الرسوم البيانية الخاصة بك.

## الأسئلة الشائعة

### هل Aspose.Slides for .NET متوافق مع الإصدارات الأحدث من Microsoft PowerPoint؟
نعم، يدعم Aspose.Slides for .NET تنسيقات ملفات PowerPoint المختلفة، بما في ذلك أحدث التنسيقات. راجع الوثائق للحصول على التفاصيل.

### هل يمكنني معالجة عناصر أخرى في عرض تقديمي في PowerPoint باستخدام Aspose.Slides لـ .NET؟
بالتأكيد! يمكنك العمل مع الشرائح والأشكال والنصوص والصور والمزيد داخل عروضك التقديمية.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Slides لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.aspose.com/).

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Slides لـ .NET؟
 طلب ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

### ما خيارات الدعم المتوفرة لمستخدمي Aspose.Slides لـ .NET؟
 يمكنك العثور على الدعم والمساعدة من مجتمع Aspose على[منتدى الدعم](https://forum.aspose.com/).