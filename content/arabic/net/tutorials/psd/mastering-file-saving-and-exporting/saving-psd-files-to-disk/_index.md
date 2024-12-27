---
title: حفظ ملفات PSD على القرص باستخدام Aspose.PSD لـ .NET
linktitle: حفظ الصور على القرص باستخدام Aspose.PSD لـ .NET
second_title: واجهة برمجة تطبيقات Aspose.PSD .NET
description: تعرف على كيفية حفظ صور PSD على القرص بسهولة باتباع دليل خطوة بخطوة. سواء كنت تقوم بتحويل ملفات PSD إلى تنسيقات صور مختلفة أو إدارة أصول صور معقدة.
type: docs
weight: 10
url: /ar/net/tutorials/psd/mastering-file-saving-and-exporting/saving-psd-files-to-disk/
---
## مقدمة

في عالم تطوير .NET سريع التطور، تعد Aspose.PSD مكتبة قوية لإدارة صور PSD بكفاءة. سيرشدك هذا الدليل خلال عملية حفظ الصور على القرص باستخدام Aspose.PSD، سواء كنت مطورًا متمرسًا أو مبتدئًا في مجال البرمجة. 

## المتطلبات الأساسية

قبل أن تبدأ، يرجى التأكد مما يلي:

### 1. تثبيت Aspose.PSD لـ .NET

 يجب أن يكون لديك Aspose.PSD for .NET مثبتًا في بيئة التطوير الخاصة بك. قم بتنزيله[هنا](https://releases.aspose.com/psd/net/).

### 2. استيراد المساحات المطلوبة

في مشروع .NET الخاص بك، قم بتضمين المساحات الأساسية اللازمة في الجزء العلوي من الكود الخاص بك:

```csharp
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## الخطوة 1: قم بتحديد دليل المستندات الخاص بك

قم بإعداد متغير لتحديد الدليل الذي توجد فيه مستنداتك:

```csharp
// المسار إلى دليل المستندات
string dataDir = "Your Document Directory";
```

 تأكد من الاستبدال`"Your Document Directory"` مع المسار الفعلي.

## الخطوة 2: تحديد مسارات المصدر والوجهة

قم بتحديد ملف PSD المصدر ومسار الوجهة للصورة الناتجة:

```csharp
// ExStart: الحفظ على القرص

string sourceFile = dataDir + @"sample.psd";
string destName = dataDir + "result.png";
```

 هنا،`sourceFile` يشير إلى ملف PSD الذي تريد معالجته، بينما`destName` هو المكان الذي تريد حفظ الصورة الناتجة فيه.

## الخطوة 3: تحميل الصورة وحفظها

استخدم الكود التالي لتحميل صورة PSD وحفظها بصيغة PNG:

```csharp
// قم بتحميل صورة PSD واستبدال الخطوط غير الموجودة
using (Image image = Image.Load(sourceFile))
{
    PsdImage psdImage = (PsdImage)image;
    psdImage.Save(destName, new PngOptions());
}
```

يقوم هذا المقطع بتحميل ملف PSD، وتحويله إلى تنسيق PNG، ثم حفظه في الوجهة المحددة. 

## خاتمة

يعمل برنامج Aspose.PSD for .NET على تبسيط مهام معالجة الصور، مما يجعله أداة أساسية للمطورين. باتباع هذا الدليل، ستتعلم كيفية حفظ الصور بسهولة، وهناك الكثير لتكتشفه!

## الأسئلة الشائعة

### هل يمكن لـ Aspose.PSD لـ .NET التعامل مع تنسيقات الصور الأخرى؟

ج1: بالتأكيد! يدعم Aspose.PSD تنسيقات الصور المختلفة، مما يوفر المرونة في مشاريعك.

### هل هناك نسخة تجريبية متاحة؟

ج2: نعم، يمكنك تنزيل نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الدعم لـ Aspose.PSD لـ .NET؟

 أ3: قم بزيارة[منتدى الدعم](https://forum.aspose.com/c/psd/34) للحصول على المساعدة أو لطرح الأسئلة.

### كيف أحصل على ترخيص مؤقت؟

 أ4: يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.conholdate.com/temporary-license/).

### أين يمكنني شراء Aspose.PSD لـ .NET؟

 A5: شراء Aspose.PSD لـ .NET[هنا](https://purchase.conholdate.com/buy).