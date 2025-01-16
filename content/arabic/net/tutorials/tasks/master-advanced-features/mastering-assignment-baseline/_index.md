---
title: إتقان خطوط الأساس للمهام باستخدام Aspose.Tasks لـ .NET
linktitle: إدارة خط الأساس للمهمة في Aspose.Tasks
second_title: واجهة برمجة تطبيقات Aspose.Tasks .NET
description: تعرف على كيفية إدارة خطوط الأساس للمهمة بكفاءة باستخدام Aspose.Tasks لـ .NET. يغطي هذا الدليل خطوة بخطوة تحميل المشروعات وتعيين خطوط الأساس واسترداد البيانات ومقارنة خطوط الأساس والمزيد لتحسين سير عمل إدارة المشروع.
type: docs
weight: 14
url: /ar/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## مقدمة

تعتمد إدارة المشروعات الفعّالة على تتبع وإدارة خطوط الأساس للمهمة بدقة. باستخدام Aspose.Tasks for .NET، يمكنك الحصول على مجموعة أدوات قوية لتبسيط التعامل مع خطوط الأساس للمهمة للحصول على رؤى أفضل للمشروع. في هذه المقالة، نرشدك خلال عملية إدارة خطوط الأساس للمهمة، لضمان بقاء مشاريعك على المسار الصحيح.

## المتطلبات الأساسية

قبل البدء في التنفيذ، تأكد من توفر ما يلي:

- الخبرة البرمجية: معرفة أساسية بلغة C#.
- بيئة التطوير: تم تثبيت Visual Studio وتكوينه.
-  مكتبة Aspose.Tasks لـ .NET: قم بتنزيلها من[إصدارات Aspose.Tasks](https://releases.aspose.com/tasks/net/).
- ملف المشروع: الوصول إلى ملف المشروع بتنسيق MPP.

## استيراد المساحات المطلوبة

لاستخدام وظيفة Aspose.Tasks، قم بتضمين المساحات التالية في ملف المشروع الخاص بك:

```csharp
using Aspose.Tasks;
using System;
```

## الخطوة 1: تحميل المشروع وتعيين الخطوط الأساسية

يعد تحميل مشروع وتعيين خط الأساس أمرًا أساسيًا لإدارة خطوط الأساس للمهمة. يوضح الكود التالي كيفية تحميل مشروع وتعيين خط الأساس الخاص به.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// تحديد خط الأساس للمشروع
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## الخطوة 2: استرداد بيانات الأساس للمهمة

يمكنك استخراج معلومات أساسية مفصلة لكل مهمة مورد. وإليك كيفية القيام بذلك:

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## الخطوة 3: مقارنة الخطوط الأساسية بين المهام

يتيح لك Aspose.Tasks مقارنة الخطوط الأساسية برمجيًا لتقييم الاختلافات بين تعيينات الموارد.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## الخطوة 4: تعديل تفاصيل خط الأساس برمجيًا

يمكنك تعديل البيانات الأساسية برمجيًا لتلبية احتياجات المشروع المتطورة:

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // تعديل التكلفة الأساسية
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // إضافة ساعات العمل

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## خاتمة

إن إدارة خطوط الأساس للمهمة بشكل فعال أمر لا يتجزأ من الحفاظ على التحكم في جداول المشروعات والميزانيات. يزودك Aspose.Tasks for .NET بالأدوات اللازمة للتعامل مع خطوط الأساس بدقة، مما يتيح اتخاذ القرارات القائمة على البيانات.

## الأسئلة الشائعة

### هل يمكن لـ Aspose.Tasks التعامل مع خطوط أساسية متعددة لمشروع واحد؟  
نعم، يدعم Aspose.Tasks خطوط أساسية متعددة، مما يوفر المرونة في تتبع إصدارات المشروع المختلفة.

### هل Aspose.Tasks متوافق مع ملفات المشاريع غير MPP؟  
بالتأكيد. يدعم Aspose.Tasks تنسيقات مثل XML وMPX والمزيد.

### هل يمكنني أتمتة التحديثات الأساسية؟  
نعم، تسمح واجهة برمجة التطبيقات بإجراء تعديلات أساسية ديناميكية وتلقائية برمجيًا.

### هل يوفر Aspose.Tasks بيانات أساسية مقسمة إلى مراحل زمنية؟  
نعم، من الممكن استرجاع البيانات الأساسية التفصيلية المقسمة حسب المرحلة الزمنية وتحليلها.

### أين يمكنني الوصول إلى الدعم والوثائق؟  
 يزور[توثيق Aspose.Tasks](https://reference.aspose.com/words/net/)أو انضم إلى[منتدى دعم Aspose](https://forum.aspose.com/c/words/8) للحصول على المساعدة. 