---
title: إضافة مربعات نصية في ملفات PDF باستخدام Aspose.PDF لـ .NET
linktitle: إضافة مربعات نصية في ملفات PDF باستخدام Aspose.PDF لـ .NET
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: يستكشف هذا البرنامج التعليمي الشامل كيفية تحويل مستندات PDF إلى نماذج تفاعلية باستخدام Aspose.PDF for .NET. تعرف على العملية خطوة بخطوة لإضافة حقول مربع نص قابلة للتخصيص، وتحسين تجربة المستخدم وكفاءة جمع البيانات.
type: docs
weight: 290
url: /ar/net/tutorials/pdf/mastering-pdf-forms/adding-text-boxes/
---
## مقدمة

في المشهد الرقمي الحالي، يعد تحسين تجربة المستخدم من خلال المستندات التفاعلية أمرًا ضروريًا. لا تعمل نماذج PDF التفاعلية على تبسيط عملية جمع البيانات فحسب، بل إنها تجذب المستخدمين أيضًا بطريقة لا تستطيع المستندات الثابتة القيام بها. Aspose.PDF for .NET هي مكتبة قوية مصممة لمساعدة المطورين على دمج حقول النماذج المختلفة في مستندات PDF دون عناء. ومن بين هذه الحقول، تعد مربعات النص مفيدة بشكل خاص لجمع مدخلات المستخدم بطريقة منظمة. في هذا البرنامج التعليمي، سنشرح عملية إضافة مربع نص إلى ملف PDF باستخدام Aspose.PDF for .NET، مما يضمن حصولك على فهم شامل لكل خطوة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. المعرفة الأساسية بلغة C#: ستساعدك المعرفة بقواعد لغة C# وبنيتها على متابعة الكود.
2.  تم تثبيت Aspose.PDF لـ .NET: قم بتنزيل مكتبة Aspose.PDF وتثبيتها من[موقع](https://releases.aspose.com/pdf/net/).
3. بيئة التطوير: استخدم IDE مثل Visual Studio للترميز والاختبار.
4. .NET Framework: تأكد من تثبيت إصدار متوافق من .NET Framework.

مع توفر هذه المتطلبات الأساسية، أصبحنا جاهزين للبدء في الترميز!

### افتح IDE الخاص بك

قم بتشغيل بيئة التطوير المفضلة لديك (يوصى باستخدام Visual Studio).

### إنشاء مشروع جديد

قم بإعداد مشروع C# جديد عن طريق تحديد "إنشاء مشروع جديد" واختيار قالب تطبيق وحدة التحكم للبساطة.

### تثبيت حزمة Aspose.PDF

قم بدمج مكتبة Aspose.PDF في مشروعك باستخدام مدير الحزم NuGet. في وحدة تحكم مدير الحزم، قم بتشغيل:

```bash
Install-Package Aspose.PDF
```

## استيراد مساحة اسم Aspose.PDF

 في الجزء العلوي من ملف البرنامج الرئيسي الخاص بك (عادةً`Program.cs`), تتضمن مساحات الأسماء التالية:

```csharp
using System.IO;
using System;
using Aspose.Pdf.Forms;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
```

هذا الإعداد يجهزك للمهام المثيرة القادمة!

الآن بعد أن أصبح كل شيء جاهزًا، دعنا نقوم بتفصيل الخطوات لإضافة مربع نص إلى مستند PDF الخاص بك.

## الخطوة 1: قم بتحديد دليل المستندات الخاص بك

 أولاً، حدد الدليل الذي يوجد به مستند PDF الخاص بك. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: افتح مستند PDF 

 قم بتحميل ملف PDF إلى مثيل`Document` فصل:

```csharp
Document pdfDocument = new Document(dataDir + "TextField.pdf");
```

 تأكد من ذلك`"TextField.pdf"` موجود في الدليل المحدد.

## الخطوة 3: إنشاء حقل مربع النص

الآن، دعونا نقوم بإنشاء حقل مربع النص:

```csharp
TextBoxField textBoxField = new TextBoxField(pdfDocument.Pages[1], new Aspose.Pdf.Rectangle(100, 200, 300, 300));
```

-  جديد`TextBoxField` تم تهيئة الكائن للصفحة الثانية من ملف PDF الخاص بك.
-  ال`Rectangle` يحدد المعامل موضع وحجم مربع النص باستخدام الإحداثيات (x1، y1، x2، y2).

## الخطوة 4: تعيين خصائص حقل مربع النص 

قم بتخصيص مربع النص الخاص بك باستخدام الخصائص التالية:

```csharp
textBoxField.PartialName = "textbox1";
textBoxField.Value = "Text Box";
```

- `PartialName` يعطي معرفًا فريدًا لمربع النص.
- `Value` تعيين النص الافتراضي الذي يظهر داخل المربع.

## الخطوة 5: تخصيص الحدود

دعونا نعمل على تحسين مظهر مربع النص الخاص بنا عن طريق تخصيص حدوده:

```csharp
Border border = new Border(textBoxField);
border.Width = 5; 
border.Dash = new Dash(1, 1);
textBoxField.Border = border;
textBoxField.Color = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Green);
```

- إنشاء حدود وتحديد عرضها.
- تطبيق نمط متقطع على الحدود.
- تعيين اللون الأخضر لمربع النص.

## الخطوة 6: إضافة مربع النص إلى المستند

الآن، سنضيف حقل مربع النص إلى مستند PDF الخاص بنا:

```csharp
pdfDocument.Form.Add(textBoxField, 1);
```

يقوم هذا السطر بدمج مربع النص في الصفحة الأولى من ملف PDF.

## الخطوة 7: احفظ ملف PDF المعدّل

وأخيرًا، قم بحفظ التغييرات باستخدام الكود التالي:

```csharp
dataDir = dataDir + "TextBox_out.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nTextbox field added successfully.\nFile saved at " + dataDir);
```

يحفظ هذا المقطع ملف PDF المعدّل باسم جديد. تحقق من مسار الإخراج لملف PDF الذي أنشأته حديثًا!

## خاتمة

تهانينا! لقد نجحت في إضافة مربع نص إلى مستند PDF باستخدام Aspose.PDF لـ .NET. لا تعمل هذه العملية على تعزيز التفاعل بين ملفات PDF فحسب، بل إنها تعمل أيضًا على تحسين مشاركة المستخدم بشكل كبير. سواء كنت تجمع مدخلات المستخدم أو تجري استطلاعات أو تنشئ نماذج، يمكن لمربعات النص أن ترفع من وظائف مستندات PDF الخاصة بك. في المرة التالية التي تنشئ فيها ملف PDF، تذكر قوة الحقول التفاعلية ومدى سهولة تنفيذها باستخدام Aspose.PDF.

## الأسئلة الشائعة

### ما هو Aspose.PDF لـ .NET؟
Aspose.PDF for .NET هي مكتبة شاملة تتيح إنشاء مستندات PDF ومعالجتها وتحويلها في تطبيقات .NET.

### هل يمكنني تجربة Aspose.PDF مجانًا؟
 نعم، تقدم Aspose نسخة تجريبية مجانية يمكنك الوصول إليها[هنا](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.PDF؟
 يمكنك العثور على الدعم ومناقشات المجتمع في[منتدى اسبوس](https://forum.aspose.com/c/pdf/10).

### ما هي أنواع حقول النموذج التي يمكنني إضافتها باستخدام Aspose.PDF؟
يمكنك إضافة مربعات نصية، ومربعات اختيار، وأزرار راديو تفاعلية، وقوائم منسدلة، والمزيد.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.PDF؟
 يمكنك طلب ترخيص مؤقت من[هذا الرابط](https://purchase.aspose.com/temporary-license/).