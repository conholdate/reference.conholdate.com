---
title: استخراج بيانات المصنف من الرسوم البيانية باستخدام Aspose.Slides لـ .NET
linktitle: استخراج بيانات المصنف من الرسوم البيانية باستخدام Aspose.Slides لـ .NET
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: أطلق العنان لإمكانات عروض PowerPoint الخاصة بك من خلال تعلم كيفية استرداد بيانات المصنف من المخططات باستخدام Aspose.Slides for .NET. يرشدك هذا البرنامج التعليمي خطوة بخطوة خلال العملية، مما يسهل عليك استخراج بيانات المخططات واستخدامها بفعالية.
type: docs
weight: 12
url: /ar/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## مقدمة

قد يكون العمل مع عروض PowerPoint أمرًا صعبًا، وخاصةً عند استخراج بيانات قيمة من المخططات المضمنة. لحسن الحظ، يوفر Aspose.Slides for .NET حلاً قويًا يبسط هذه العملية. في هذا البرنامج التعليمي، سنرشدك خطوة بخطوة حول كيفية استرداد مصنف من مخطط داخل عرض تقديمي في PowerPoint.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، تأكد من أن لديك ما يلي جاهزًا:

### Aspose.Slides لـ .NET

يجب أن يكون لديك Aspose.Slides for .NET مثبتًا في بيئة التطوير الخاصة بك. إذا لم تقم بذلك بعد، فيمكنك تنزيله من موقع الويب:

[تنزيل Aspose.Slides لـ .NET](https://releases.aspose.com/slides/net/)

### عرض تقديمي بالبوربوينت

احتفظ بملف عرض PowerPoint الخاص بك في متناول يدك، وخاصة الملف الذي يحتوي على مخطط بالبيانات المرتبطة التي ترغب في استردادها.

## الخطوة 1: استيراد المساحات الأساسية الضرورية

للعمل بشكل فعال مع Aspose.Slides، ستحتاج أولاً إلى استيراد المساحات المطلوبة:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## الخطوة 2: تحديد دليل المستندات

حدد الدليل الذي يوجد به ملف العرض التقديمي الخاص بك:

```csharp
string dataDir = "Your Document Directory"; // قم بتعديل هذا المسار حسب الحاجة
```

## الخطوة 3: تحميل العرض التقديمي

يمكنك تحميل عرض PowerPoint أثناء تمكين استرداد المصنف من ذاكرة التخزين المؤقت للرسم البياني. وإليك كيفية القيام بذلك:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // الوصول إلى بيانات الرسم البياني والعمل بها
    // سيتم وضع الكود الخاص بك هنا
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 في هذه الخطوة،`LoadOptions` يسمح لك الكائن بتمكين استرداد المصنف باستخدام`RecoverWorkbookFromChartCache` ملكية.

## الخطوة 4: استرداد الرسم البياني والوصول إلى المصنف الخاص به

الآن حان الوقت للبحث في الرسم البياني واسترجاع البيانات المرتبطة به:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // ضبط المؤشر حسب الحاجة
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// الآن يمكنك العمل مع بيانات المصنف حسب متطلباتك
```

من خلال الوصول إلى الشكل الأول للشريحة الأولى (والذي من المتوقع أن يكون مخططًا)، يمكنك الحصول على مصنف بيانات المخطط ويمكنك معالجة البيانات أو استخراجها حسب الحاجة.

## خاتمة

في هذا البرنامج التعليمي، أوضحنا كيفية استرداد مصنف من مخطط في عرض تقديمي على PowerPoint بفعالية باستخدام Aspose.Slides for .NET. باتباع هذه الخطوات، يمكنك استخراج بيانات المخطط واستخدامها بسهولة لتلبية احتياجاتك التحليلية.

## الأسئلة الشائعة

### ما هو Aspose.Slides لـ .NET؟

Aspose.Slides for .NET عبارة عن مكتبة قوية تتيح للمطورين إنشاء عروض تقديمية من Microsoft PowerPoint ومعالجتها وتحويلها برمجيًا.

### هل يمكنني تجربة Aspose.Slides لـ .NET قبل الشراء؟

 نعم! تقدم Aspose نسخة تجريبية مجانية من Aspose.Slides لـ .NET. يمكنك تقييم إمكانياتها قبل الشراء.[احصل على النسخة التجريبية المجانية هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الوثائق الخاصة بـ Aspose.Slides لـ .NET؟

 يمكنك الوصول إلى وثائق شاملة لـ Aspose.Slides لـ .NET[هنا](https://reference.aspose.com/slides/net/)، والذي يتضمن أمثلة ومراجع API.

### كيف يمكنني شراء ترخيص لـ Aspose.Slides لـ .NET؟

 لشراء الترخيص، قم بزيارة موقع Aspose واستخدم الرابط التالي:[شراء Aspose.Slides لـ .NET](https://purchase.aspose.com/buy).