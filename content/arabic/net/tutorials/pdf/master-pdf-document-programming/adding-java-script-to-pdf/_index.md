---
title: إضافة Java Script إلى ملف PDF
linktitle: إضافة ملف PDF Java Script
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: توفر هذه الوثيقة دليلاً شاملاً لإضافة عناصر تفاعلية مثل التنبيهات المنبثقة أو وظائف الطباعة التلقائية إلى مستندات PDF باستخدام Aspose.PDF لـ .NET.
type: docs
weight: 10
url: /ar/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## مقدمة
توفر هذه الوثيقة دليلاً شاملاً لإضافة عناصر تفاعلية مثل التنبيهات المنبثقة أو وظائف الطباعة التلقائية إلى مستندات PDF باستخدام Aspose.PDF for .NET. من خلال الاستفادة من إمكانيات هذه المكتبة، يمكنك إنشاء ملفات PDF ديناميكية وجذابة تلبي احتياجات المستخدمين المختلفة.

## المتطلبات الأساسية
 قبل المتابعة، تأكد من تنزيل أحدث إصدار من Aspose.PDF لـ .NET من[إصدارات Aspose](https://الإصدارات.aspose.com/pdf/net/) أو حصلت على نسخة تجريبية مجانية من خلال موقعهم على الإنترنت:[releases.aspose.com](http://releases.aspose.com).

يجب أن يكون لديك أيضًا فهم أساسي للغة C# وأن تكون على دراية ببيئة التطوير التي تستخدمها. بالإضافة إلى ذلك، إذا كنت بحاجة إلى تجنب القيود أثناء عملية التطوير، ففكر في الحصول على ترخيص مؤقت من Aspose.

## استيراد الحزم الضرورية
لبدء كتابة التعليمات البرمجية، قم باستيراد المساحات المطلوبة من مكتبة Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## الخطوة 1: تحميل ملف PDF الموجود
قم بتحميل مستند PDF الحالي الذي تريد إضافة عناصر تفاعلية إليه:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي لملف PDF الخاص بك.

## الخطوة 2: إضافة JavaScript على مستوى المستند

 لتطبيق البرنامج النصي الذي يتم تشغيله عند فتح المستند، قم بإنشاء مثيل لـ`JavascriptAction` هدف:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## الخطوة 3: إضافة JavaScript على مستوى الصفحة

 لتحفيز إجراءات محددة استنادًا إلى فتح أو إغلاق الصفحات، قم بإنشاء مثيل`JavascriptAction` كائن لكل صفحة:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## الخطوة 4: حفظ مستند PDF

لحفظ مستند PDF المعدّل، حدد مسار ملف الإخراج:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## خاتمة
باتباع هذا الدليل واستخدام Aspose.PDF for .NET، يمكنك تحسين ملفات PDF الخاصة بك بفعالية باستخدام عناصر تفاعلية. تقدم هذه المكتبة حلاً شاملاً لإنشاء مستندات ديناميكية وجذابة تلبي احتياجات المستخدمين المختلفة.

## الأسئلة الشائعة

### هل يمكنني إضافة إجراءات JavaScript متعددة إلى صفحات مختلفة في ملف PDF؟
نعم، يمكنك تعيين إجراءات JavaScript مختلفة لصفحات فردية أو للمستند بأكمله.

### هل من الممكن إزالة JavaScript من ملف PDF بعد إضافته؟
 نعم، يمكنك إزالة أو تعديل إجراءات JavaScript الموجودة عن طريق مسح`Actions` خصائص المستند أو الصفحة.

### ما هي أنواع وظائف JavaScript التي يمكنني استخدامها في ملف PDF؟
بإمكانك استخدام أي JavaScript يدعمه محرك JavaScript الخاص بـ Adobe Acrobat، مثل الطباعة والتنبيهات ومعالجة النماذج.

### هل يعمل JavaScript في جميع برامج عرض PDF؟
ستعمل معظم إجراءات JavaScript في برامج عرض PDF التي تدعم ملفات PDF التفاعلية، مثل Adobe Acrobat. ومع ذلك، قد لا تدعم بعض برامج قراءة PDF الأساسية JavaScript.