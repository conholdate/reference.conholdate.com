---
title: إنشاء إشارة مرجعية في مستند Word باستخدام Aspose.Words لـ .NET
linktitle: إنشاء إشارة مرجعية في مستند Word باستخدام Aspose.Words لـ .NET
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تحسين مستندات Word الخاصة بك عن طريق إنشاء وإدارة الإشارات المرجعية باستخدام Aspose.Words for .NET. هذا دليل تعليمي خطوة بخطوة.
type: docs
weight: 10
url: /ar/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## مقدمة

قد يكون التنقل عبر المستندات الكبيرة أمرًا صعبًا، ولكن الإشارات المرجعية تجعل الأمر سهلاً للغاية! سيرشدك هذا البرنامج التعليمي خلال إنشاء إشارات مرجعية في مستند Word باستخدام Aspose.Words for .NET. ستتعلم خطوة بخطوة كيفية إعداد المستند وإضافة الإشارات المرجعية وحفظه بتنسيق PDF. لنبدأ!

## المتطلبات الأساسية

قبل الغوص، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET Library: قم بتنزيلها وتثبيتها من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: استخدم Visual Studio أو أي بيئة تطوير متكاملة متوافقة مع .NET.
3. المعرفة الأساسية بلغة C#: ستكون المعرفة بمفاهيم برمجة C# مفيدة.

## استيراد المساحات الاسمية

أولاً، قم باستيراد المساحات الأساسية اللازمة للعمل مع Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد المستند وDocumentBuilder

 إنشاء مستند جديد وبدء تشغيله`DocumentBuilder`، والذي يسمح لك بإضافة المحتوى والإشارات المرجعية.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إنشاء الإشارة المرجعية الرئيسية

لإنشاء إشارة مرجعية، يجب عليك تحديد نقطة البداية والنهاية. إليك كيفية إنشاء إشارة مرجعية باسم "إشارتي المرجعية":

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`:يشير إلى بداية الإشارة المرجعية.
- `Writeln`:يضيف نصًا داخل الإشارة المرجعية.

## الخطوة 3: إنشاء إشارة مرجعية متداخلة

يمكنك تضمين إشارات مرجعية لتنظيم أفضل. إليك كيفية إضافة "إشارة مرجعية متداخلة" داخل "إشارتي المرجعية":

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- يتيح لك التعشيش إنشاء هيكل هرمي. 
- `EndBookmark`:إغلاق الإشارة المرجعية الحالية.

## الخطوة 4: إضافة نص خارج الإشارة المرجعية المتداخلة

بعد إنشاء الإشارة المرجعية المتداخلة، استمر في إضافة المحتوى داخل الإشارة المرجعية الرئيسية:

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
يضمن هذا أن الإشارة المرجعية الرئيسية تتضمن الإشارة المرجعية المتداخلة وأي نص إضافي.

## الخطوة 5: تكوين خيارات حفظ PDF

لتضمين الإشارات المرجعية في ملف PDF، قم بتكوين خيارات الحفظ:

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`:يحدد كيفية حفظ المستند بتنسيق PDF.
- `BookmarksOutlineLevels`:يحدد التسلسل الهرمي للإشارات المرجعية في ملف PDF.

## الخطوة 6: حفظ المستند

وأخيرًا، احفظ المستند بصيغة PDF:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
 ال`Save` تحفظ هذه الطريقة المستند بالتنسيق والموقع المحددين، مع الإشارات المرجعية.

## خاتمة

إن إنشاء إشارات مرجعية في مستند Word باستخدام Aspose.Words for .NET أمر بسيط ويعزز التنقل بين المستندات. سواء كنت تقوم بإنشاء تقارير أو كتب إلكترونية أو إدارة مستندات ضخمة، فإن الإشارات المرجعية لا تقدر بثمن. اتبع هذا البرنامج التعليمي، وستحصل على ملف PDF منظم جيدًا ومُضاف إليه إشارات مرجعية في وقت قصير!

## الأسئلة الشائعة

### هل يمكنني إنشاء إشارات مرجعية متعددة على مستويات مختلفة؟
نعم! يمكنك إنشاء عدة إشارات مرجعية وتحديد التسلسل الهرمي لها عند الحفظ بتنسيق PDF.

### كيف أقوم بتحديث نص الإشارة المرجعية؟
 يستخدم`DocumentBuilder.MoveToBookmark`للانتقال إلى الإشارة المرجعية وتحديث النص.

### هل من الممكن حذف الإشارة المرجعية؟
 بالتأكيد! استخدم`Bookmarks.Remove` الطريقة عن طريق تحديد اسم الإشارة المرجعية.

### هل يمكنني إنشاء إشارات مرجعية بتنسيقات أخرى غير PDF؟
نعم، يدعم Aspose.Words الإشارات المرجعية بتنسيقات مثل DOCX وHTML وEPUB.

### كيف يمكنني التأكد من ظهور الإشارات المرجعية بشكل صحيح في ملف PDF؟
 يُعرِّف`BookmarksOutlineLevels` بشكل صحيح في`PdfSaveOptions` للتأكد من تضمين الإشارات المرجعية في مخطط PDF.