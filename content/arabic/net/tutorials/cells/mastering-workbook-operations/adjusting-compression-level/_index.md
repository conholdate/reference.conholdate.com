---
title: ضبط مستوى الضغط في المصنف
linktitle: ضبط مستوى الضغط في المصنف
second_title: واجهة برمجة تطبيقات معالجة Excel الخاصة بـ Aspose.Cells .NET
description: اكتشف كيفية إدارة ملفات Excel الكبيرة بكفاءة من خلال ضبط مستويات الضغط باستخدام Aspose.Cells for .NET. يغطي هذا الدليل التفصيلي كل شيء بدءًا من إعداد الدلائل إلى قياس أوقات الضغط، مما يساعدك على تحسين حجم الملف وتعزيز الأداء.
type: docs
weight: 14
url: /ar/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## مقدمة

قد يكون إدارة ملفات Excel الكبيرة تحديًا، خاصة عندما يتعلق الأمر بكفاءة التخزين والنقل. لحسن الحظ، يمكن لضغط الملفات تقليل حجم هذه الملفات بشكل كبير، مما يجعلها أسهل في التعامل معها. إذا كنت تستخدم Aspose.Cells لـ .NET، فلديك القدرة على ضبط مستوى ضغط المصنفات الخاصة بك بسهولة. سيرشدك هذا الدليل خلال العملية خطوة بخطوة، مع توفير تفسيرات واضحة لكل جزء من التعليمات البرمجية.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من أن لديك المتطلبات الأساسية التالية:

1. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على فهم مقتطفات التعليمات البرمجية بشكل أفضل.
2.  مكتبة Aspose.Cells: قم بتنزيل مكتبة Aspose.Cells وتثبيتها من[هنا](https://releases.aspose.com/cells/net/).
3. Visual Studio: بيئة تطوير مثل Visual Studio ضرورية لتشغيل الكود.
4. .NET Framework: تأكد من إعداد مشروعك باستخدام إصدار متوافق من .NET Framework.

## استيراد الحزم الضرورية

للبدء، تحتاج إلى استيراد الحزم اللازمة في مشروع C# الخاص بك. أضف الأسطر التالية في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 تعد هذه الحزم ضرورية للعمل مع ملفات Excel باستخدام مكتبة Aspose.Cells.`Aspose.Cells` تحتوي مساحة الاسم على جميع الفئات اللازمة للتعامل مع ملفات Excel، بينما`Aspose.Cells.Xlsb` يوفر خيارات لحفظ الملفات بتنسيق XLSB.

## الخطوة 1: تحديد أدلة المصدر والإخراج

أولاً، قم بإعداد الدلائل التي تتواجد بها ملفات المصدر والمكان الذي تريد حفظ ملفات الإخراج فيه:

```csharp
// تحديد أدلة المصدر والإخراج
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 تأكد من الاستبدال`"Your Document Directory\\"` مع المسارات الفعلية إلى الدلائل الخاصة بك. وهذا يضمن أن يتمكن برنامجك من تحديد موقع الملفات التي يحتاج إلى العمل بها.

## الخطوة 2: تحميل المصنف

بعد ذلك، قم بتحميل المصنف الذي تريد ضغطه:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 هنا، نقوم بإنشاء مثيل جديد لـ`Workbook` قم بتحميل ملف Excel الموجود. تأكد من أن اسم الملف يتطابق مع اسم الملف الموجود في دليل المصدر.

## الخطوة 3: إعداد خيارات الحفظ

الآن، قم بتكوين خيارات الحفظ للمصنف الخاص بك:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 ال`XlsbSaveOptions`تتيح لك الفئة تحديد خيارات مختلفة عند حفظ المصنف الخاص بك بتنسيق XLSB، بما في ذلك مستويات الضغط.

## الخطوة 4: قياس وقت الضغط للمستوى 1

ابدأ بمستوى الضغط الأول وقم بقياس الوقت المستغرق لحفظ المصنف:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

يؤدي هذا المقطع إلى تعيين نوع الضغط إلى المستوى 1، وحفظ المصنف، وقياس الوقت المنقضي.

## الخطوة 5: قياس وقت الضغط للمستوى 6

بعد ذلك، اختبر الأداء باستخدام ضغط المستوى 6:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

هذه الخطوة مشابهة للخطوة السابقة، ولكن بمستوى ضغط أعلى.

## الخطوة 6: قياس وقت الضغط للمستوى 9

وأخيرًا، قم بتقييم الأداء بأعلى مستوى ضغط:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

تؤدي هذه الخطوة إلى ضبط مستوى الضغط على المستوى 9، حيث من المرجح أن ترى أكبر انخفاض في حجم الملف، على الرغم من أن معالجته قد تستغرق وقتًا أطول.

## الخطوة 7: الناتج النهائي

بعد إكمال جميع مستويات الضغط، قم بإخراج رسالة تشير إلى انتهاء العملية بنجاح:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

يؤكد هذا السطر البسيط أن برنامجك تم تنفيذه دون مشاكل.

## خاتمة

إن ضبط مستوى ضغط المصنفات باستخدام Aspose.Cells for .NET هو عملية بسيطة يمكن أن تؤدي إلى تحسينات كبيرة في حجم الملف والأداء. باتباع الخطوات الموضحة في هذا الدليل، يمكنك تنفيذ الضغط بكفاءة في تطبيقاتك، مما يعزز قدرات إدارة ملفات Excel.

## الأسئلة الشائعة

### ما هو Aspose.Cells؟  
Aspose.Cells هي مكتبة قوية لـ .NET تتيح للمطورين إنشاء ملفات Excel ومعالجتها وتحويلها دون الحاجة إلى Microsoft Excel.

### كيف أقوم بتثبيت Aspose.Cells؟  
 يمكنك تنزيل Aspose.Cells وتثبيته من[موقع اسبوس](https://releases.aspose.com/cells/net/).

### ما هي مستويات الضغط المتاحة؟  
يدعم Aspose.Cells مستويات ضغط متعددة تتراوح من المستوى 1 (أقل ضغط) إلى المستوى 9 (أعلى ضغط).

### هل يمكنني اختبار Aspose.Cells مجانًا؟  
 نعم! يمكنك الحصول على نسخة تجريبية مجانية من Aspose.Cells[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على الدعم لـ Aspose.Cells؟  
 لأي استفسارات أو دعم، قم بزيارة منتدى دعم Aspose[هنا](https://forum.aspose.com/c/cells/9).