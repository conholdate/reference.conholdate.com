---
title: إنشاء أشكال المجموعات في PowerPoint باستخدام Aspose.Slides لـ .NET
linktitle: إنشاء أشكال المجموعات في PowerPoint باستخدام Aspose.Slides لـ .NET
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: تعرف على كيفية إنشاء أشكال المجموعات وإدارتها باستخدام Aspose.Slides for .NET. يوفر هذا الدليل الشامل تعليمات واضحة خطوة بخطوة.
type: docs
weight: 11
url: /ar/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## مقدمة

إن تحسين المظهر المرئي وتنظيم عروض PowerPoint الخاصة بك يمكن أن يؤثر بشكل كبير على تفاعل الجمهور. إحدى الطرق الفعّالة لتحقيق ذلك هي من خلال أشكال المجموعات. في هذا البرنامج التعليمي، سنستكشف كيفية الاستفادة من Aspose.Slides for .NET لإنشاء أشكال المجموعات في عروضك التقديمية والتلاعب بها.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

-  Aspose.Slides لـ .NET: قم بتنزيل أحدث إصدار من مكتبة Aspose.Slides وتثبيته من[موقع اسبوس](https://releases.aspose.com/slides/net/).
- بيئة التطوير: قم بإعداد IDE متوافق مع .NET، مثل Visual Studio، للعمل على مشروعك.
- المعرفة الأساسية بلغة C#: تعرف على المفاهيم الأساسية للغة C#.


## استيراد المساحات الاسمية الضرورية

في مشروع C# الخاص بك، ابدأ بتضمين المساحات الأسماءية التالية:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## الخطوة 1: إنشاء مثيل لفئة العرض التقديمي

 إنشاء مثيل لـ`Presentation`الصف الذي ستعمل فيه على شرائحك. حدد الدليل الذي يتم تخزين مستنداتك فيه:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // ستتم هنا خطوات إنشاء الأشكال والتلاعب بها
}
```

## الخطوة 2: الوصول إلى الشريحة الأولى

استرداد الشريحة الأولى من العرض التقديمي الذي قمت بإنشائه حديثًا:

```csharp
ISlide slide = pres.Slides[0];
```

## الخطوة 3: الوصول إلى مجموعة الأشكال

احصل على مجموعة الأشكال الموجودة على الشريحة:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## الخطوة 4: إضافة شكل المجموعة

الآن حان الوقت لإضافة شكل المجموعة إلى الشريحة:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## الخطوة 5: إضافة الأشكال داخل المجموعة

يمكنك ملء شكل المجموعة بأشكال فردية، مثل المستطيلات:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // الشكل 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // الشكل 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // الشكل 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // الشكل 4
```

## الخطوة 6: تحديد الإطار لشكل المجموعة

يؤدي تعيين إطار لشكل المجموعة إلى منحها حدودًا محددة:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## الخطوة 7: حفظ العرض التقديمي

وأخيرًا، احفظ العرض التقديمي المعدّل في الدليل المحدد:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## خاتمة

تهانينا! لقد نجحت في إنشاء أشكال مجموعات في عروض PowerPoint التقديمية باستخدام Aspose.Slides for .NET. من خلال تنظيم الأشكال بهذه الطريقة، يمكنك تحسين التخطيط المرئي ووضوح المحتوى بشكل كبير، مما يجعل عروضك التقديمية أكثر تأثيرًا.

## الأسئلة الشائعة

### هل Aspose.Slides متوافق مع أحدث إصدار من .NET؟

 نعم، يتم تحديث Aspose.Slides بانتظام للتوافق مع أحدث إصدارات .NET. تحقق من[التوثيق](https://reference.aspose.com/slides/net/) للحصول على أحدث تفاصيل التوافق.

### هل يمكنني تجربة Aspose.Slides قبل الشراء؟

 بالتأكيد! يمكنك تنزيل نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الدعم للاستعلامات المتعلقة بـ Aspose.Slides؟

 قم بزيارة موقع Aspose.Slides[منتدى](https://forum.aspose.com/c/slides/11) للدعم المجتمعي والمناقشات.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Slides؟

 يمكنك طلب ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

### أين يمكنني شراء ترخيص كامل لـ Aspose.Slides؟

 يمكنك شراء ترخيص من[صفحة الشراء](https://purchase.aspose.com/buy).