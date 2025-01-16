---
title: إنشاء صورة مصغرة مع حدود للشكل في Aspose.Slides
linktitle: إنشاء صورة مصغرة مع حدود للشكل في Aspose.Slides
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: تعرف على كيفية استخدام Aspose.Slides for .NET لإنشاء صور مصغرة ذات حدود محددة للأشكال في عروض PowerPoint التقديمية. يوفر هذا الدليل الشامل تعليمات خطوة بخطوة.
type: docs
weight: 10
url: /ar/net/tutorials/slides/mastering-image-and-video-manipulation/create-thumbnail-bounds-shape/
---
## مقدمة

إذا كنت مطورًا لـ .NET وتبحث عن طريقة فعّالة لإنشاء صور مصغرة مع حدود للأشكال في عروض PowerPoint التقديمية، فإن Aspose.Slides for .NET هي أداة ممتازة يجب أخذها في الاعتبار. تعمل هذه المكتبة القوية على تبسيط معالجة ملفات PowerPoint، مما يتيح لك استخراج البيانات القيمة والعمل بها بسلاسة. في هذا البرنامج التعليمي، سنرشدك خلال عملية إنشاء صورة مصغرة مع حدود لشكل.

## المتطلبات الأساسية

قبل البدء، تأكد من توفر ما يلي:

1.  Aspose.Slides لمكتبة .NET: قم بتنزيلها وتثبيتها من[موقع Aspose](https://releases.aspose.com/slides/net/).
2.  مسار الملف: استبدال`"Your Documents Directory"` في الكود الذي يحتوي على المسار الفعلي لمستنداتك.

## استيراد المساحات الاسمية الضرورية

للاستفادة من ميزات Aspose.Slides، ابدأ باستيراد المساحات المطلوبة في بداية مشروعك:

```csharp
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Slides;
```

## الخطوة 1: إنشاء مثيل لفئة العرض التقديمي

 أولاً، تحتاج إلى تهيئة`Presentation` الفئة التي تمثل ملف PowerPoint الخاص بك:

```csharp
string dataDir = "Your Documents Directory\\";
using (Presentation presentation = new Presentation(dataDir + "HelloWorld.pptx"))
{
    // أصبح الآن كائن العرض التقديمي الخاص بك جاهزًا للتعامل معه.
}
```

 استخدام`using` يضمن البيان الموجود هنا إصدار الموارد بشكل مناسب بعد الانتهاء منها.

## الخطوة 2: إنشاء صورة مصغرة مع حدود الشكل

بعد ذلك، ستقوم بإنشاء صورة مصغرة لشكل في العرض التقديمي الخاص بك مع الحدود المحددة:

```csharp
using (Bitmap bitmap = presentation.Slides[0].Shapes[0].GetThumbnail(ShapeThumbnailBounds.Appearance, 1, 1))
{
    // تحتوي الخريطة النقطية الآن على الصورة المصغرة ضمن الحدود المحددة.
}
```

 في هذه المقتطفة،`ShapeThumbnailBounds.Appearance` يحدد أنك تريد حدود المظهر للشكل. اضبط المعلمات (1، 1) للعرض والارتفاع حسب الحاجة بناءً على متطلبات الإخراج الخاصة بك.

## الخطوة 3: حفظ الصورة المصغرة على القرص

أخيرًا، احفظ الصورة المصغرة الناتجة بالتنسيق المفضل، مثل PNG:

```csharp
bitmap.Save(dataDir + "Shape_thumbnail_Bound_Shape_out.png", ImageFormat.Png);
```

هنا، يمكنك تخصيص اسم الملف وتنسيقه وفقًا لاحتياجات مشروعك.

تهانينا! لقد نجحت في إنشاء صورة مصغرة تحتوي على حدود لشكل باستخدام Aspose.Slides for .NET. هذه العملية بسيطة ويمكن دمجها بسهولة في تطبيقات .NET الخاصة بك.

## خاتمة

يعمل Aspose.Slides for .NET على تبسيط عملية إنشاء وإدارة عروض PowerPoint، وتزويد المطورين بأدوات قوية لإنشاء الصور المصغرة والمزيد. باتباع هذا الدليل، ستتعلم الخطوات الأساسية لاستخدام هذه المكتبة بكفاءة في مشاريعك.

## الأسئلة الشائعة

### هل Aspose.Slides متوافق مع أحدث إطار عمل .NET؟

نعم، يتم تحديث Aspose.Slides بشكل متكرر لدعم أحدث إصدارات إطار عمل .NET.

### هل يمكنني استخدام Aspose.Slides للمشاريع التجارية؟

 بالتأكيد! يوفر Aspose.Slides خيارات ترخيص متنوعة مناسبة للاستخدام الفردي والتجاري. تحقق من[هنا](https://purchase.aspose.com/buy) لمزيد من المعلومات.

### هل هناك نسخة تجريبية مجانية متاحة؟

 نعم! يمكنك استكشاف ميزات Aspose.Slides من خلال إصدار تجريبي مجاني متاح[هنا](https://releases.aspose.com/).

### كيف يمكنني الحصول على الدعم لـ Aspose.Slides؟

للحصول على المساعدة، قم بزيارة[منتدى Aspose.Slides](https://forum.aspose.com/c/slides/11) للتواصل مع المجتمع والمطورين ذوي الخبرة.

### هل يمكنني الحصول على ترخيص مؤقت لـ Aspose.Slides؟

 نعم يمكن الحصول على تراخيص مؤقتة للمشاريع قصيرة المدى[هنا](https://purchase.aspose.com/temporary-license/).