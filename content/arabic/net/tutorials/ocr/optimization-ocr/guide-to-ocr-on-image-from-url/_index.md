---
title: دليل التعرف الضوئي على الحروف (OCR) على الصور من عنوان URL في التعرف الضوئي على الحروف (OCR) على الصور
linktitle: دليل التعرف الضوئي على الحروف (OCR) على الصور من عنوان URL في التعرف الضوئي على الحروف (OCR) على الصور
second_title: واجهة برمجة تطبيقات Aspose.OCR .NET
description: اكتشف كيفية تنفيذ التعرف الضوئي على الحروف (OCR) بسهولة في تطبيقات .NET الخاصة بك باستخدام Aspose.OCR. يرشدك هذا الدليل خطوة بخطوة خلال العملية بأكملها.
type: docs
weight: 10
url: /ar/net/tutorials/ocr/optimization-ocr/guide-to-ocr-on-image-from-url/
---
## مقدمة

يُعد التعرف الضوئي على الحروف (OCR) تقنية أساسية لاستخراج النص من الصور، مما يتيح للمطورين إنشاء تطبيقات يمكنها قراءة المعلومات النصية ومعالجتها بسلاسة. Aspose.OCR for .NET عبارة عن مكتبة قوية مصممة لتبسيط دمج قدرات التعرف الضوئي على الحروف في تطبيقات .NET الخاصة بك. سيوضح هذا الدليل كيفية تنفيذ التعرف الضوئي على الحروف على صورة مباشرة من عنوان URL في بضع خطوات بسيطة.

## المتطلبات الأساسية

قبل البدء، تأكد من توفر المتطلبات الأساسية التالية:

-  Aspose.OCR لـ .NET: قم بتنزيل مكتبة Aspose.OCR ودمجها في مشروع .NET الخاص بك من[صفحة الإصدار](https://releases.aspose.com/ocr/net/).
- بيئة التطوير: قم بإعداد بيئة تطوير .NET على جهازك (يوصى باستخدام Visual Studio).

## الخطوة 1: استيراد المساحات الأساسية الضرورية

للاستفادة من الميزات التي يقدمها Aspose.OCR، قم باستيراد المساحات المطلوبة في مشروعك:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
using Aspose.OCR.Models;
```

## الخطوة 2: تحديد دليل المستندات

 قم بتحديد دليل لمستنداتك. استبدل`"Your Document Directory"` مع المسار إلى دليل العمل الخاص بك:

```csharp
string dataDir = "Your Document Directory";
```

## الخطوة 3: توفير عنوان URL للصورة

حدد عنوان URL للصورة التي تريد استخراج النص منها. تأكد من إمكانية الوصول إلى الصورة بشكل عام:

```csharp
string uri = "https://"مثال.com/image.jpg";
```

## الخطوة 4: تهيئة Aspose.OCR

 إنشاء مثيل لـ`AsposeOcr` الفئة التي ستستخدمها لإجراء عملية التعرف الضوئي على الحروف:

```csharp
AsposeOcr api = new AsposeOcr();
```

## الخطوة 5: التعرف على النص من الصورة

 استخدم`RecognizeImageFromUri` طريقة لاستخراج النص من عنوان URL للصورة. يمكنك ضبط إعدادات التعرف المختلفة بناءً على متطلباتك المحددة:

```csharp
RecognitionResult result = api.RecognizeImageFromUri(uri, new RecognitionSettings
{
    DetectAreas = true,
    RecognizeSingleLine = false,
    AutoSkew = true,
    RecognitionAreas = new List<Rectangle>
    {
        new Rectangle(1, 3, 390, 70),
        new Rectangle(1, 72, 390, 70)
    }
});
```

## الخطوة 6: عرض نتائج التعرف

إخراج النص المعترف به مع أي معلومات ذات صلة، بما في ذلك المناطق المعترف بها والتحذيرات:

```csharp
Console.WriteLine($"Text:\n {result.RecognitionText}");
Console.WriteLine("Areas:");
result.RecognitionAreasText.ForEach(a => Console.WriteLine($"{a}"));
Console.WriteLine("Warnings:");
result.Warnings.ForEach(w => Console.WriteLine($"{w}"));
Console.WriteLine($"JSON: {result.GetJson()}");
```

## الخطوة 7: تنفيذ التطبيق الخاص بك

قم بتشغيل التطبيق الخاص بك. إذا تم تكوين كل شيء بشكل صحيح، فيجب أن ترى تنفيذًا ناجحًا لعملية التعرف الضوئي على الحروف:

```csharp
Console.WriteLine("OCR process executed successfully.");
```

## خاتمة

إن دمج قدرات التعرف الضوئي على الحروف في تطبيقات .NET أمر سهل مع Aspose.OCR. لقد أخذك هذا الدليل خلال الخطوات المهمة لإجراء التعرف الضوئي على الحروف على صورة من عنوان URL، مما أرسى الأساس لتطوير التطبيقات التي تستفيد من تقنية التعرف على النصوص.

## الأسئلة الشائعة

### هل برنامج Aspose.OCR مناسب للتعرف على لغات متعددة؟

نعم، يدعم Aspose.OCR العديد من اللغات، مما يجعله مثاليًا للتطبيقات التي تستهدف المستخدمين الدوليين.

### هل يمكن لـ Aspose.OCR التعامل مع التعرف على النصوص ذات السطر الواحد والمتعدد الأسطر؟

بالتأكيد! المكتبة متعددة الاستخدامات، حيث تسمح بالتعرف على النص أحادي السطر ومتعدد الأسطر وفقًا لاحتياجات مشروعك.

### ما هي خيارات الترخيص المتاحة لـ Aspose.OCR؟

 يمكنك التعرف على خيارات الترخيص المختلفة وإجراء عمليات الشراء من[متجر اسبوس](https://purchase.conholdate.com/buy).

### هل هناك نسخة تجريبية من Aspose.OCR؟

 نعم، تتوفر نسخة تجريبية مجانية. يمكنك استكشافها على[صفحة الإصدار](https://releases.aspose.com/).

### أين يمكنني العثور على الدعم لـ Aspose.OCR؟

للحصول على المساعدة أو المناقشات المجتمعية حول Aspose.OCR، قم بزيارة[منتدى Aspose.OCR](https://forum.aspose.com/c/ocr/16).