---
title: حذف الصفوف حسب الإشارة المرجعية في مستندات Word باستخدام Aspose.Words لـ .NET
linktitle: حذف الصفوف حسب الإشارة المرجعية في مستندات Word باستخدام Aspose.Words لـ .NET
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية حذف صفوف معينة بكفاءة في مستندات Word من خلال استخدام الإشارات المرجعية مع Aspose.Words for .NET. يغطي هذا الدليل خطوة بخطوة تحميل المستندات.
type: docs
weight: 10
url: /ar/net/tutorials/words/mastering-bookmarks/delete-row-by-bookmark-word-documents/
---
## مقدمة

قد يبدو حذف صف من خلال الإشارة المرجعية الخاصة به في مستند Word أمرًا صعبًا، ولكن مع Aspose.Words for .NET، تصبح العملية سهلة ومباشرة. سيوفر لك هذا الدليل نهجًا خطوة بخطوة لتحقيق ذلك بكفاءة. لنبدأ!

## المتطلبات الأساسية

قبل التعمق في الكود، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: قم بتنزيله وتثبيته من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
- بيئة التطوير: استخدم Visual Studio أو أي بيئة تطوير متكاملة تدعم .NET للتنفيذ.
- المعرفة الأساسية بلغة C#: ستساعدك المعرفة بلغة C# على المتابعة بسلاسة.

## استيراد المساحات الاسمية

ابدأ باستيراد مساحات الأسماء الأساسية. توفر هذه المساحات الفئات والطرق اللازمة لمعالجة مستندات Word باستخدام Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## الخطوة 1: تحميل المستند

 قم بتحميل مستند Word الذي يتضمن الإشارة المرجعية المستهدفة. استبدل`"your-document.docx"` مع المسار إلى مستندك.

```csharp
Document doc = new Document("your-document.docx");
```

## الخطوة 2: تحديد موقع الإشارة المرجعية

حدد الإشارة المرجعية في المستند. تعد هذه الإشارة المرجعية ضرورية لتحديد الصف المحدد الذي سيتم حذفه.

```csharp
Bookmark bookmark = doc.Range.Bookmarks["YourBookmarkName"];
```

## الخطوة 3: تحديد الصف المستهدف

 بمجرد تحديد موقع الإشارة المرجعية، ستحتاج إلى العثور على الصف الذي يحتوي على هذه الإشارة المرجعية. يتضمن هذا الحصول على أقرب سلف للإشارة المرجعية، وتحديدًا من النوع`Row`.

```csharp
Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
```

## الخطوة 4: إزالة الصف

بمجرد تحديد الصف، يمكنك إزالته من المستند. تأكد من التحقق من القيم الفارغة لمنع الاستثناءات.

```csharp
row?.Remove();
```

## الخطوة 5: حفظ التغييرات

أخيرًا، احفظ المستند لتطبيق التغييرات التي أجريتها. احفظه باسم جديد إذا كنت تريد الاحتفاظ بالأصل سليمًا.

```csharp
doc.Save("output-document.docx");
```

## خاتمة

لقد تعلمت الآن كيفية حذف صف حسب الإشارة المرجعية في مستند Word باستخدام Aspose.Words for .NET. تتيح لك هذه الطريقة تحديد الصفوف بدقة استنادًا إلى الإشارات المرجعية، مما يبسط مهام إدارة المستندات بشكل كبير.

## الأسئلة الشائعة

### هل يمكنني حذف صفوف متعددة باستخدام الإشارات المرجعية؟

نعم، يمكنك تكرار الإشارات المرجعية المتعددة وتطبيق نفس منطق الحذف لكل منها.

### ماذا لو لم يتم العثور على الإشارة المرجعية؟

 إذا لم تكن الإشارة المرجعية موجودة،`bookmark` المتغير سيكون`null`، وسيتم تجاهل إزالة الصف التالي بأمان، مما يمنع حدوث الأخطاء.

### هل من الممكن التراجع عن الحذف بعد الحفظ؟

بعد حفظ المستند، تصبح التغييرات دائمة. من المستحسن الاحتفاظ بنسخة احتياطية من المستند قبل إجراء أي تعديلات.

### هل يمكنني حذف صف بناءً على معايير أخرى؟

بالتأكيد! يدعم Aspose.Words for .NET طرقًا مختلفة للتنقل بين عناصر المستند وتعديلها استنادًا إلى معايير مختلفة، مثل نوع العنصر أو المحتوى المحدد.

### هل تعمل هذه الطريقة مع جميع أنواع مستندات Word؟

تتوافق هذه التقنية مع المستندات التي يدعمها Aspose.Words لـ .NET. تأكد من أن تنسيق المستند الخاص بك مناسب للمكتبة التي تستخدمها.