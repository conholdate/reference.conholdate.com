---
title: إضافة رسومات مملوءة بالتدرج اللوني باستخدام Aspose.PDF لـ .NET
linktitle: إضافة رسومات مملوءة بالتدرج اللوني باستخدام Aspose.PDF لـ .NET
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: أطلق العنان لإمكانات مستندات PDF الخاصة بك بالكامل من خلال هذا الدليل التفصيلي حول إضافة رسومات مذهلة مملوءة بالتدرج اللوني باستخدام Aspose.PDF لـ .NET. مثالي لتحسين التقارير والعروض التقديمية وأي مستند يتطلب ترقية بصرية.
type: docs
weight: 20
url: /ar/net/tutorials/pdf/mastering-Graph-programming/add-gradient-filled-drawings/
---
## مقدمة

في عالمنا الرقمي اليوم، يعد إنشاء مستندات جذابة بصريًا أمرًا بالغ الأهمية. إحدى الطرق الفعّالة لتحسين مستندات PDF الخاصة بك هي دمج الرسومات مع التعبئة المتدرجة. سيرشدك هذا الدليل خلال عملية استخدام Aspose.PDF لـ .NET لإضافة رسومات مذهلة مملوءة بالتدرج إلى ملفات PDF الخاصة بك. لنبدأ!

## المتطلبات الأساسية

قبل أن نتعمق في التنفيذ، تأكد من أن لديك ما يلي:

1.  Aspose.PDF لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من[موقع اسبوس](https://releases.aspose.com/pdf/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير .NET، مثل Visual Studio، لكتابة التعليمات البرمجية الخاصة بك وتنفيذها.
3. الفهم الأساسي لـ C#: إن الإلمام ببرمجة C# سيساعدك على المتابعة بسلاسة.

بمجرد أن يكون كل شيء في مكانه، يمكننا المضي قدمًا!

## الخطوة 1: إعداد مشروعك

ابدأ بإنشاء مشروع C# جديد في Visual Studio وأضف مرجعًا إلى مكتبة Aspose.PDF باستخدام NuGet Package Manager. ثم استورد المساحات الأساسية اللازمة:

```csharp
using Aspose.Pdf.Drawing;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## الخطوة 2: تحديد دليل المستندات

بعد ذلك، حدد الدليل الذي تريد حفظ ملف PDF الخاص بك فيه:

```csharp
// تعيين المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY"; // استبدله بمسار الدليل الفعلي الخاص بك
```

## الخطوة 3: إنشاء مستند PDF جديد

الآن، دعونا ننشئ مستند PDF جديد:

```csharp
Document doc = new Document();
```

## الخطوة 4: إضافة صفحة إلى المستند

أضف صفحة جديدة إلى مستندك:

```csharp
Page page = doc.Pages.Add();
```

## الخطوة 5: إنشاء كائن رسومي

لرسم الأشكال، قم بإنشاء منطقة رسومية على الصفحة:

```csharp
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(300.0, 300.0);
page.Paragraphs.Add(graph);
```

## الخطوة 6: تحديد شكل المستطيل

قم بتحديد شكل المستطيل الذي تريد تعبئته بالتدرج:

```csharp
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(0, 0, 300, 300);
graph.Shapes.Add(rect);
```

## الخطوة 7: تطبيق تعبئة متدرجة على المستطيل

الآن، دعونا نضيف تعبئة متدرجة إلى المستطيل:

```csharp
rect.GraphInfo.FillColor = new Color
{
    PatternColorSpace = new GradientAxialShading(Color.Red, Color.Blue)
    {
        Start = new Point(0, 0),
        End = new Point(300, 300)
    }
};
```

## الخطوة 8: احفظ مستند PDF

وأخيرًا، احفظ مستندك:

```csharp
doc.Save(dataDir + "GradientFilledDrawing.pdf");
```

## خاتمة

تهانينا! لقد نجحت في إضافة رسم ملون إلى مستند PDF الخاص بك باستخدام Aspose.PDF لـ .NET. يمكن لهذه التقنية البسيطة والقوية أن تعزز بشكل كبير من المظهر المرئي لمستنداتك، سواء كانت تقارير أو فواتير أو عروض تقديمية.

## الأسئلة الشائعة

### ما هو Aspose.PDF لـ .NET؟
Aspose.PDF for .NET عبارة عن مكتبة قوية تتيح للمطورين إنشاء مستندات PDF ومعالجتها وتحويلها برمجيًا.

### هل استخدام Aspose.PDF مجاني؟
 يمكنك البدء بـ[نسخة تجريبية مجانية](https://releases.aspose.com/) لاستكشاف ميزاته، ولكن كن على علم بأنه قد تكون هناك قيود على الاستخدام.

### أين يمكنني العثور على مزيد من الوثائق؟
 تتوفر وثائق شاملة على[صفحة مرجعية لـ Aspose PDF](https://reference.aspose.com/pdf/net/).

### كيف يمكنني شراء Aspose.PDF؟
 يمكنك شراء مكتبة Aspose.PDF من خلال[رابط الشراء](https://purchase.aspose.com/buy).

### ماذا لو كنت بحاجة إلى مساعدة في استخدام Aspose.PDF؟
للحصول على المساعدة، قم بزيارة[منتدى دعم Aspose](https://forum.aspose.com/c/pdf/10) حيث يمكنك طرح الأسئلة ومشاركة الخبرات مع المجتمع.