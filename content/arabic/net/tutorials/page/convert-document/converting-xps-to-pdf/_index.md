---
title: تحويل XPS إلى PDF باستخدام Aspose.Page لـ .NET
linktitle: تحويل XPS إلى PDF
second_title: واجهة برمجة تطبيقات Aspose.Page .NET
description: اكتشف كيفية تحويل مستندات XPS (مواصفات ورق XML) إلى PDF (تنسيق المستندات المحمولة) بسلاسة باستخدام مكتبة Aspose.Page القوية لـ .NET.
type: docs
weight: 11
url: /ar/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## مقدمة

في هذا البرنامج التعليمي، سنستكشف كيفية تحويل مستندات XPS (مواصفات ورق XML) إلى PDF (تنسيق المستندات المحمولة) باستخدام مكتبة Aspose.Page متعددة الاستخدامات لـ .NET. تعمل هذه المكتبة القوية على تبسيط تحويل المستندات وتوفر خيارات تخصيص متنوعة، مما يجعلها خيارًا ممتازًا للمطورين.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر ما يلي:

-  مكتبة Aspose.Page لـ .NET: قم بتنزيل وتثبيت مكتبة Aspose.Page لـ .NET من[توثيق Aspose.Page](https://reference.aspose.com/page/net/).
  
- بيئة التطوير: قم بإعداد بيئة تطوير .NET باستخدام Visual Studio أو أي بيئة تطوير متكاملة متوافقة أخرى.

- مستند XPS: قم بإعداد ملف XPS الذي ترغب في تحويله وتخزينه في دليل مخصص.

## الخطوة 1: استيراد المساحات المطلوبة

ابدأ باستيراد مساحة الأسماء اللازمة للوصول إلى وظائف Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## الخطوة 2: تهيئة دليل المستندات

قم بتحديد مسار الدليل الذي سيتم تخزين مستنداتك فيه:

```csharp
string dataDir = "Your Document Directory";
```

 تأكد من الاستبدال`"Your Document Directory"` مع المسار الفعلي إلى الدليل الذي يحتوي على مستند XPS الخاص بك.

### الخطوة 3: فتح تدفقات PDF وXPS

بعد ذلك، قم بتهيئة التدفقات لكل من ملف XPS المدخل وملف PDF المخرج:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

تأكد من تعيين المسار الصحيح لملفاتك.

### الخطوة 4: تحميل مستند XPS

الآن، قم بتحميل مستند XPS الخاص بك باستخدام مكتبة Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### الخطوة 5: تكوين خيارات حفظ PDF

قم بإعداد خيارات الحفظ لملف PDF الخاص بك، بما في ذلك جودة الصورة ومعلمات الضغط:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // ضبط مستوى جودة JPEG
    ImageCompression = PdfImageCompression.Jpeg, // استخدم ضغط JPEG للصور
    TextCompression = PdfTextCompression.Flate, // تطبيق ضغط Flate للنص
    PageNumbers = new int[] { 1, 2, 6 } // حدد أرقام الصفحات المراد تضمينها
};
```

لا تتردد في تعديل هذه المعلمات وفقًا لمتطلباتك.

### الخطوة 6: إنشاء جهاز عرض PDF

إنشاء جهاز عرض لتنسيق PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### الخطوة 7: احفظ المستند بتنسيق PDF

أخيرًا، احفظ مستند XPS بتنسيق PDF باستخدام الجهاز والخيارات المحددة:

```csharp
document.Save(device, options);
```

## خاتمة

تهانينا! لقد نجحت في تحويل مستند XPS إلى PDF باستخدام Aspose.Page لـ .NET. لا تعمل هذه المكتبة على تبسيط تحويل المستندات فحسب، بل إنها توفر أيضًا إمكانيات واسعة للتعامل مع التنسيقات المختلفة.

## الأسئلة الشائعة

### هل يمكنني تحويل ملفات XPS متعددة إلى ملف PDF واحد؟

بالتأكيد! يمكنك تكرار ملفات XPS المتعددة ودمجها في مستند PDF واحد باتباع نفس خطوات التحويل.

### ما هي تنسيقات الإخراج الأخرى التي يدعمها Aspose.Page لـ .NET؟

بالإضافة إلى PDF، يدعم Aspose.Page لـ .NET مجموعة من التنسيقات، بما في ذلك TIFF، وJPEG، وPNG.

### كيف يمكنني تخصيص مظهر ملف PDF المُحوّل؟

 يمكنك تعديل المعلمات في`PdfSaveOptions` يمكنك أيضًا ضبط إعدادات الصورة لتناسب احتياجاتك، مثل جودة JPEG وإعدادات الضغط، لتحقيق المظهر الذي تريده.

### هل هناك نسخة تجريبية متاحة لـ Aspose.Page لـ .NET؟

 نعم، يمكنك تجربة Aspose.Page لـ .NET مع توفر نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على دعم المجتمع لـ Aspose.Page لـ .NET؟

للمناقشات المجتمعية والدعم، قم بزيارة[منتدى Aspose.Page](https://forum.aspose.com/c/page/39).