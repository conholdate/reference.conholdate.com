---
title: تحويل تصدير CAD إلى صورة نقطية باستخدام Aspose.CAD لـ .NET
linktitle: تحويل تصدير CAD إلى صورة نقطية
second_title: Aspose.CAD .NET - تنسيق ملفات CAD وBIM
description: تعرف على كيفية تحويل تخطيطات CAD بكفاءة إلى تنسيقات صور نقطية مختلفة باستخدام Aspose.CAD لـ .NET. يرشدك هذا الدليل الشامل خلال العملية باستخدام كود واضح.
type: docs
weight: 10
url: /ar/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## مقدمة

هل تبحث عن تحويل تخطيطات CAD إلى تنسيقات صور نقطية بسهولة باستخدام Aspose.CAD لـ .NET؟ تم تصميم هذا الدليل التفصيلي لمساعدتك في التنقل خلال العملية، مع مقتطفات برمجية موجزة لتجربة سلسة. سواء كنت مطورًا متمرسًا أو مبتدئًا، يوفر هذا البرنامج التعليمي رؤى قيمة لجميع مستويات المهارة.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

-  مكتبة Aspose.CAD لـ .NET: قم بتنزيل المكتبة وتثبيتها من[موقع Aspose.CAD](https://releases.aspose.com/cad/net/).
-  ملف رسم CAD: احصل على ملف رسم CAD الخاص بك (على سبيل المثال،`conic_pyramid.dxf`) جاهزة للتحويل.

## استيراد المساحات المطلوبة

في مشروع .NET الخاص بك، ستحتاج إلى استيراد مساحات الأسماء اللازمة لاستخدام وظائف Aspose.CAD. أضف ما يلي إلى أعلى الكود الخاص بك:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## الخطوة 1: قم بتحميل رسم CAD الخاص بك

أولاً، حدد الدليل وقم بتحميل ملف CAD الخاص بك إلى مثيل صورة:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// تحميل رسم CAD
using (var image = Image.Load(sourceFilePath))
{
    // انتقل إلى الخطوات التالية
}
```

## الخطوة 2: إنشاء خيارات التنقيح

بعد ذلك، قم بإعداد خيارات التحويل إلى صورة نقطية، وتحديد الأبعاد المطلوبة للصورة الناتجة:

```csharp
// تهيئة خيارات CadRasterization
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## الخطوة 3: تحديد الطبقات للتحويل

إذا كنت تريد تحويل طبقات معينة، فأضفها إلى خيارات التحويل إلى صور نقطية:

```csharp
// حدد الطبقة المراد تحويلها
rasterizationOptions.Layers = new [] { "LayerA" };
```

## الخطوة 4: إعداد خيارات تصدير JPEG

الآن، قم بإنشاء خيارات لتنسيق الصورة التي ترغب في التصدير إليها (JPEG في هذه الحالة):

```csharp
// إنشاء خيارات Jpeg للتصدير
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## الخطوة 5: التصدير إلى تنسيق JPEG

وأخيرًا، احفظ الصورة المحولة:

```csharp
// قم بتحديد مسار ملف الإخراج وحفظ الصورة
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## ميزة إضافية: تحويل كافة الطبقات

لتحويل كافة الطبقات في رسم CAD الخاص بك، يمكنك تنفيذ طريقة مثل هذه:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // قم بالتكرار خلال الطبقات وحفظ كل منها كملف JPEG منفصل
    // كود التنفيذ الخاص بك هنا
}
```

## خاتمة

تهانينا! لقد تعلمت كيفية تحويل تخطيطات CAD بفعالية إلى تنسيقات صور نقطية باستخدام Aspose.CAD لـ .NET. يقدم هذا الدليل نهجًا مباشرًا مناسبًا للمطورين الذين يهدفون إلى تحويلات CAD فعالة.

## الأسئلة الشائعة

### هل يمكنني التصدير إلى تنسيقات صور مختلفة؟

 بالتأكيد! قم بالتبديل ببساطة`JpegOptions` مع خيارات التنسيق الأخرى، مثل`PngOptions` أو`BmpOptions`، اعتمادًا على احتياجاتك.

### هل تتوفر نسخة تجريبية؟

 نعم، يمكنك تنزيل نسخة تجريبية لاستكشاف الوظائف من خلال اتباع هذا[وصلة](https://releases.aspose.com/cad/net/).

### أين يمكنني العثور على الدعم لـ Aspose.CAD؟

 للحصول على دعم المجتمع، راجع Aspose.CAD[منتدى](https://forum.aspose.com/c/cad/19)أو فكر في شراء ترخيص للحصول على مساعدة أكثر تخصصًا.

### هل من الممكن الحصول على تراخيص مؤقتة؟

 نعم، التراخيص المؤقتة متاحة؛ يمكنك طلب واحدة[هنا](https://purchase.conholdate.com/temporary-license/).

### أين يمكنني الوصول إلى الوثائق التفصيلية؟

 قم بزيارة الوثائق الشاملة[هنا](https://reference.aspose.com/cad/net/) لمزيد من المعلومات.