---
title: إضافة طبقة إلى قاعدة بيانات جغرافية للملفات باستخدام Aspose.GIS لـ .NET
linktitle: إضافة طبقة إلى قاعدة بيانات جغرافية للملفات
second_title: واجهة برمجة تطبيقات Aspose.GIS .NET
description: تعرف على كيفية إضافة طبقة جديدة إلى قاعدة بيانات جغرافية للملفات (GDB) باستخدام Aspose.GIS for .NET. يغطي هذا الدليل الشامل المتطلبات الأساسية، واستيرادات المساحة، والخطوات التفصيلية لإنشاء الطبقات والتحقق منها في مجموعات بيانات GIS الخاصة بك.
type: docs
weight: 16
url: /ar/net/tutorials/gis/mastering-layer-management/add-layer-to-file-geo-database/
---
## مقدمة

تلعب تقنية نظام المعلومات الجغرافية (GIS) دورًا محوريًا في تحليل البيانات وتصورها في العصر الحديث. Aspose.GIS for .NET هي مكتبة استثنائية تمكن المطورين من التعامل مع البيانات الجغرافية بكفاءة. يستكشف هذا الدليل التفصيلي كيفية إضافة طبقة جديدة إلى مجموعة بيانات قاعدة بيانات الملفات الجغرافية (GDB) باستخدام Aspose.GIS for .NET. اتبع هذه الخطوات الشاملة لدمج الطبقات بسلاسة وتعزيز قدرات نظام المعلومات الجغرافية لديك.

## المتطلبات الأساسية لإضافة طبقات إلى ملف GDB

قبل أن نستمر، تأكد من أن لديك ما يلي:

1. مكتبة Aspose.GIS لـ .NET  
    قم بتنزيل المكتبة وتثبيتها من[صفحة Aspose.GIS لـ .NET](https://reference.aspose.com/gis/net/).

2. مجموعة بيانات قاعدة بيانات الملفات الجغرافية (GDB)  
   تأكد من أن لديك مجموعة بيانات GDB موجودة للعملية.

3. بيئة التطوير  
   قم بتثبيت وتكوين IDE المفضل لديك مع دعم .NET (على سبيل المثال، Visual Studio).

4. رخصة مؤقتة (اختياري)  
    للحصول على تقييم كامل للميزات، اطلب[رخصة مؤقتة](https://purchase.conholdate.com/temporary-license/).

5. دليل البيانات  
   قم بإعداد دليل لإدارة مجموعات البيانات المدخلة والمخرجة.

## استيراد المساحات المطلوبة

قبل الترميز، قم بتضمين مساحات الأسماء الأساسية للوصول إلى وظائف Aspose.GIS. أضف مقتطف التعليمات البرمجية التالي في بداية مشروعك:

```csharp
using Aspose.Gis;
using Aspose.Gis.Geometries;
using Aspose.Gis.SpatialReferencing;
using System;
```

## الخطوة 1: تكرار مجموعة بيانات GDB

للحفاظ على سلامة مجموعة البيانات الأصلية، أنشئ نسخة مكررة. استخدم الكود التالي لنسخ مجموعة البيانات إلى موقع جديد:

```csharp
string dataDir = "C:\\GISData\\"; // الدليل الذي يحتوي على مجموعات البيانات الخاصة بك
string originalPath = dataDir + "ExistingDataset.gdb";
string newDatasetPath = dataDir + "ModifiedDataset.gdb";

// وظيفة تكرار الدليل
RunExamples.CopyDirectory(originalPath, newDatasetPath);
```

## الخطوة 2: افتح مجموعة البيانات وتحقق من إمكانية الإنشاء

يتيح Aspose.GIS للمطورين فتح مجموعات البيانات والتحقق مما إذا كان من الممكن إضافة طبقات جديدة. استخدم المقطع التالي لتأكيد قدرات إنشاء مجموعة البيانات:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    Console.WriteLine($"Can Create Layers: {dataset.CanCreateLayers}"); // يجب أن يعود صحيحا
}
```

## الخطوة 3: إنشاء طبقة جديدة في مجموعة البيانات

تتطلب إضافة طبقة تحديد نظامها المرجعي المكاني وسماتها. فيما يلي كيفية إنشاء طبقة وملؤها ببيانات العينة:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    // إنشاء طبقة جديدة باستخدام نظام المرجع المكاني WGS 84
    using (var layer = dataset.CreateLayer("NewLayer", SpatialReferenceSystem.Wgs84))
    {
        // إضافة مخطط سمة
        layer.Attributes.Add(new FeatureAttribute("LocationName", AttributeDataType.String));

        // إنشاء ميزة وإضافتها
        var feature = layer.ConstructFeature();
        feature.SetValue("LocationName", "Sample Point");
        feature.Geometry = new Point(34.0522, -118.2437); // خط الطول ودائرة العرض
        layer.Add(feature);
    }
}
```

## الخطوة 4: افتح الطبقة الجديدة وتحقق من صحتها

بعد إنشاء طبقة، تحقق من صحة محتوياتها للتأكد من دقتها. استخدم مقتطف التعليمات البرمجية التالي:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    using (var layer = dataset.OpenLayer("NewLayer"))
    {
        Console.WriteLine($"Feature Count: {layer.Count}");
        Console.WriteLine($"Attribute Value: {layer[0].GetValue<string>("LocationName")}");
    }
}
```

## خاتمة

إن إضافة طبقة إلى مجموعة بيانات قاعدة بيانات ملف جغرافي باستخدام Aspose.GIS for .NET هي عملية بسيطة عند اتباع الخطوات التالية. من تكرار مجموعات البيانات إلى إنشاء طبقات والتحقق من صحتها، توفر المكتبة أدوات قوية لإدارة بيانات GIS. من خلال إتقان هذه التقنيات، يمكنك تحسين سير عمل GIS الخاص بك وتحقيق معالجة فعالة للبيانات الجغرافية.

## الأسئلة الشائعة

### ما هو استخدام Aspose.GIS for .NET؟
Aspose.GIS for .NET هي مكتبة مصممة لمعالجة البيانات الجغرافية ومعالجتها، وتدعم تنسيقات ملفات مختلفة، بما في ذلك Shapefiles، وGDB، والمزيد.

### هل يمكنني إضافة طبقات متعددة في عملية واحدة؟
نعم، يسمح Aspose.GIS بإنشاء وإدارة طبقات متعددة داخل مجموعة البيانات.

### ما هي أنظمة المرجع المكاني المدعومة؟
تدعم المكتبة العديد من أنظمة المرجع المكاني، بما في ذلك WGS 84، وNAD 83، وCRS المخصص.

### أين يمكنني العثور على الدعم؟
 قم بزيارة[منتدى Aspose.GIS](https://forum.aspose.com/c/gis/33) للمناقشات المجتمعية والدعم.

### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم، أ[نسخة تجريبية مجانية](https://releases.aspose.com/) متاح لاختبار ميزات المكتبة.