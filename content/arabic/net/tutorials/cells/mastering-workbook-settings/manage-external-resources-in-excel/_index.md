---
title: إدارة الموارد الخارجية في Excel باستخدام Aspose.Cells لـ .NET
linktitle: إدارة الموارد الخارجية في Excel باستخدام Aspose.Cells لـ .NET
second_title: واجهة برمجة تطبيقات معالجة Excel الخاصة بـ Aspose.Cells .NET
description: اكتشف كيفية التحكم بسلاسة في الموارد الخارجية في مصنفات Excel باستخدام Aspose.Cells for .NET. يرشدك هذا الدليل الشامل خلال كل خطوة - من تنفيذ موفر تدفق مخصص إلى عرض أوراق العمل.
type: docs
weight: 10
url: /ar/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## مقدمة

عند العمل بالبيانات في Excel، يمكن لإدارة الموارد الخارجية بسلاسة أن تعزز بشكل كبير من وظائف التطبيق الخاص بك. إذا كنت تبحث عن التحكم في الصور والعناصر الخارجية الأخرى في مصنفات Excel باستخدام Aspose.Cells for .NET، فأنت في المكان المناسب! سيرشدك هذا الدليل خلال العملية خطوة بخطوة، مما يتيح لك تنفيذ حل مخصص للتعامل مع هذه الموارد دون عناء.

## المتطلبات الأساسية

قبل أن نتعمق في جوانب الترميز، تأكد من إعداد ما يلي:

1. Visual Studio: بيئة تطوير متكاملة لكتابة واختبار تطبيقات .NET. يوصى باستخدام Visual Studio نظرًا لدعمه الشامل وواجهته سهلة الاستخدام.
2.  Aspose.Cells لـ .NET: قم بتنزيل المكتبة من[صفحة إصدار Aspose Cells](https://releases.aspose.com/cells/net/).
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة بمفاهيم C# و.NET على فهم التنفيذ بشكل أفضل.
4. إعداد مشروعك: تأكد من أن مشروعك يشير إلى مكتبة Aspose.Cells، والتي يمكنك إضافتها عبر NuGet Package Manager في Visual Studio.
5. ملفات العينة: قم بإعداد ملف Excel نموذجي يحتوي على موارد خارجية (على سبيل المثال، صور مرتبطة) لأغراض العرض التوضيحي.

بمجرد توفر كل هذه المتطلبات الأساسية لديك، فلنبدأ في إدارة الموارد الخارجية باستخدام Aspose.Cells.

## استيراد الحزم
للبدء في كتابة التعليمات البرمجية، ستحتاج إلى استيراد الحزم اللازمة في ملف C# الخاص بك. إليك ما تحتاجه:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## الخطوة 1: تحديد الدلائل

أولاً، قم بتحديد دليل المصدر والإخراج الذي سيتم تخزين ملفاتك فيه والمكان الذي تريد حفظ ملفات الإخراج فيه.

```csharp
// تحديد دليل المصدر
static string sourceDir = @"C:\Path\To\Your\Documents\"; // تخصيص المسار
// تحديد دليل الإخراج
static string outputDir = @"C:\Path\To\Your\Output\";
```

تأكد من استبدال المسارات بالدلائل الفعلية على جهازك.

### الخطوة 2: تنفيذ واجهة IStreamProvider

 بعد ذلك، قم بإنشاء فئة مخصصة لتنفيذ`IStreamProvider` ستقوم هذه الفئة بإدارة كيفية الوصول إلى الموارد الخارجية مثل الصور.

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // تنظيف الموارد إذا لزم الأمر
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // فتح مجرى الملف للمورد الخارجي
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 في`InitStream` الطريقة هي أننا نفتح الملف الذي يعمل كمورد خارجي ونقوم بتعيينه إلى`Stream` ملكية.

### الخطوة 3: تحميل ملف Excel

الآن، دعنا نقوم بتحميل مصنف Excel الذي يتضمن المورد الخارجي.

```csharp
public static void Execute()
{
    // تحميل ملف Excel
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // تعيين موفر البث المخصص
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

يقوم هذا المقطع بتحميل ملف Excel الخاص بك وتعيين موفر البث المخصص للتعامل مع الموارد الخارجية.

### الخطوة 4: الوصول إلى ورقة العمل

بعد تحميل المصنف، يمكنك الوصول إلى ورقة العمل المطلوبة بسهولة.

```csharp
    // الوصول إلى ورقة العمل الأولى
    Worksheet worksheet = workbook.Worksheets[0];
```

بإمكانك الوصول إلى أي ورقة عمل عن طريق تحديد فهرسها.

### الخطوة 5: تكوين خيارات الصورة والطباعة

قم بتحديد الشكل الذي تريد أن تبدو عليه الصورة الناتجة عن طريق تكوين خيارات الصورة أو الطباعة.

```csharp
    // تحديد خيارات الصورة أو الطباعة
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

يؤدي اختيار تنسيق PNG إلى ضمان الحصول على إخراج واضح ونقي.

### الخطوة 6: تحويل ورقة العمل إلى صورة

الآن يأتي الجزء المثير - تحويل ورقة العمل إلى ملف صورة!

```csharp
    // إنشاء عرض تقديمي للورقة وتحويل ورقة العمل إلى صورة
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

يقوم هذا الكود بتحويل ورقة العمل بأكملها إلى صورة PNG، والتي سيتم حفظها في دليل الإخراج المحدد.

## خاتمة

تهانينا! لقد تعلمت الآن كيفية التحكم في الموارد الخارجية في ملفات Excel باستخدام Aspose.Cells for .NET. لا تعمل هذه الوظيفة على تعزيز قدرات تطبيقك فحسب، بل إنها تبسط أيضًا كيفية إدارة مجموعات البيانات والعروض التقديمية. باتباع الخطوات الموضحة أعلاه، يمكنك تكييف هذا الحل ليناسب المتطلبات الفريدة لمشروعك.

## الأسئلة الشائعة

### ما هو Aspose.Cells؟
Aspose.Cells عبارة عن مكتبة قوية مصممة لمطوري .NET لإنشاء ملفات Excel ومعالجتها وإدارتها دون الحاجة إلى Microsoft Excel.

### كيف يمكنني تنزيل Aspose.Cells لـ .NET؟
 يمكنك تنزيله من[موقع اسبوس](https://releases.aspose.com/cells/net/).

### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم! تقدم Aspose نسخة تجريبية مجانية من Aspose.Cells، متاحة على موقعها[صفحة الإصدار](https://releases.aspose.com/cells/net/).

### ما هي أنواع الملفات التي يدعمها Aspose.Cells؟
يدعم Aspose.Cells تنسيقات Excel المختلفة، بما في ذلك XLS، وXLSX، وCSV، والمزيد.

### أين يمكنني العثور على الدعم لـ Aspose.Cells؟
 قم بزيارة[منتدى اسبوس](https://forum.aspose.com/c/cells/9) للحصول على المساعدة والدعم المجتمعي.