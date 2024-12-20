---
title: خوارزمية برادلي الثنائية
linktitle: خوارزمية برادلي الثنائية
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: تعرف على كيفية تحويل صفحات PDF إلى صور TIFF ثنائية عالية الجودة باستخدام خوارزمية التحويل الثنائي برادلي في Aspose.PDF لـ .NET. يتضمن هذا الدليل خطوة بخطوة مثالاً للكود.
type: docs
weight: 30
url: /ar/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## مقدمة

في هذا البرنامج التعليمي، سنرشدك خلال عملية تحويل صفحة PDF إلى صورة TIFF باستخدام خوارزمية Bradley Binarization. يبسط Aspose.PDF for .NET هذه المهمة، مما يسمح لك بأتمتة وتبسيط سير عمل المستندات الخاصة بك بسهولة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.PDF لـ .NET: قم بتنزيل المكتبة من[هنا](https://releases.aspose.com/pdf/net/).
- Visual Studio (أو أي C# IDE).
- المعرفة الأساسية بلغة C#.
-  رخصة سارية المفعول أو[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) من Aspose.

## الخطوة 1: إعداد مشروعك

أولاً، قم بإنشاء مشروع C# جديد في IDE الخاص بك واستورد المساحات الأساسية الضرورية:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## الخطوة 2: تحديد دليل المستندات

حدد المسار إلى الدليل الذي يوجد به مستند PDF الخاص بك، بالإضافة إلى مسارات الإخراج لصور TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // المسار إلى ملف PDF الخاص بك
```

سيخزن هذا الدليل كلاً من ملف PDF المصدر وملفات TIFF المحولة.

## الخطوة 3: تحميل مستند PDF

افتح مستند PDF الذي تريد تحويله:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 يستبدل`PageToTIFF.pdf` مع اسم ملف PDF الخاص بك.

## الخطوة 4: تحديد مسارات الإخراج

قم بتحديد مسارات الإخراج لملفات TIFF المُولدة:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## الخطوة 5: ضبط دقة الصورة

اضبط الدقة لصور TIFF. كلما زاد عدد النقاط في البوصة، كلما كانت جودة الصورة أفضل:

```csharp
Resolution resolution = new Resolution(300);
```

## الخطوة 6: تكوين إعدادات TIFF

قم بتكوين الإعدادات لصورة TIFF، بما في ذلك الضغط وعمق اللون:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

يؤدي استخدام 1bpp (بت واحد لكل بكسل) إلى تحضير الصورة لإخراج ثنائي.

## الخطوة 7: إنشاء جهاز TIFF

إنشاء جهاز TIFF الذي سيتعامل مع التحويل:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## الخطوة 8: تحويل صفحة PDF إلى TIFF

تحويل الصفحة الأولى من ملف PDF إلى صورة TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## الخطوة 9: تطبيق خوارزمية برادلي الثنائية

الآن، قم بتطبيق خوارزمية برادلي لتحويل صورة TIFF ذات التدرج الرمادي إلى صورة ثنائية:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 ال`BinarizeBradley` تتطلب الطريقة تدفقين للملفات (إدخال وإخراج) وقيمة حدية. اضبط الحدية حسب الحاجة للحصول على نتائج مثالية.

## الخطوة 10: تأكيد التحويل الناجح

وأخيرًا، تأكد من نجاح التحويل:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## خاتمة

تهانينا! لقد نجحت في تحويل صفحة PDF إلى صورة TIFF وتطبيق خوارزمية Bradley Binarization باستخدام Aspose.PDF لـ .NET. هذه العملية ضرورية لأرشفة المستندات والتعرف الضوئي على الحروف والتطبيقات المهنية الأخرى. بفضل الدقة العالية والضغط الفعّال، ستكون صور المستندات واضحة وسهلة التحكم في الحجم.

## الأسئلة الشائعة

### ما هي خوارزمية برادلي؟
خوارزمية برادلي هي تقنية ثنائية تقوم بتحويل الصور ذات التدرج الرمادي إلى صور ثنائية من خلال تحديد عتبة تكيفية لكل بكسل بناءً على محيطه.

### هل يمكنني تحويل عدة صفحات PDF إلى TIFF باستخدام هذه الطريقة؟
 نعم يمكنك تعديل`Process` طريقة لتكرار جميع الصفحات في المستند للتحويل.

### ما هو الدقة الأمثل لتحويل ملفات PDF إلى TIFF؟
يوصى عمومًا بدقة 300 نقطة في البوصة للحصول على صور عالية الجودة، ولكن يمكنك ضبط هذا استنادًا إلى احتياجاتك المحددة.

### ماذا يعني 1bpp في عمق اللون؟
يشير 1bpp (بت واحد لكل بكسل) إلى أن الصورة ستكون بالأبيض والأسود، حيث يكون كل بكسل إما أسود بالكامل أو أبيض بالكامل.

### هل خوارزمية برادلي مناسبة للتعرف الضوئي على الحروف؟
نعم، غالبًا ما يتم استخدام خوارزمية برادلي في معالجة التعرف الضوئي على الحروف (OCR) لأنها تعمل على تعزيز تباين النص في المستندات الممسوحة ضوئيًا، مما يؤدي إلى تحسين دقة التعرف.