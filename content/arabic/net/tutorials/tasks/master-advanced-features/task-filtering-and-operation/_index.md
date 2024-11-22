---
title: تصفية المهام والعمليات في Aspose.Tasks
linktitle: تصفية المهام والعمليات في Aspose.Tasks
second_title: واجهة برمجة تطبيقات Aspose.Tasks .NET
description: تعرف على كيفية الاستفادة من الفئة الموجودة في Aspose.Tasks لـ .NET لتصفية مهام المشروع استنادًا إلى شروط متعددة. من خلال الجمع بين معايير مثل مهام الملخص والسمات غير الصفرية.
type: docs
weight: 10
url: /ar/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## مقدمة

في هذا البرنامج التعليمي، سوف نستكشف كيفية إجراء تصفية متقدمة لمهام المشروع في Aspose.Tasks لـ .NET من خلال الاستفادة من`Util.And` تتيح هذه الميزة القوية للمطورين تصفية المهام استنادًا إلى معايير متعددة بكفاءة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. المعرفة الأساسية لبرمجة C#.
2.  تم تثبيت Aspose.Tasks لـ .NET. إذا لم تقم بذلك بعد، فيمكنك تنزيله من[هذا الرابط](https://releases.aspose.com/tasks/net/).
3. بيئة تطوير متكاملة (IDE) مثل Visual Studio لكتابة وتشغيل التعليمات البرمجية.

## استيراد المساحات الاسمية

للبدء، تحتاج إلى استيراد مساحات الأسماء المطلوبة إلى مشروع C# الخاص بك. سيتيح لك هذا الوصول إلى الوظائف التي يوفرها Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## الخطوة 1: تهيئة المشروع وجمع المهام

 أولاً، قم بتشغيل مشروع Aspose.Tasks وجمع كل المهام داخله. لأغراض العرض التوضيحي، سنفترض وجود ملف مشروع باسم`Project2.mpp`.

```csharp
// المسار إلى دليل المستندات
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// جمع كل مهام الطفل
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## الخطوة 2: تحديد شروط التصفية

في هذه الخطوة، سنحدد شروط تصفية المهام. في مثالنا، سننشئ شرطين: أحدهما لتصفية المهام الموجزة والآخر للتأكد من أن المهام ليست فارغة.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## الخطوة 3: دمج الشروط باستخدام عملية AND

 الخطوة التالية هي الجمع بين هذه الشروط باستخدام`Util.And` يسمح لنا هذا بإنشاء شرط مركب يفرض كلا المعيارين.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## الخطوة 4: تطبيق مهام الشرط والتصفية المجمعة

الآن، دعنا نطبق الشرط المدمج على المهام المجمعة لتصفية المهام المحددة التي تلبي كلا الشرطين.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## الخطوة 5: إخراج المهام المفلترة

أخيرًا، سنعمل على تكرار المهام التي قمنا بتصفية نتائجها وإخراج التفاصيل ذات الصلة. وسيساعدنا هذا في فهم المهام التي تلبي معاييرنا.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## خاتمة

 في هذا البرنامج التعليمي، أوضحنا كيفية إجراء عمليات تصفية متقدمة في Aspose.Tasks لـ .NET باستخدام`Util.And`من خلال الجمع بين عدة شروط، يمكننا تصفية المهام بفعالية، وبالتالي تعزيز فائدة تطبيقات إدارة المشاريع الخاصة بنا.

## الأسئلة الشائعة

### ما هو Aspose.Tasks لـ .NET؟

Aspose.Tasks for .NET عبارة عن واجهة برمجة تطبيقات شاملة مصممة للمطورين للتعامل مع ملفات Microsoft Project برمجيًا داخل تطبيقات .NET.

### هل يمكنني دمج أكثر من شرطين باستخدام Util.And؟

 نعم!`Util.And` تتيح لك الفئة دمج شروط متعددة، مما يتيح منطق تصفية معقدًا مصممًا خصيصًا لتلبية احتياجاتك.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Tasks؟

 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هذا الرابط](https://releases.aspose.com/).

### أين يمكنني العثور على وثائق مفصلة لـ Aspose.Tasks؟

 الوثائق التفصيلية متاحة[هنا](https://reference.aspose.com/tasks/net/).

### كيف يمكنني الحصول على الدعم لـ Aspose.Tasks؟

 يتوفر الدعم من خلال منتدى مجتمع Aspose.Tasks، والذي يمكن الوصول إليه[هنا](https://forum.aspose.com/c/tasks/15).