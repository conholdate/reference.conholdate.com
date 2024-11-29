---
title: دليل التوقيع على الصور باستخدام البيانات الوصفية باستخدام GroupDocs.Signature
linktitle: دليل التوقيع على الصور باستخدام البيانات الوصفية
second_title: GroupDocs.Signature .NET API
description: تعرف على كيفية التوقيع على الصور بكفاءة باستخدام البيانات الوصفية في تطبيقات .NET الخاصة بك باستخدام GroupDocs.Signature. يغطي هذا البرنامج التعليمي خطوة بخطوة كل شيء من التثبيت إلى التنفيذ، مما يتيح لك تحسين مستنداتك باستخدام توقيعات البيانات الوصفية دون عناء.
type: docs
weight: 10
url: /ar/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## مقدمة

GroupDocs.Signature for .NET هي مكتبة قوية تتيح للمطورين التوقيع على الصور بكفاءة باستخدام البيانات الوصفية. سيرشدك هذا البرنامج التعليمي خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

1.  GroupDocs.Signature لـ .NET: قم بتثبيت حزمة GroupDocs.Signature في مشروع .NET الخاص بك. يمكنك تنزيلها من[هنا](https://releases.groupdocs.com/signature/net/).
2. ملف الصورة: قم بإعداد ملف الصورة الذي تريد توقيعه باستخدام البيانات الوصفية.

## استيراد المساحات الاسمية الضرورية

في الكود C# الخاص بك، قم باستيراد المساحات التالية:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## الخطوة 1: قم بتحميل ملف صورتك

ابدأ بتحديد المسار إلى ملف صورتك ودليل الإخراج للصورة الموقعة:

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## الخطوة 2: إنشاء توقيعات البيانات الوصفية

بعد ذلك، قم بإنشاء توقيعات البيانات الوصفية وأضفها إلى خيارات التوقيع:

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; // معرف البدء للبيانات الوصفية
    MetadataSignOptions options = new MetadataSignOptions();

    //إضافة أنواع مختلفة من توقيعات البيانات الوصفية
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) // قيمة السلسلة
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          // قيمة التاريخ والوقت
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                // قيمة صحيحة
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              // قيمة مزدوجة
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              // القيمة العشرية
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             // قيمة التعويم

    // توقيع الوثيقة وحفظ النتيجة
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## خاتمة

في هذا البرنامج التعليمي، تعلمت كيفية توقيع صورة باستخدام بيانات وصفية باستخدام GroupDocs.Signature لـ .NET. باتباع هذه الخطوات، يمكنك بسهولة إضافة توقيعات بيانات وصفية إلى تطبيقات .NET الخاصة بك، مما يعزز وظائف وسلامة صورك.

## الأسئلة الشائعة

### هل يمكنني توقيع صور متعددة باستخدام البيانات الوصفية باستخدام GroupDocs.Signature لـ .NET؟
نعم، يمكنك توقيع صور متعددة عن طريق التكرار عبر كل ملف صورة وتطبيق توقيعات البيانات الوصفية.

### هل هناك نسخة تجريبية متاحة لـ GroupDocs.Signature لـ .NET؟
 نعم يمكنك تنزيل النسخة التجريبية من[هنا](https://releases.groupdocs.com/).

### هل يدعم GroupDocs.Signature لـ .NET تنسيقات ملفات أخرى بالإضافة إلى الصور؟
بالتأكيد! يدعم GroupDocs.Signature تنسيقات مختلفة، بما في ذلك PDF وWord وExcel والمزيد.

### هل يمكنني تخصيص مظهر توقيع البيانات الوصفية؟
نعم، يمكنك تخصيص جوانب مثل حجم الخط، واللون، وموضع توقيع البيانات الوصفية.

### أين يمكنني الحصول على الدعم لـ GroupDocs.Signature لـ .NET؟
 للحصول على الدعم، قم بزيارة منتدى GroupDocs.Signature[هنا](https://forum.groupdocs.com/c/signature/13).