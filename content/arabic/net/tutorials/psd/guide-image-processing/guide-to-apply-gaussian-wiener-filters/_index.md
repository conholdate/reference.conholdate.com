---
title: دليل لتطبيق المرشحات Gaussian وWiener في Aspose.PSD لـ .NET
linktitle: دليل لتطبيق المرشحات Gaussian وWiener
second_title: واجهة برمجة تطبيقات Aspose.PSD .NET
description: اكتشف كيفية تقليل الضوضاء بشكل فعال وتحسين جودة الصورة في تطبيقات .NET باستخدام مرشحات Gaussian وWiener مع Aspose.PSD. يرشدك هذا الدليل الشامل خلال عملية الإعداد والتصفية.
type: docs
weight: 10
url: /ar/net/tutorials/psd/guide-image-processing/guide-to-apply-gaussian-wiener-filters/
---
## مقدمة

في مجال معالجة الصور، وخاصةً ضمن بيئات .NET، يتألق Aspose.PSD كمجموعة أدوات متعددة الاستخدامات. ومن بين ميزاته العديدة، تعد القدرة على تطبيق المرشحات Gaussian وWiener قوية بشكل خاص، مما يسمح للمطورين بتحسين جودة الصورة وتقليل الضوضاء وتحسين الناتج المرئي بشكل فعال. سترشدك هذه المقالة خلال الخطوات المطلوبة لتطبيق هذه المرشحات في تطبيقاتك.

## المتطلبات الأساسية

قبل البدء، تأكد من أن لديك ما يلي:

1.  Aspose.PSD لـ .NET: قم بتنزيل المكتبة وتثبيتها من[توثيق Aspose.PSD لـ .NET](https://reference.aspose.com/psd/net/).
   
2. صورة العينة: قم بإعداد صورة عينة واحدة على الأقل بتنسيق PSD للاختبار. يمكنك العثور على مجموعة متنوعة من صور العينة في وثائق Aspose.PSD.

3. إعداد IDE: يوصى باستخدام بيئة تطوير متكاملة (IDE) متوافقة مع .NET، مثل Visual Studio، لتنفيذ التعليمات البرمجية بسلاسة.

## الخطوة 1: استيراد المساحات الأساسية الضرورية

ابدأ باستيراد المساحات المطلوبة في مشروع C# الخاص بك للوصول إلى وظائف Aspose.PSD:

```csharp
using Aspose.PSD.ImageFilters.FilterOptions;
using Aspose.PSD.ImageOptions;
```

## الخطوة 2: تحميل الصورة المشوشة

ابدأ بتحميل صورتك المشوشة إلى التطبيق. اضبط مسار الملف حسب الحاجة:

```csharp
// حدد المسار إلى دليل المستندات الخاص بك.
string dataDir = "Your Document Directory";
string sourceFile = dataDir + @"sample.psd";

// تحميل الصورة المشوشة
using (Image image = Image.Load(sourceFile))
{
    // المضي قدما في المعالجة الإضافية
}
```

## الخطوة 3: التحويل إلى RasterImage

 لضمان التوافق مع عمليات التصفية، قم بتحويل صورتك المحملة إلى`RasterImage`:

```csharp
// تأكد من أن الصورة من نوع RasterImage للتصفية
RasterImage rasterImage = image as RasterImage;
if (rasterImage == null)
{
    Console.WriteLine("The image is not a RasterImage.");
    return;
}
```

## الخطوة 4: تكوين خيارات التصفية

بعد ذلك، قم بإنشاء وتكوين خيارات المرشح Gaussian وWiener من خلال تحديد قيم نصف القطر والتنعيم:

```csharp
// إنشاء مثيل لـ GaussWienerFilterOptions باستخدام المعلمات المحددة
GaussWienerFilterOptions options = new GaussWienerFilterOptions(12, 3)
{
    Grayscale = true // تم ضبطه على true لمعالجة التدرج الرمادي
};
```

## الخطوة 5: تطبيق المرشحات

 قم بتطبيق خيارات الفلترة المكوّنة على`RasterImage`:

```csharp
// قم بتطبيق المرشحات Gaussian وWiener على الصورة
rasterImage.Filter(image.Bounds, options);
```

## الخطوة 6: احفظ الصورة الناتجة

أخيرًا، احفظ الصورة المعالجة بالتنسيق الذي تريده. في هذا المثال، سنحفظها بتنسيق GIF:

```csharp
string destName = dataDir + @"gauss_wiener_out.gif";
image.Save(destName, new GifOptions());
Console.WriteLine($"Filtered image saved to: {destName}");
```

## خاتمة

تهانينا! لقد نجحت في تطبيق مرشحات Gaussian وWiener لتحسين جودة صورتك باستخدام Aspose.PSD لـ .NET. تعد هذه المرشحات أدوات لا تقدر بثمن في سيناريوهات مختلفة، من استعادة الوضوح في الصور الفوتوغرافية إلى تحسين الرسومات في مشاريع التصميم.

## الأسئلة الشائعة

### هل يمكنني تطبيق هذه المرشحات على الصور بتنسيقات أخرى غير PSD؟

نعم، يدعم Aspose.PSD تنسيقات متعددة، بما في ذلك BMP وJPEG وPNG والمزيد، مما يسمح بمعالجة الصور بتنوع كبير.

### ماذا يعني حجم نصف القطر وقيمة السلاسة؟

يحدد حجم نصف القطر مدى تشغيل الفلتر، بينما تعمل قيمة التنعيم على ضبط مستوى التنعيم المطبق على صورتك، مما يؤثر على حدتها وتفاصيلها بشكل عام.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.PSD؟

 يمكنك الحصول على ترخيص مؤقت من خلال زيارة[صفحة الترخيص المؤقت لـ Aspose.PSD](https://purchase.conholdate.com/temporary-license/).

### أين يمكنني العثور على الدعم والموارد الإضافية؟

 للاستفسارات والمساعدة،[منتدى Aspose.PSD](https://forum.aspose.com/c/psd/34) يعد مصدرًا رائعًا للتواصل مع المجتمع وفريق الدعم.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.PSD؟

 نعم، يمكنك استكشاف ميزات Aspose.PSD عن طريق تنزيل[نسخة تجريبية مجانية](https://releases.aspose.com/).