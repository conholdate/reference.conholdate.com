---
title: استدعاء حفظ الصفحة في مستندات Word
linktitle: استدعاء حفظ الصفحة في مستندات Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تحويل كل صفحة من مستند Word بسهولة إلى صور PNG فردية باستخدام Aspose.Words for .NET. يوفر هذا الدليل تعليمات خطوة بخطوة، بما في ذلك أمثلة التعليمات البرمجية.
type: docs
weight: 10
url: /ar/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## مقدمة

هل احتجت يومًا إلى تحويل كل صفحة من مستند Word إلى صور فردية؟ سواء كنت تبحث عن إنشاء صور مصغرة لمعاينة أو تقسيم تقرير طويل إلى صور مرئية سهلة الفهم، فإن Aspose.Words for .NET يجعل هذه المهمة بسيطة وفعالة. في هذا الدليل، سنرشدك خلال عملية إعداد معاودة الاتصال لحفظ الصفحة لحفظ كل صفحة من مستندك كصورة PNG. لنبدأ!

## المتطلبات الأساسية

قبل الغوص، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: قم بتنزيله وتثبيته من[هنا](https://releases.aspose.com/words/net/).
2. Visual Studio: أي إصدار سيعمل، ولكننا سنستخدم Visual Studio 2019 لهذا الدليل.
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة بلغة C# على المتابعة بسلاسة.

## الخطوة 1: استيراد المساحات الأساسية الضرورية

أولاً، نحتاج إلى استيراد مساحات الأسماء المطلوبة. يتيح لنا هذا الوصول إلى الفئات والطرق اللازمة دون الحاجة إلى كتابة مساحة الأسماء بالكامل في كل مرة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 2: قم بتحديد دليل المستندات الخاص بك

بعد ذلك، قم بتعيين المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي يوجد فيه مستند Word المدخل وحيث سيتم حفظ الصور الناتجة.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 3: قم بتحميل مستندك

الآن، لنبدأ بتحميل المستند الذي تريد معالجته. تأكد من أن المستند الذي تحمل اسمه "Rendering.docx" موجود في الدليل المحدد.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 4: تكوين خيارات حفظ الصورة

سنقوم بإعداد خيارات حفظ الصور، مع تحديد أننا نريد حفظ الصفحات كملفات PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 هنا،`PageSet` يحدد نطاق الصفحات المراد حفظها، و`PageSavingCallback` يشير إلى فئة الاستدعاء المخصصة لدينا.

## الخطوة 5: تنفيذ استدعاء حفظ الصفحة

الآن، نحتاج إلى تنفيذ فئة الاستدعاء التي تتعامل مع كيفية حفظ كل صفحة.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 هذه الفئة تنفذ`IPageSavingCallback` الواجهة. في`PageSaving` الطريقة هي أننا نحدد نمط التسمية لكل صفحة محفوظة.

## الخطوة 6: حفظ المستند كصور

وأخيرًا، نحفظ المستند باستخدام الخيارات التي قمنا بإعدادها.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## خاتمة

تهانينا! لقد نجحت في إعداد معاودة اتصال لحفظ الصفحة لحفظ كل صفحة من مستند Word كصورة PNG منفصلة باستخدام Aspose.Words for .NET. هذه التقنية مفيدة بشكل لا يصدق للعديد من التطبيقات، من إنشاء معاينات الصفحات إلى إنشاء صور صفحات فردية للتقارير.

## الأسئلة الشائعة

### هل يمكنني حفظ الصفحات بتنسيقات غير PNG؟
 نعم! يمكنك حفظ الصفحات بتنسيقات مثل JPEG وBMP وTIFF عن طريق تغيير`SaveFormat` في`ImageSaveOptions`.

### كيف يمكنني حفظ صفحات محددة فقط؟
 لحفظ صفحات معينة، قم بتعديل`PageSet` المعلمة في`ImageSaveOptions` لتشمل الصفحات المطلوبة فقط.

### هل من الممكن تخصيص جودة الصورة؟
 بالتأكيد! يمكنك التحكم في جودة الصورة الناتجة عن طريق ضبط خصائص مثل`ImageSaveOptions.JpegQuality`.

### كيف يمكنني التعامل مع المستندات الكبيرة بكفاءة؟
بالنسبة للمستندات الكبيرة، فكر في معالجة الصفحات على دفعات لإدارة استخدام الذاكرة بشكل فعال.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟
 للحصول على أدلة وأمثلة شاملة، راجع[توثيق Aspose.Words](https://reference.aspose.com/words/net/).