---
title: تغيير اتجاه صفحة PDF
linktitle: تغيير اتجاه صفحة PDF
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: اكتشف كيفية ضبط اتجاه الصفحة لملفات PDF بسهولة باستخدام Aspose.PDF for .NET. يوفر هذا الدليل خطوة بخطوة تعليمات واضحة حول تحميل المستندات وتدويرها وحفظها.
type: docs
weight: 10
url: /ar/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## مقدمة

هل سبق لك أن واجهت ملف PDF حيث يكون اتجاه الصفحة خاطئًا تمامًا؟ سواء كان مستندًا تم مسحه ضوئيًا بشكل غير صحيح أو مستندًا يحتاج ببساطة إلى تخطيط مختلف، فإن تعديل الاتجاه يمكن أن يحدث فرقًا كبيرًا. لحسن الحظ، يوفر Aspose.PDF for .NET طريقة قوية وسهلة الاستخدام للتعامل مع ملفات PDF، بما في ذلك تغيير اتجاه الصفحات. في هذا الدليل، سنرشدك خلال العملية خطوة بخطوة، سواء كنت تريد التبديل من الوضع الرأسي إلى الأفقي أو العكس.

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل، تأكد من أنك قمت بما يلي:

-  Aspose.PDF لـ .NET: تأكد من تثبيت مكتبة Aspose.PDF. إذا لم تقم بذلك بعد، فيمكنك[تحميله هنا](https://releases.aspose.com/pdf/net/).
- بيئة تطوير .NET: يمكنك استخدام Visual Studio، أو JetBrains Rider، أو أي بيئة تطوير متكاملة أخرى تفضلها لتطوير .NET.
- المعرفة الأساسية بلغة C#: ستساعدك المعرفة بلغة C# على المتابعة بسهولة أكبر.
- ملف PDF: قم بإعداد ملف PDF نموذجي جاهز للاختبار. يمكنك إنشاء ملف أو تنزيل نموذج عبر الإنترنت.

 إذا كنت بدأت للتو، ففكر في تجربة Aspose.PDF مع[رخصة مؤقتة مجانية](https://purchase.aspose.com/temporary-license/) قبل اتخاذ القرار[شراء النسخة الكاملة](https://purchase.aspose.com/buy).

## استيراد مساحات الأسماء

للتعامل مع صفحات PDF، ستحتاج أولاً إلى استيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك. أضف الأسطر التالية في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using System.IO;
using Aspose.Pdf;
```

الآن بعد أن قمنا بإعداد كل شيء، فلنبدأ!

## الخطوة 1: تحميل مستند PDF

 الخطوة الأولى هي تحميل ملف PDF الذي تريد تعديله. استخدم`Document` الفئة من مساحة اسم Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 تأكد من الاستبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي لملف PDF الخاص بك.

## الخطوة 2: تكرار كل صفحة

بعد ذلك، سننتقل عبر كل صفحة في مستند PDF. وهذا يسمح لنا بتطبيق تغيير الاتجاه على كل الصفحات:

```csharp
foreach (Page page in doc.Pages)
{
    // التلاعب بكل صفحة
}
```

## الخطوة 3: الوصول إلى MediaBox الخاص بالصفحة

 تحتوي كل صفحة PDF على`MediaBox` الذي يحدد حدوده. نحتاج إلى الوصول إلى هذا للتحقق من الاتجاه الحالي وإجراء التعديلات:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 ال`MediaBox` يوفر أبعاد الصفحة، بما في ذلك العرض والارتفاع.

## الخطوة 4: تبديل العرض والارتفاع

لتغيير اتجاه الصفحة، سنقوم بتبديل قيم العرض والارتفاع. سيؤدي هذا التعديل إلى تغيير أبعاد الصفحة:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

هنا، نقوم بحساب الأبعاد الجديدة وإعادة وضع الزاوية اليسرى السفلية (`LLY`) وفقاً لذلك.

## الخطوة 5: تحديث MediaBox وCropBox

 الآن بعد أن أصبح لدينا الأبعاد الجديدة، سنطبق هذه التغييرات على`MediaBox` و`CropBox` للتأكد من عرض الصفحة بشكل صحيح:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## الخطوة 6: تدوير الصفحة

لإكمال تغيير الاتجاه، سنقوم بتدوير الصفحة. هذا سهل للغاية مع Aspose.PDF:

```csharp
page.Rotate = Rotation.on90; // تدوير 90 درجة
```

يقوم هذا الخط بقلب الصفحة بشكل فعال إلى الاتجاه المطلوب.

## الخطوة 7: احفظ ملف PDF الناتج

بعد تعديل اتجاه جميع الصفحات، احفظ المستند المحدث في ملف جديد:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

تأكد من توفير اسم ملف جديد لتجنب الكتابة فوق المستند الأصلي.

## خاتمة

والآن، لقد انتهيت! إن تغيير اتجاه الصفحة في ملف PDF باستخدام Aspose.PDF لـ .NET هي عملية بسيطة. فمن خلال تحميل المستند، والتنقل بين الصفحات، وتحديث MediaBox، وحفظ الملف، يمكنك بسهولة تعديل التخطيط لتلبية احتياجاتك. سواء كنت تقوم بتصحيح مستند ممسوح ضوئيًا بشكل سيئ أو تنسيق الصفحات للعرض التقديمي، فإن هذا الدليل من شأنه أن يساعدك في إنجاز المهمة بكفاءة.

## الأسئلة الشائعة

### هل يمكنني تدوير صفحات محددة بدلاً من جميع الصفحات في ملف PDF؟  
نعم، يمكنك تعديل الحلقة لاستهداف صفحات محددة حسب فهرسها بدلاً من التكرار عبر كل الصفحات.

### ما هو`MediaBox`?  
 ال`MediaBox` يقوم بتحديد حجم وشكل الصفحة في ملف PDF، وتحديد مكان وضع المحتوى.

### هل يعمل Aspose.PDF for .NET مع تنسيقات الملفات الأخرى؟  
نعم، يمكن لبرنامج Aspose.PDF التعامل مع تنسيقات ملفات مختلفة، بما في ذلك HTML وXML وXPS والمزيد.

### هل هناك نسخة مجانية من Aspose.PDF لـ .NET؟  
 نعم يمكنك البدء بـ[نسخة تجريبية مجانية](https://releases.aspose.com/) أو اطلب[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

### هل يمكنني التراجع عن التغييرات بعد حفظها؟  
بمجرد حفظ المستند، تصبح التغييرات دائمة. من المستحسن العمل على نسخة أو الاحتفاظ بنسخة احتياطية من الملف الأصلي.