---
title: إنشاء إشارة مرجعية لملف PDF لورقة الرسم البياني في Aspose.Cells
linktitle: إنشاء إشارة مرجعية لملف PDF لورقة الرسم البياني في Aspose.Cells
second_title: واجهة برمجة تطبيقات معالجة Excel الخاصة بـ Aspose.Cells .NET
description: تعرف على كيفية تحسين مستندات Excel الخاصة بك من خلال إنشاء إشارات مرجعية تفاعلية بتنسيق PDF لجداول البيانات باستخدام Aspose.Cells for .NET. يوفر هذا البرنامج التعليمي خطوة بخطوة إرشادات واضحة للمطورين من جميع مستويات المهارة.
type: docs
weight: 13
url: /ar/net/tutorials/cells/mastering-rendering-and-exporting/creating-pdf-bookmark-for-chart-sheet/
---
## مقدمة

Aspose.Cells for .NET هي مكتبة قوية تتيح للمطورين التعامل مع ملفات Excel برمجيًا. ومن بين ميزاتها البارزة القدرة على إنشاء إشارات مرجعية بتنسيق PDF لأوراق المخططات الفردية، مما يعزز التنقل بين المستندات وسهولة استخدامها. سيرشدك هذا البرنامج التعليمي خطوة بخطوة خلال العملية، مما يجعلها في متناول الجميع بغض النظر عن خبرتك في البرمجة. احصل على محرر التعليمات البرمجية الخاص بك، ولنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Cells لـ .NET: قم بتنزيل المكتبة من[هنا](https://releases.aspose.com/cells/net/).
2. Visual Studio أو أي .NET IDE: ستحتاج إلى بيئة تطوير لكتابة وتنفيذ كود C# الخاص بك.
3. الفهم الأساسي للغة C#: سيكون التعرف على أساسيات لغة C# مفيدًا أثناء تعاملنا مع الكود.
4. ملف Excel نموذجي: احصل على ملف Excel نموذجي يتضمن مخططات جاهزة لهذا التمرين.

بمجرد توفر هذه المتطلبات الأساسية لديك، ستكون جاهزًا لإنشاء إشارات مرجعية بتنسيق PDF لأوراق المخططات!

## الخطوة 1: إنشاء مشروع جديد
1. افتح Visual Studio وقم بإنشاء تطبيق وحدة تحكم C# جديد. قم بتسميته AsposePDFBookmarkExample.
   
## الخطوة 2: إضافة مرجع Aspose.Cells
1. انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول.
2. حدد إدارة حزم NuGet.
3. ابحث عن Aspose.Cells وقم بتثبيت الإصدار الأحدث.

## الخطوة 3: تضمين توجيهات الاستخدام الضرورية
 فيك`Program.cs` الملف، أضف الأسطر التالية في الأعلى لاستيراد المساحات المطلوبة:

```csharp
using System;
using System.Collections;
using System.Linq;
using System.Text;
using Aspose.Cells;
using Aspose.Cells.Rendering;
```

ستتيح لك هذه المساحات الاسمية العمل مع ملفات Excel وتحويلها إلى ملفات PDF مع الإشارات المرجعية.

## الخطوة 4: تحديد مسارات الدليل الخاص بك
قم بتنظيم الكود الخاص بك عن طريق تحديد المسارات للملفات الخاصة بك:
```csharp
string sourceDir = "Your Document Directory"; // قم بالتعديل على دليل المصدر الخاص بك
string outputDir = "Your Document Directory"; // قم بالتعديل على دليل الإخراج الخاص بك
```

## الخطوة 5: تحميل مصنف Excel
قم بتحميل مصنف Excel الذي تريد معالجته:
```csharp
Workbook wb = new Workbook(sourceDir + "sampleCreatePdfBookmarkEntryForChartSheet.xlsx");
```
تأكد من أن اسم الملف يتطابق مع ملفك الفعلي.

## الخطوة 6: الوصول إلى أوراق العمل
الوصول إلى أوراق العمل داخل المصنف:
```csharp
Worksheet sheet1 = wb.Worksheets[0];
Worksheet sheet2 = wb.Worksheets[1];
Worksheet sheet3 = wb.Worksheets[2];
Worksheet sheet4 = wb.Worksheets[3];
```
تأكد من أن ملف Excel الخاص بك يحتوي على أربع أوراق على الأقل.

## الخطوة 7: إنشاء إدخالات إشارة مرجعية لملف PDF
الآن، قم بإنشاء إدخالات الإشارة المرجعية لكل ورقة:
```csharp
PdfBookmarkEntry ent1 = new PdfBookmarkEntry {
    Destination = sheet1.Cells["A1"],
    Text = "Bookmark-I"
};
PdfBookmarkEntry ent2 = new PdfBookmarkEntry {
    Destination = sheet2.Cells["A1"],
    Text = "Bookmark-II-Chart1"
};
PdfBookmarkEntry ent3 = new PdfBookmarkEntry {
    Destination = sheet3.Cells["A1"],
    Text = "Bookmark-III"
};
PdfBookmarkEntry ent4 = new PdfBookmarkEntry {
    Destination = sheet4.Cells["A1"],
    Text = "Bookmark-IV-Chart2"
};
```
 كل`PdfBookmarkEntry` يحدد الكائن خلية الوجهة وعلامة النص للإشارة المرجعية.

## الخطوة 8: ترتيب إدخالات الإشارة المرجعية
لإنشاء هيكل هرمي للإشارات المرجعية، قم بتنظيمها على النحو التالي:
```csharp
ArrayList lst = new ArrayList();
ent1.SubEntry = lst;
lst.Add(ent2);
lst.Add(ent3);
lst.Add(ent4);
```
يتيح هذا الهيكل إنشاء إشارة مرجعية رئيسية مع إشارات مرجعية فرعية، مما يعزز التنقل في ملف PDF.

## الخطوة 9: إنشاء خيارات حفظ PDF باستخدام إدخالات الإشارة المرجعية
قم بإعداد خيارات حفظ PDF لتشمل الإشارات المرجعية:
```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = ent1;
```

## الخطوة 10: احفظ ملف PDF الناتج
وأخيرًا، احفظ المصنف الخاص بك بصيغة PDF:
```csharp
wb.Save(outputDir + "outputCreatePdfBookmarkEntryForChartSheet.pdf", opts);
```
يقوم هذا الأمر بحفظ المصنف في ملف PDF في مسار الإخراج المحدد، مع الإشارات المرجعية.

## الخطوة 11: تأكيد التنفيذ
اطبع رسالة نجاح لتأكيد التنفيذ:
```csharp
Console.WriteLine("CreatePdfBookmarkEntryForChartSheet executed successfully.");
```

## خاتمة
إن إنشاء إشارات مرجعية بتنسيق PDF لجداول البيانات باستخدام Aspose.Cells for .NET هي عملية بسيطة تعمل على تحسين قابلية استخدام مستندات Excel بشكل كبير. فباستخدام بضعة أسطر فقط من التعليمات البرمجية، يمكنك تحسين التنقل داخل ملفات PDF، مما يوفر الوقت ويبسط سير العمل.

## الأسئلة الشائعة

### ما هو Aspose.Cells؟
Aspose.Cells عبارة عن مكتبة .NET قوية مصممة للتعامل مع عمليات معالجة ملفات Excel، بما في ذلك القراءة والكتابة وتحويل جداول البيانات.

### هل يمكنني إنشاء إشارات مرجعية لخلايا محددة فقط؟
نعم، يمكن تعيين الإشارات المرجعية للإشارة إلى أي خلية في ورقة العمل الخاصة بك.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Cells؟
على الرغم من أن Aspose.Cells يقدم نسخة تجريبية مجانية، إلا أنه يلزم الحصول على ترخيص مدفوع للحصول على الوظائف الكاملة في بيئات الإنتاج.

### هل يمكنني إنشاء إشارات مرجعية لأكثر من أربع أوراق؟
بالتأكيد! يمكنك إنشاء إشارات مرجعية لأي عدد من الأوراق حسب الحاجة من خلال اتباع بنية مماثلة في الكود.

### أين يمكنني العثور على المزيد من المساعدة؟
 للحصول على دعم إضافي، راجع[منتدى دعم مجتمع Aspose](https://forum.aspose.com/c/cells/9) لأي مشاكل أو استفسارات.