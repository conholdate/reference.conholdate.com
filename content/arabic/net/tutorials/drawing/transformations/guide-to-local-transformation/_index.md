---
title: دليل التحويلات المحلية باستخدام Aspose.Drawing لـ .NET
linktitle: دليل التحويلات المحلية باستخدام Aspose.Drawing
second_title: Aspose.Drawing .NET API - بديل لـ System.Drawing.Common
description: قم بترقية القدرات المرئية لتطبيق .NET الخاص بك باستخدام التحويلات المحلية باستخدام Aspose.Drawing. يرشدك هذا البرنامج التعليمي الشامل خلال عملية إنشاء رسومات مذهلة من خلال تطبيق مصفوفات التحويل.
type: docs
weight: 11
url: /ar/net/tutorials/drawing/transformations/guide-to-local-transformation/
---
## مقدمة

يتيح برنامج Aspose.Drawing for .NET للمطورين إنشاء رسومات متطورة من خلال التحويلات المحلية. سيرشدك هذا الدليل الموجز خلال إعداد التحويلات المحلية خطوة بخطوة.

## المتطلبات الأساسية

1. Aspose.Drawing لـ .NET: قم بتنزيله وتثبيته من[هنا](https://releases.aspose.com/drawing/net/).
2. دليل المستندات: اختر دليلاً لحفظ صورك.
3. المعرفة الأساسية بـ .NET: الإلمام بلغة C# ومفاهيم البرمجة الرسومية.

## استيراد مساحات الأسماء

ابدأ باستيراد المساحات الأساسية اللازمة إلى مشروع C# الخاص بك:

```csharp
using System.Drawing;
using System.Drawing.Drawing2D;
```

## الخطوة 1: إنشاء خريطة نقطية

```csharp
Bitmap bitmap = new Bitmap(1000, 800, System.Drawing.Imaging.PixelFormat.Format32bppPArgb);
```

## الخطوة 2: إنشاء كائن رسومي

```csharp
Graphics graphics = Graphics.FromImage(bitmap);
graphics.Clear(Color.FromKnownColor(KnownColor.Gray));
```

### الخطوة 3: إنشاء GraphicsPath

ارسم شكلًا بيضاويًا:

```csharp
GraphicsPath path = new GraphicsPath();
path.AddEllipse(300, 300, 400, 200);
```

### الخطوة 4: تطبيق التحويل المحلي

قم بإعداد مصفوفة التحويل الخاصة بك للدوران:

```csharp
Matrix matrix = new Matrix();
matrix.RotateAt(45, new Point(500, 400));
path.Transform(matrix);
```

### الخطوة 5: ارسم المسار المحول

استخدم قلمًا لرسم المسار على الكائن الرسومي:

```csharp
Pen pen = new Pen(Color.Blue, 2);
graphics.DrawPath(pen, path);
```

### الخطوة 6: احفظ الصورة المحولة

```csharp
bitmap.Save(@"Your Document Directory\CoordinateSystemsTransformations\LocalTransformation_out.png");
```

## خاتمة

من خلال اتباع الخطوات التالية، يمكنك تنفيذ التحويلات المحلية بسهولة باستخدام Aspose.Drawing، مما يؤدي إلى إثراء القدرات المرئية لتطبيقات .NET الخاصة بك.

## الأسئلة الشائعة

### هل يمكنني تطبيق تحويلات متعددة بالتتابع؟  
نعم، يمكنك إجراء سلسلة من التحويلات باستخدام المصفوفة.

### هل هو مناسب للتطبيقات الرسومية المعقدة؟  
بالتأكيد! يدعم Aspose.Drawing مجموعة واسعة من عمليات الرسومات.

### هل هناك أنواع أخرى من التحولات؟  
نعم، فهو يدعم الترجمة والتوسع والتحريف.

### كيفية التعامل مع الاستثناءات؟  
 تنفيذ معالجة الأخطاء واستشارة[التوثيق](https://reference.aspose.com/drawing/net/) للإرشاد.

### هل يمكنني تجربته قبل الشراء؟  
 نعم، استكشف[نسخة تجريبية مجانية](https://releases.aspose.com/).