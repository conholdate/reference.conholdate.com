---
title: إضافة توقيعات نصية إلى المستندات باستخدام GroupDocs.Signature
linktitle: إضافة توقيعات نصية إلى المستندات
second_title: GroupDocs.Signature .NET API
description: تعرف على كيفية توقيع المستندات باستخدام النص باستخدام GroupDocs.Signature لـ .NET. دليل خطوة بخطوة لإضافة توقيعات نصية برمجيًا.
type: docs
weight: 17
url: /ar/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## مقدمة

في المشهد الرقمي الحالي، أصبح التوقيع الإلكتروني على المستندات أمرًا ضروريًا لتبسيط سير العمل وتوفير الموارد. يوفر GroupDocs.Signature for .NET حلاً قويًا لإضافة توقيعات نصية برمجيًا إلى تنسيقات المستندات المختلفة. سيرشدك هذا البرنامج التعليمي خلال الخطوات اللازمة لتوقيع مستند بنص باستخدام GroupDocs.Signature for .NET.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. GroupDocs.Signature لـ .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/signature/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير .NET الخاصة بك.
3. المستند: قم بإعداد المستند الذي تريد توقيعه (على سبيل المثال، PDF، Word).

## استيراد المساحات الأساسية الضرورية

ابدأ باستيراد المساحات المطلوبة إلى مشروع .NET الخاص بك:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## الخطوة 1: تحميل المستند

ابدأ بتحميل المستند الذي تنوي التوقيع عليه:

```csharp
string filePath = "sample.pdf"; // المسار إلى مستندك
string fileName = Path.GetFileName(filePath);
```

## الخطوة 2: تحديد مسار ملف الإخراج

بعد ذلك، قم بتعيين مسار ملف الإخراج الذي سيتم حفظ المستند الموقع فيه:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## الخطوة 3: إنشاء خيارات التوقيع

قم بتكوين الخيارات الخاصة بتوقيع النص الخاص بك، بما في ذلك المحتوى والموضع والحجم واللون ونمط الخط:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // موضع X
    Top = 200, // موضع Y
    Width = 100, // عرض التوقيع
    Height = 30, // ارتفاع التوقيع
    ForeColor = Color.Red, // لون النص
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // إعدادات الخط
};
```

## الخطوة 4: توقيع الوثيقة

أخيرًا، استخدم GroupDocs.Signature لتطبيق توقيع النص وحفظ المستند الموقّع:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // توقيع الوثيقة
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## خاتمة

في هذا البرنامج التعليمي، أوضحنا كيفية إضافة توقيع نصي برمجيًا إلى مستند باستخدام GroupDocs.Signature لـ .NET. باتباع هذه الخطوات، يمكنك تحسين أمان مستنداتك ومصداقيتها بكفاءة.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر توقيع النص؟
نعم، يمكنك تخصيص العديد من السمات مثل اللون والخط والحجم وموضع توقيع النص لتناسب احتياجاتك.

### هل GroupDocs.Signature متوافق مع تنسيقات المستندات المتعددة؟
بالتأكيد! يدعم GroupDocs.Signature مجموعة واسعة من التنسيقات، بما في ذلك PDF وWord وExcel وPowerPoint والمزيد.

### هل يمكنني إضافة توقيعات نصية متعددة إلى مستند واحد؟
نعم، يمكنك إضافة توقيعات نصية متعددة، ولكل منها خيارات التخصيص الخاصة بها.

### هل يضمن GroupDocs.Signature سلامة المستند بعد التوقيع؟
نعم، تستخدم المكتبة خوارزميات تشفير قوية لضمان سلامة المستندات ومنع العبث بها بعد التوقيع.

### هل هناك نسخة تجريبية متاحة للاختبار قبل الشراء؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/) لاستكشاف الميزات قبل إجراء عملية شراء.