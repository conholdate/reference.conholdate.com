---
title: إضافة جدول المحتويات إلى مستند PDF
linktitle: إضافة جدول المحتويات إلى مستند PDF
second_title: مرجع واجهة برمجة التطبيقات Aspose.PDF لـ .NET
description: يوضح هذا البرنامج التعليمي كيفية إضافة جدول محتويات (TOC) إلى مستند PDF باستخدام Aspose.Pdf لـ .NET.
type: docs
weight: 40
url: /ar/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## مقدمة

إن إنشاء جدول محتويات (TOC) في مستند PDF يمكن أن يعزز بشكل كبير من إمكانية التنقل فيه وإمكانية الوصول إليه. في هذا الدليل، سنوضح كيفية إضافة جدول محتويات (TOC) إلى ملف PDF باستخدام Aspose.Pdf لـ .NET.

## المتطلبات الأساسية

قبل البدء، تأكد من توفر ما يلي:

1.   Aspose.PDF لـ .NET: قم بتنزيل أحدث إصدار وتثبيته من[هنا](https://releases.aspose.com/pdf/net/).
2.  بيئة التطوير: قم بإعداد بيئة تطوير .NET مثل Visual Studio.
3.   الترخيص: اطلب ترخيصًا مؤقتًا إذا لزم الأمر؛ يرجى زيارة[صفحة ترخيص Aspose.Pdf](https://asposepdf.com/developers) لمزيد من المعلومات.

استيراد المكتبات الضرورية

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## الخطوة 1: تحميل مستند PDF

قم بتحميل ملف PDF الحالي حيث تريد إضافة جدول المحتويات. حدد المسار إلى دليل المستند الخاص بك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## الخطوة 2: إدراج صفحة جديدة لجدول المحتويات

قم بإدراج صفحة جديدة في بداية مستند PDF. ستكون هذه الصفحة بمثابة جدول المحتويات (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## الخطوة 3: إنشاء كائن معلومات جدول المحتويات

أنشئ كائنًا يمثل معلومات جدول المحتويات. أضف عنوانًا ورابطًا إليه لتسهيل التنقل.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## الخطوة 4: تحديد عناصر جدول المحتويات

قم بتحديد العناصر (أو العناوين) التي سيتم عرضها في جدول المحتويات. يمكن أن تساعد هذه العناصر القراء في التنقل إلى أقسام معينة من المستند.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## الخطوة 5: إنشاء عناوين جدول المحتويات

أنشئ عناوين للعنصرين الأولين في جدول المحتويات. ستؤدي هذه العناوين إلى ربط الصفحات الخاصة بها.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## الخطوة 6: احفظ ملف PDF مع جدول المحتويات

وأخيرًا، قم بحفظ ملف PDF المحدّث.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## رسالة التأكيد

عرض رسالة تأكيد لإعلام المستخدم بأن العملية قد اكتملت.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## خاتمة

مع Aspose.PDF for .NET، لا يصبح إضافة جدول محتويات إلى ملف PDF أمرًا سهلاً فحسب، بل إنه قابل للتخصيص أيضًا. سواء كنت بحاجة إلى إنشاء روابط تنقل بسيطة أو هياكل معقدة، فإن هذه الأداة ستلبي احتياجاتك. لذا، في المرة القادمة التي تعمل فيها على ملف PDF طويل، لا تنس إضافة جدول محتويات لإضفاء لمسة احترافية.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر جدول المحتويات في Aspose.PDF؟

نعم، يمكنك تخصيص مظهر جدول المحتويات بالكامل، بما في ذلك نمط الخط وحجمه ومحاذاته.

### كيف أضيف عناوين فرعية إلى جدول المحتويات؟

يمكنك إضافة عناوين فرعية عن طريق تعديل`Heading` المستوى (على سبيل المثال،`Heading(2)`).

### هل من الممكن تحديث جدول المحتويات تلقائيًا إذا تغيرت الوثيقة؟

لا، لن يتم تحديث جدول المحتويات تلقائيًا. ستحتاج إلى إعادة إنشائه إذا تغير هيكل المستند.

### هل يمكنني ربط إدخالات جدول المحتويات بمستندات خارجية؟

نعم، يمكنك استخدام الارتباطات التشعبية لربط إدخالات جدول المحتويات بملفات PDF أو عناوين URL الخارجية.

### هل يدعم Aspose.PDF جداول المحتويات متعددة المستويات؟

نعم، يدعم Aspose.PDF جداول المحتويات متعددة المستويات للمستندات المعقدة التي تحتوي على أقسام فرعية.
