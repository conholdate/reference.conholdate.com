---
title: قص الصور باستخدام Aspose.Drawing في .NET
linktitle: قص الصور باستخدام Aspose.Drawing
second_title: Aspose.Drawing .NET API - بديل لـ System.Drawing.Common
description: استخدم قوة معالجة الصور في تطبيقات .NET الخاصة بك من خلال دليلنا خطوة بخطوة لقص الصور باستخدام Aspose.Drawing. يغطي هذا البرنامج التعليمي كل ما تحتاج إلى معرفته، من إنشاء خريطة نقطية إلى حفظ الصورة المقصوصة النهائية.
type: docs
weight: 10
url: /ar/net/tutorials/drawing/master-image-editing/image-cropping/
---
## مقدمة

في عالم تطوير .NET، قد يكون التعامل مع الصور مهمة معقدة. ولحسن الحظ، يوفر Aspose.Drawing مجموعة أدوات قوية للتعامل مع الصور، بما في ذلك القدرة على اقتصاصها بدقة. في هذا البرنامج التعليمي، سنرشدك خلال العملية البسيطة لقص الصور باستخدام Aspose.Drawing، مما يتيح لك تحسين مهارات معالجة الصور لديك!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر ما يلي:

- مكتبة Aspose.Drawing: تأكد من دمج مكتبة Aspose.Drawing في مشروع .NET الخاص بك. يمكنك تنزيلها[هنا](https://releases.aspose.com/drawing/net/).
  
-  دليل الصور: خصص دليلًا لصور مشروعك. ستحتاج إلى استبدال`"Your Document Directory"` في مقتطفات التعليمات البرمجية مع المسار إلى مجلد الصور الخاص بك.

## الخطوة 1: استيراد المساحات الأساسية الضرورية

ابدأ باستيراد المساحات المطلوبة:

```csharp
using System.Drawing;
```

سيؤدي هذا إلى إعداد البيئة الخاصة بك للعمل مع الخرائط النقطية والرسومات.

## الخطوة 2: إنشاء خريطة نقطية

 بعد ذلك، قم بإنشاء ملف جديد`Bitmap` هذا هو الكائن. سيكون هذا هو القماش الذي سنرسم عليه الصورة المقصوصة.

```csharp
Bitmap bitmap = new Bitmap(1000, 800, System.Drawing.Imaging.PixelFormat.Format32bppPArgb);
```

يمكنك تعديل العرض والارتفاع حسب احتياجاتك.

## الخطوة 3: إنشاء كائن رسومي

 مع خريطة البتات جاهزة، قم بإنشاء`Graphics` هدف:

```csharp
Graphics graphics = Graphics.FromImage(bitmap);
graphics.InterpolationMode = InterpolationMode.NearestNeighbor;
```

 ال`Graphics` سيعمل الكائن على تمكين عمليات الرسم على الخريطة النقطية.`InterpolationMode` يمكن ضبطها بناءً على متطلبات الجودة الخاصة بك.

## الخطوة 4: تحميل الصورة للقص

الآن قم بتحميل الصورة التي تريد اقتصاصها:

```csharp
Bitmap image = new Bitmap("Your Document Directory" + @"Images\aspose_logo.png");
```

 يستبدل`"Your Document Directory"` مع المسار الفعلي لمجلد الصور الخاص بك، وضبط اسم الملف حسب الحاجة.

## الخطوة 5: تحديد المستطيلات المصدر والوجهة

بعد ذلك، قم بتحديد المستطيلات التي تحدد منطقة الاقتصاص:

```csharp
Rectangle sourceRectangle = new Rectangle(0, 0, 50, 40); // مساحة للزراعة
Rectangle destinationRectangle = sourceRectangle; // نفس الحجم للوجهة
```

في هذا المثال، نقوم بقص مساحة 50×40 بكسل من الزاوية العلوية اليسرى للصورة.

## الخطوة 6: قم بإجراء عملية القطع

الآن حان الوقت لإجراء عملية القطع:

```csharp
graphics.DrawImage(image, destinationRectangle, sourceRectangle, GraphicsUnit.Pixel);
```

 ال`DrawImage` تقوم الطريقة بنسخ المنطقة المحددة من صورة المصدر إلى منطقة الوجهة المحددة.

## الخطوة 7: احفظ الصورة المقصوصة

وأخيرًا، احفظ صورتك المقصوصة:

```csharp
bitmap.Save("Your Document Directory" + @"Images\Cropping_out.png");
```

تأكد من تحديد مسار الإخراج واسم الملف المطلوب.

## خاتمة

تهانينا! لقد نجحت في تعلم كيفية اقتصاص صورة باستخدام Aspose.Drawing for .NET. يمكن بسهولة تكييف هذه الوظيفة القوية ودمجها في مشاريعك، مما يفتح إمكانيات جديدة للتلاعب بالصور وتحسينها.

## الأسئلة الشائعة

### هل يمكنني قص الصور بأي تنسيق باستخدام Aspose.Drawing؟

بالتأكيد! يدعم برنامج Aspose.Drawing تنسيقات الصور المختلفة، مما يوفر لك المرونة التي تحتاجها لمشاريعك.

### هل تتوفر خيارات قص متقدمة؟

نعم، يوفر Aspose.Drawing ميزات اقتصاص متقدمة، مما يسمح لك بتحسين معالجة الصور الخاصة بك للحصول على نتائج أفضل.

### هل يمكنني تطبيق عمليات اقتصاص متعددة على صورة واحدة؟

بالتأكيد! يمكنك تنفيذ عمليات اقتصاص متعددة معًا لتحقيق تحولات معقدة بسهولة.

### هل برنامج Aspose.Drawing مناسب لمعالجة الصور بالدفعات؟

في الواقع! يتميز برنامج Aspose.Drawing بقدرته على معالجة الدفعات، مما يجعله فعالاً في التعامل مع صور متعددة في عملية واحدة.

### أين يمكنني الحصول على الدعم للاستعلامات المتعلقة بـ Aspose.Drawing؟

للحصول على المساعدة، قم بزيارة[منتدى الرسم Aspose](https://forum.aspose.com/c/diagram/17) للتواصل مع المجتمع وطلب المساعدة لاستفساراتك.