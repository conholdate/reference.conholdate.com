---
title: تصدير نطاقات خلايا Excel كصور باستخدام Aspose.Cells لـ .NET
linktitle: تصدير نطاقات خلايا Excel كصور باستخدام Aspose.Cells لـ .NET
second_title: واجهة برمجة تطبيقات معالجة Excel الخاصة بـ Aspose.Cells .NET
description: تعرف خطوة بخطوة على كيفية استخدام Aspose.Cells for .NET لتحويل نطاقات معينة من الخلايا في ورقة عمل Excel إلى ملفات صور بكفاءة. يغطي هذا الدليل الشامل المتطلبات الأساسية وتعليمات الإعداد ومثال التعليمات البرمجية.
type: docs
weight: 14
url: /ar/net/tutorials/cells/mastering-rendering-and-exporting/export-excel-cell-ranges-as-images/
---
## مقدمة

عند العمل مع ملفات Excel، قد يكون مشاركة نطاقات معينة من البيانات كصور أمرًا مفيدًا للغاية—سواء للتقارير أو العروض التقديمية أو المشاركة السريعة. في هذا الدليل، سنستكشف كيفية تصدير نطاقات الخلايا إلى صور باستخدام Aspose.Cells for .NET. باستخدام التعليمات خطوة بخطوة، ستكون مجهزًا للتعامل مع هذه العملية بسلاسة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي جاهزًا:

1. Visual Studio: سوف تحتاج إلى تثبيت Visual Studio على جهاز الكمبيوتر الخاص بك.
2.  Aspose.Cells لـ .NET: قم بتنزيل المكتبة من[موقع اسبوس](https://releases.aspose.com/cells/net/)يمكنك اختيار إصدار تجريبي مجاني لاستكشاف الميزات.
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة بلغة C# و.NET على متابعة هذا البرنامج التعليمي بسهولة أكبر.
4. ملف Excel النموذجي: في هذا العرض التوضيحي، سنستخدم ملفًا باسم`sampleExportRangeOfCellsInWorksheetToImage.xlsx`، والتي يمكنك إنشاؤها للاختبار.

## الخطوة 1: استيراد الحزم الضرورية

للعمل مع ملفات Excel والصور في .NET، تحتاج إلى استيراد المساحات التالية:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

توفر هذه المساحات الأسماء الأدوات اللازمة للتعامل مع المصنفات، وعرض الصور، وإدارة خيارات الرسم.

## الخطوة 2: إعداد مسارات الدليل

بعد ذلك، قم بإنشاء مسارات الدليل المصدر والإخراج حيث يوجد ملف Excel الخاص بك والمكان الذي تريد حفظ الصورة الناتجة فيه.

```csharp
// تحديد أدلة المصدر والإخراج
string sourceDir = "Your Document Directory";
string outputDir = "Your Document Directory";
```

 يستبدل`"Your Document Directory\\"` مع مسار الملف الفعلي الخاص بك.

## الخطوة 3: إنشاء مصنف من ملف المصدر

 إنشاء`Workbook` مثال مع ملف Excel الخاص بك:

```csharp
//تحميل المصنف
Workbook workbook = new Workbook(sourceDir + "sampleExportRangeOfCellsInWorksheetToImage.xlsx");
```

يفتح هذا السطر ملف Excel الخاص بك لمزيد من المعالجة.

## الخطوة 4: الوصول إلى ورقة العمل المطلوبة

بعد فتح المصنف، ستحتاج إلى الوصول إلى ورقة العمل المحددة التي تحتوي على البيانات التي تريد تصديرها.

```csharp
// الوصول إلى ورقة العمل الأولى
Worksheet worksheet = workbook.Worksheets[0];
```

بإمكانك تغيير الفهرس إذا كانت بياناتك موجودة في ورقة مختلفة.

## الخطوة 5: تحديد منطقة الطباعة

قم بتحديد نطاق الخلايا التي تريد تحويلها إلى صورة عن طريق تعيين منطقة الطباعة:

```csharp
// تعيين منطقة الطباعة
worksheet.PageSetup.PrintArea = "D8:G16";
```

ضبط مراجع الخلايا (`D8:G16`) وفقًا لاحتياجاتك المحددة.

## الخطوة 6: تكوين هوامش الصفحة

لتجنب وجود مسافات بيضاء إضافية في صورتك المصدرة، اضبط الهوامش على الصفر:

```csharp
// تعيين الهوامش إلى الصفر
worksheet.PageSetup.LeftMargin = 0;
worksheet.PageSetup.RightMargin = 0;
worksheet.PageSetup.TopMargin = 0;
worksheet.PageSetup.BottomMargin = 0;
```

## الخطوة 7: تعيين خيارات الصورة

الآن، قم بتحديد كيفية عرض الصورة، بما في ذلك الدقة والتنسيق:

```csharp
// إنشاء خيارات الصورة
ImageOrPrintOptions options = new ImageOrPrintOptions
{
    OnePagePerSheet = true,
    ImageType = ImageType.Jpeg,
    HorizontalResolution = 200,
    VerticalResolution = 200
};
```

هنا، ستكون الصورة بتنسيق JPEG بدقة 200 نقطة في البوصة. يمكنك تعديل هذه الإعدادات حسب الحاجة.

## الخطوة 8: تحويل ورقة العمل إلى صورة

حان الوقت لتحويل النطاق المحدد إلى صورة:

```csharp
// تحويل ورقة العمل إلى صورة
SheetRender sr = new SheetRender(worksheet, options);
sr.ToImage(0, outputDir + "outputExportRangeOfCellsInWorksheetToImage.jpg");
```

سيؤدي هذا إلى حفظ الصورة في دليل الإخراج المحدد.

## الخطوة 9: تأكيد التنفيذ

لتقديم تعليقات بعد التصدير، اطبع رسالة نجاح على وحدة التحكم:

```csharp
Console.WriteLine("ExportRangeOfCellsInWorksheetToImage executed successfully.");
```

## خاتمة

لقد نجحت في تعلم كيفية تصدير نطاق من الخلايا من ورقة عمل Excel إلى صورة باستخدام Aspose.Cells for .NET! يمكن أن تكون هذه الإمكانية مفيدة بشكل خاص لمشاركة البيانات بكفاءة أو إنشاء تمثيلات مرئية لمعلوماتك.

## الأسئلة الشائعة

### هل يمكنني تغيير صيغة الصورة؟

 نعم! يمكنك بسهولة تغيير`ImageType` تحويل الخاصية إلى صيغ أخرى مثل PNG أو BMP.

### ماذا لو أردت تصدير نطاقات متعددة؟

سوف تحتاج إلى تكرار عملية العرض لكل نطاق ترغب في تصديره.

### هل هناك حد لحجم النطاق الذي يمكنني تصديره؟

تم تصميم Aspose.Cells للتعامل مع نطاقات كبيرة، ولكن الأداء قد يختلف. من الجيد إجراء الاختبار ضمن حدود معقولة.

### هل يمكنني أتمتة هذه العملية؟

بالتأكيد! يمكنك دمج هذه الوظيفة في تطبيقات أو نصوص أكبر حجمًا للأتمتة.

### أين يمكنني الحصول على الدعم الإضافي؟

 لمزيد من المساعدة، قم بزيارة[منتدى دعم Aspose](https://forum.aspose.com/c/cells/9).