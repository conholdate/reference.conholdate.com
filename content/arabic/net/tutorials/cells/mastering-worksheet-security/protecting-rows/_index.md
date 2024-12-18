---
title: حماية الصفوف في ورقة العمل باستخدام Aspose.Cells
linktitle: حماية الصفوف في ورقة العمل باستخدام Aspose.Cells
second_title: واجهة برمجة تطبيقات معالجة Excel الخاصة بـ Aspose.Cells .NET
description: تعرف على كيفية تأمين المعلومات الحساسة في أوراق عمل Excel الخاصة بك عن طريق حماية صفوف معينة باستخدام Aspose.Cells for .NET. يغطي هذا البرنامج التعليمي الشامل كل شيء بدءًا من إعداد البيئة الخاصة بك.
type: docs
weight: 18
url: /ar/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## مقدمة

غالبًا ما يتطلب العمل مع ملفات Excel برمجيًا ليس فقط معالجة البيانات ولكن أيضًا حماية البيانات. يمكن أن تكون حماية صفوف معينة في ورقة عمل أمرًا بالغ الأهمية لحماية المعلومات الحساسة أو منع التحرير غير المقصود. في هذا البرنامج التعليمي، سنستكشف كيفية حماية الصفوف في ورقة عمل Excel باستخدام Aspose.Cells for .NET. سنرشدك خلال الخطوات اللازمة، من إعداد البيئة الخاصة بك إلى تنفيذ ميزات حماية الصفوف بطريقة مباشرة.

## المتطلبات الأساسية
قبل أن تبدأ، تأكد من توفر ما يلي:

1.  Aspose.Cells لـ .NET: قم بتنزيله وتثبيته من[صفحة تحميل Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio أو أي بيئة تطوير متكاملة متوافقة مع .NET: تحتاج إلى بيئة تطوير. يوصى باستخدام Visual Studio، ولكن أي بيئة تطوير متكاملة متوافقة مع .NET ستكون كافية.
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على المتابعة وتعديل كود المثال حسب الحاجة.
4.  توثيق واجهة برمجة تطبيقات Aspose.Cells: مراجعة[توثيق Aspose.Cells لـ .NET](https://reference.aspose.com/cells/net/) للحصول على نظرة عامة على بنية الفصل والأساليب.

بمجرد أن تكون المتطلبات الأساسية جاهزة، يمكننا المضي قدمًا في التنفيذ.

## استيراد الحزم الضرورية
ابدأ باستيراد الحزم المطلوبة في مشروع C# الخاص بك. هذه المكتبات ضرورية للتفاعل مع ملفات Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## الخطوة 1: إنشاء مصنف وورقة عمل جديدة
قبل تطبيق أي إعدادات حماية، قم بإنشاء مصنف جديد وحدد ورقة العمل التي تريد العمل عليها.

```csharp
// قم بتحديد المسار إلى دليل المستندات.
string dataDir = "Your Document Directory";
// إنشاء الدليل إذا لم يكن موجودًا.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// قم بإنشاء مصنف جديد وحدد ورقة العمل الأولى.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## الخطوة 2: تحديد كائنات Style وStyleFlag
قم بتحديد كائنات النمط وعلم النمط، والتي ستسمح لك بتعديل خصائص الخلية، مثل قفلها أو إلغاء قفلها.

```csharp
// قم بتعريف النمط وكائنات علم النمط.
Style style;
StyleFlag flag;
```

## الخطوة 3: إلغاء قفل جميع الأعمدة في ورقة العمل
بشكل افتراضي، يتم تأمين جميع الخلايا في ورقة عمل Excel. لحماية صفوف محددة فقط، قم بإلغاء تأمين جميع الأعمدة أولاً.

```csharp
// قم بالمرور على جميع الأعمدة وإلغاء قفلها.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## الخطوة 4: قفل صفوف محددة
الآن، قم بقفل الصفوف التي تريد حمايتها. في هذا المثال، سنقوم بقفل الصف الأول.

```csharp
// قفل الصف الأول.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

يمكنك تكرار هذه الخطوة لأي صفوف إضافية ترغب في قفلها.

## الخطوة 5: حماية الورقة
بعد تأمين الصفوف اللازمة، حان الوقت لحماية ورقة العمل. سيمنع هذا إجراء أي تعديلات على الصفوف المقفلة ما لم تتم إزالة الحماية.

```csharp
// حماية الورقة.
sheet.Protect(ProtectionType.All);
```

## الخطوة 6: احفظ المصنف
أخيرًا، احفظ المصنف بالتغييرات المطبقة. يمكنك الاختيار من بين تنسيقات مختلفة، مثل Excel 97-2003 أو الإصدارات الأحدث.

```csharp
// احفظ ملف Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## خاتمة
تهانينا! لقد تعلمت بنجاح كيفية حماية الصفوف في ورقة عمل Excel باستخدام Aspose.Cells for .NET. باتباع الخطوات التالية، يمكنك إلغاء قفل الصفوف أو الأعمدة أو قفلها حسب الحاجة وتطبيق الحماية للحفاظ على سلامة بياناتك.

## الأسئلة الشائعة
### كيف يمكنني حماية صفوف متعددة في وقت واحد؟
يمكنك التنقل عبر مؤشرات الصفوف المتعددة وتطبيق نمط القفل على كل مؤشر على حدة.

### هل يمكنني تعيين كلمة مرور لحماية الورقة؟
 نعم، يمكنك تمرير كلمة المرور إلى`sheet.Protect()` طريقة لفرض حماية كلمة المرور.

### هل يمكنني فتح خلايا محددة بدلاً من الأعمدة بأكملها؟
نعم، يمكنك إلغاء قفل الخلايا الفردية عن طريق تعديل خصائص أسلوبها بدلاً من إلغاء قفل الأعمدة بأكملها.

### ماذا يحدث إذا حاولت تحرير صف محمي؟
عندما يكون الصف محميًا، سيمنع Excel إجراء أي تعديلات على الخلايا المقفلة ما لم تكن الورقة غير محمية.

### هل يمكنني حماية نطاقات محددة ضمن صف واحد؟
 نعم! يمكنك قفل النطاقات الفردية في صف واحد عن طريق ضبط`IsLocked` الممتلكات لخلايا محددة ضمن هذا النطاق.