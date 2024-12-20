---
title: إضافة رسم في ملف PDF
linktitle: إضافة رسم في ملف PDF
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: تعرف على كيفية تحسين ملفات PDF الخاصة بك عن طريق إضافة رسومات مخصصة باستخدام Aspose.PDF لـ .NET. يغطي هذا البرنامج التعليمي خطوة بخطوة كل شيء بدءًا من إعداد مشروعك وحتى إنشاء الرسومات.
type: docs
weight: 10
url: /ar/net/tutorials/pdf/mastering-Graph-programming/adding-drawing/
---
## مقدمة

إن تحسين مستندات PDF باستخدام رسومات مخصصة يمكن أن يحسن بشكل كبير من مظهرها ووظائفها. سواء كنت تعمل على تقارير أو عروض تقديمية أو نماذج تفاعلية، فإن Aspose.PDF for .NET يوفر طريقة فعّالة لتضمين رسومات وأشكال مخصصة. سيرشدك هذا البرنامج التعليمي خطوة بخطوة خلال عملية إضافة الرسومات إلى ملف PDF.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.PDF لـ .NET: قم بتنزيله من[موقع اسبوس](https://releases.aspose.com/pdf/net/).
2. .NET Framework: يفترض هذا البرنامج التعليمي أن لديك بيئة تطوير .NET مهيأة.
3. Visual Studio: على الرغم من أنه ليس ضروريًا، إلا أن Visual Studio يبسط عملية الترميز واستكشاف الأخطاء وإصلاحها.
4. المعرفة الأساسية بلغة C#: ستكون المعرفة ببرمجة C# مفيدة.

## استيراد الحزم الضرورية

للبدء، قم باستيراد المساحات المطلوبة في مشروعك:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

دعنا ننشئ مثالًا بسيطًا يضيف مستطيلًا بلون تعبئة شفاف إلى مستند PDF.

## الخطوة 1: إعداد مشروعك

قم بتحديد المسار الخاص بمستنداتك وحدد معلمات اللون الخاصة برسمك:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // استبدله بمسار الدليل الخاص بك
int alpha = 100; // التحكم في الشفافية (0-255)
int red = 100;
int green = 0;
int blue = 0;
```

## الخطوة 2: إنشاء كائن ملون

تهيئة اللون بالشفافية:

```csharp
Aspose.Pdf.Color alphaColor = Aspose.Pdf.Color.FromArgb(alpha, red, green, blue);
```

## الخطوة 3: إنشاء كائن المستند

إنشاء مستند جديد يحتوي على رسوماتك:

```csharp
Document document = new Document();
```

## الخطوة 4: إضافة صفحة إلى المستند

قم بإنشاء صفحة جديدة حيث سيتم وضع الرسم الخاص بك:

```csharp
Page page = document.Pages.Add();
```

## الخطوة 5: إنشاء كائن رسم بياني

قم بتحديد الرسم البياني الذي سيتم رسم الأشكال الخاصة بك فيه:

```csharp
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(300.0, 400.0);
```

## الخطوة 6: تعيين حدود لكائن الرسم البياني

أضف حدودًا مرئية لتمييز الرسم البياني:

```csharp
graph.Border = new Aspose.Pdf.BorderInfo(Aspose.Pdf.BorderSide.All, Aspose.Pdf.Color.Black);
```

## الخطوة 7: إضافة الرسم البياني إلى الصفحة

الآن، أضف الرسم البياني إلى مجموعة الصفحة:

```csharp
page.Paragraphs.Add(graph);
```

## الخطوة 8: إنشاء كائن مستطيل وتكوينه

قم بتحديد حجم المستطيل ولونه وملؤه:

```csharp
Aspose.Pdf.Drawing.Rectangle rectangle = new Aspose.Pdf.Drawing.Rectangle(0, 0, 100, 50);
rectangle.GraphInfo.Color = Aspose.Pdf.Color.Red; // تعيين لون الحدود
rectangle.GraphInfo.FillColor = alphaColor; // تعيين لون التعبئة مع الشفافية
```

## الخطوة 9: أضف المستطيل إلى الرسم البياني

أضف المستطيل إلى مجموعة أشكال الرسم البياني:

```csharp
graph.Shapes.Add(rectangle);
```

## الخطوة 10: احفظ مستند PDF

وأخيرًا، احفظ مستند PDF الخاص بك باستخدام الرسم المضاف حديثًا:

```csharp
dataDir = dataDir + "AddDrawing_out.pdf";
document.Save(dataDir);
```

## خاتمة

يوضح هذا البرنامج التعليمي كيفية إثراء ملف PDF برسومات مخصصة باستخدام Aspose.PDF for .NET. باتباع هذه الخطوات، يمكنك بسهولة إضافة رسومات لتعزيز وظائف وجماليات مستنداتك.

## الأسئلة الشائعة

### ما هو Aspose.PDF لـ .NET؟

Aspose.PDF for .NET عبارة عن مكتبة قوية مصممة لإنشاء ملفات PDF ومعالجتها برمجيًا داخل تطبيقات .NET.

### كيف يمكنني تنزيل Aspose.PDF لـ .NET؟

 قم بزيارة[صفحة إصدارات Aspose](https://releases.aspose.com/pdf/net/) لتحميل المكتبة.

### هل Aspose.PDF لـ .NET مجاني؟

 يقدم Aspose إصدارًا تجريبيًا مجانيًا يمكنك الحصول عليه من[صفحة التجربة المجانية](https://releases.aspose.com/).

### أين يمكنني العثور على وثائق Aspose.PDF لـ .NET؟

 الوثائق متاحة على[موقع توثيق Aspose](https://reference.aspose.com/pdf/net/).

### كيف أحصل على الدعم لـ Aspose.PDF لـ .NET؟

 للحصول على الدعم، قم بزيارة[منتديات اسبوس](https://forum.aspose.com/c/pdf/10).