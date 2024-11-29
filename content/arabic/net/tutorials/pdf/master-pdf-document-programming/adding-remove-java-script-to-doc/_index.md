---
title: إضافة إزالة Javascript إلى مستند PDF
linktitle: إضافة إزالة Javascript إلى مستند PDF
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: يوضح لك هذا الدليل الشامل كيفية إضافة سلوكيات مخصصة، وإجراء العمليات الحسابية أو التحقق من الصحة بشكل ديناميكي، والتكامل مع تطبيقات البرامج الأخرى.
type: docs
weight: 30
url: /ar/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## مقدمة

في هذا الدليل الشامل، سنتعمق في عالم Aspose.PDF لـ .NET ونكتشف إمكاناته الكاملة لإضافة وظائف JavaScript المخصصة إلى مستندات PDF الخاصة بك. تتيح لك هذه الميزة القوية دمج عناصر ديناميكية وتحسين تجربة المستخدم وتبسيط سير العمل.

## المتطلبات الأساسية

للمتابعة، ستحتاج إلى:

1. تم تثبيت Aspose.PDF لـ .NET في مشروعك (قم بالتنزيل من[صفحة تنزيل Aspose.PDF لـ .NET](https://releases.aspose.com/pdf/net/))
2. رخصة صالحة لاستخدام المكتبة
3. AC# IDE أو محرر النصوص

## استيراد الحزم

للبدء، قم باستيراد المساحات الأساسية اللازمة إلى مشروعك:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## الخطوة 1: تهيئة مستند PDF جديد

قم بإنشاء مستند PDF جديد وأضفه إلى لوحتك:

```csharp
Document doc = new Document();
doc.Pages.Add();
```

هذا هو المكان الذي ستبدأ فيه بناء ملف PDF الخاص بك والذي يعتمد بشكل كبير على JavaScript.

## الخطوة 2: إضافة JavaScript إلى ملف PDF

 قم بإدراج وظائف JavaScript في مستندك باستخدام`doc.JavaScript` المجموعة. فيما يلي مثال:

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## الخطوة 3: حفظ ملف PDF باستخدام JavaScript

احفظ مستندك المحدث على القرص:

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

الآن، يمكنك الوصول إلى كود JavaScript وتعديله داخل ملف PDF الحالي.

## الخطوة 4: تحميل وعرض JavaScript في ملف PDF الموجود

 قم بتحميل ملف PDF يحتوي على JavaScript والوصول إلى مفاتيحه باستخدام`Keys` ملكية:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## الخطوة 5: عرض وظائف JavaScript

قم بالتكرار خلال مفاتيح JavaScript وطباعة الكود المقابل لها في وحدة التحكم:

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

يوضح هذا كيفية التحقق من وظائف JavaScript الموجودة حاليًا.

## الخطوة 6: إزالة JavaScript من ملف PDF

ابحث عن وظيفة JavaScript المطلوبة باستخدام اسمها ثم قم بإزالتها:

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

تأكد من حذف الوظيفة بنجاح عن طريق إعادة طباعة الوظائف المتبقية.

## خاتمة

في هذا الدليل الشامل، ستكتشف كيفية إطلاق العنان لقوة وظيفة JavaScript القابلة للتخصيص في Aspose.PDF for .NET. باستخدام هذه الميزة، يمكنك إنشاء ملفات PDF ديناميكية، وتحسين تجارب المستخدم، وتبسيط سير العمل. من خلال إتقان هذه الخطوات واستكشاف قدرات المكتبة بشكل أكبر، ستكون على الطريق الصحيح لإطلاق العنان لإمكانيات جديدة في تطبيقاتك.

## الأسئلة الشائعة

### هل يمكنني إضافة وظائف JavaScript متعددة إلى ملف PDF واحد؟
 نعم! يمكنك إضافة عدد لا حصر له من وظائف JavaScript باستخدام`doc.JavaScript` مجموعة.

### ماذا يحدث إذا حاولت إزالة وظيفة JavaScript غير موجودة؟
 إذا لم تكن الوظيفة موجودة،`Remove` لن تتسبب الطريقة في حدوث خطأ، ولكنها لن تزيل أي شيء أيضًا. للتعامل مع الوظائف غير الموجودة، يمكنك إضافة معالجة إضافية للأخطاء أو تعديل الكود لتجاهلها.

### هل من الممكن تشغيل JavaScript بمجرد فتح ملف PDF؟
نعم! يمكنك تكوين JavaScript لتشغيله عند تشغيل عوامل تشغيل محددة، مثل فتح المستند أو النقر فوق زر.

### هل يمكنني تعديل JavaScript بعد إضافته إلى ملف PDF؟
نعم، يمكنك تحميل ملف PDF موجود، والوصول إلى JavaScript الخاص به، وتعديل الكود، وحفظ المستند مرة أخرى.

### هل يؤثر إزالة JavaScript على بقية محتوى PDF؟
لا، إن إزالة JavaScript تؤثر فقط على النص البرمجي، أما محتوى ملف PDF فيظل كما هو.