---
title: دليل التوقيع على ملفات PDF باستخدام البيانات الوصفية باستخدام GroupDocs.Signature
linktitle: دليل التوقيع على ملفات PDF باستخدام البيانات الوصفية
second_title: GroupDocs.Signature .NET API
description: تعرف على كيفية تعزيز مستندات PDF الخاصة بك من خلال تعزيز الأمان وإمكانية التتبع من خلال توقيعها باستخدام البيانات الوصفية باستخدام GroupDocs.Signature for .NET. يوفر هذا البرنامج التعليمي الشامل شرحًا واضحًا.
type: docs
weight: 11
url: /ar/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## مقدمة

في هذا البرنامج التعليمي، سنتعلم كيفية توقيع مستند PDF وإضافة بيانات وصفية باستخدام GroupDocs.Signature لـ .NET. تعمل إضافة البيانات الوصفية على تحسين المستند من خلال توفير معلومات أساسية مثل المؤلف وتاريخ الإنشاء ومعرف المستند والمزيد.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  GroupDocs.Signature لـ .NET: قم بتنزيله من[هنا](https://releases.groupdocs.com/signature/net/).
2. مستند PDF: احصل على ملف PDF نموذجي جاهز للتوقيع.
3. المعرفة الأساسية لبرمجة C#: المعرفة بقواعد لغة C# ضرورية لفهم أمثلة التعليمات البرمجية.

## استيراد مساحات الأسماء

ابدأ باستيراد المساحات المطلوبة للوصول إلى الفئات والطرق الضرورية:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## الخطوة 1: تحميل مستند PDF

حدد مسار مستند PDF الذي تريد توقيعه:

```csharp
string filePath = "sample.pdf";
```

## الخطوة 2: تحديد مسار ملف الإخراج

قم بتحديد المكان الذي سيتم فيه حفظ ملف PDF الموقع مع البيانات الوصفية:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## الخطوة 3: إنشاء مثيل توقيع

 تهيئة`Signature` مثال مع المسار إلى مستند PDF:

```csharp
using (Signature signature = new Signature(filePath))
{
    // سيتم وضع الكود المتعلق بالتوقيع هنا
}
```

## الخطوة 4: تحديد خيارات البيانات الوصفية

 يخلق`MetadataSignOptions` وأضف حقول البيانات الوصفية مع قيمها:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // قيمة السلسلة
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // قيمة التاريخ والوقت
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // قيمة صحيحة
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // قيمة مزدوجة
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // القيمة العشرية
    .Add(new PdfMetadataSignature("Total", 123.456F));              // قيمة التعويم
```

## الخطوة 5: توقيع الوثيقة

قم بتوقيع مستند PDF باستخدام خيارات البيانات الوصفية المحددة وحفظ المستند الموقع:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## خاتمة

في هذا البرنامج التعليمي، تناولنا كيفية توقيع مستند PDF باستخدام البيانات الوصفية باستخدام GroupDocs.Signature لـ .NET. باتباع هذه الخطوات، يمكنك بسهولة إثراء ملفات PDF الخاصة بك بالبيانات الوصفية القيمة، وتحسين إمكانية تتبعها وفائدتها.

## الأسئلة الشائعة

### هل يمكنني إضافة حقول بيانات وصفية مخصصة إلى مستندات PDF الخاصة بي؟

نعم، يمكنك إضافة حقول بيانات تعريفية مخصصة عن طريق تحديد اسم الحقل والقيمة المقابلة له باستخدام GroupDocs.Signature لـ .NET.

### هل GroupDocs.Signature لـ .NET متوافق مع كافة إصدارات .NET Framework؟

يعد GroupDocs.Signature لـ .NET متوافقًا مع الإصدارات المختلفة من .NET Framework، مما يضمن المرونة وسهولة التكامل.

### هل يدعم GroupDocs.Signature التوقيع على تنسيقات مستندات أخرى غير PDF؟

نعم، يدعم GroupDocs.Signature مجموعة واسعة من تنسيقات المستندات، بما في ذلك Word وExcel وPowerPoint والمزيد.

### هل يمكنني التوقيع على مستندات متعددة دفعة واحدة باستخدام GroupDocs.Signature لـ .NET؟

بالتأكيد! يمكنك التوقيع على مستندات متعددة دفعة واحدة من خلال تكرار قائمة من الملفات وتطبيق عملية التوقيع برمجيًا.

### هل يتوفر الدعم الفني لمستخدمي GroupDocs.Signature؟

نعم، توفر GroupDocs دعمًا فنيًا مخصصًا من خلال منتدياتها. يمكنك الوصول إلى منتدى الدعم[هنا](https://forum.groupdocs.com/c/signature/13).