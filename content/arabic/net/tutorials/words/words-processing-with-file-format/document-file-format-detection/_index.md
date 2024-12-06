---
title: اكتشاف تنسيق ملف المستند
linktitle: اكتشاف تنسيق ملف المستند
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية اكتشاف تنسيقات ملفات المستندات المختلفة وإدارتها بسلاسة باستخدام Aspose.Words for .NET. اتبع دليلنا المفصل الذي يتضمن أمثلة عملية ونصائح وأسئلة شائعة.
type: docs
weight: 10
url: /ar/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## مقدمة

إن إدارة وتنظيم تنسيقات المستندات المختلفة بكفاءة أمر بالغ الأهمية في المشهد الرقمي الحالي. يوفر Aspose.Words for .NET حلاً قويًا للكشف عن أنواع الملفات المختلفة ومعالجتها. في هذا الدليل، نتعمق في عملية الكشف عن تنسيقات المستندات خطوة بخطوة، وضمان الدقة وتوفير الوقت الثمين.

## المتطلبات الأساسية لكشف المستندات

قبل أن نبدأ، تأكد من استيفاء المتطلبات التالية:

1. Aspose.Words لمكتبة .NET  
    قم بتنزيل المكتبة من[إصدارات كلمات Aspose](https://releases.aspose.com/words/net/) وتفعيله باستخدام ترخيص صالح. للحصول على تراخيص مؤقتة، قم بزيارة[ترخيص Aspose المؤقت](https://purchase.aspose.com/temporary-license/).

2. بيئة التطوير  
   استخدم Visual Studio (أي إصدار حديث) مع تثبيت .NET Framework.

3. إعداد الملف الأساسي  
   قم بتنظيم ملفات الإدخال الخاصة بك وإعداد الدلائل لفرز التنسيقات المكتشفة.

## استيراد مساحات الأسماء الأساسية

قم بتضمين هذه المساحات الاسمية في بداية برنامجك:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

توفر هذه الواردات إمكانية الوصول إلى الفئات والطرق الضرورية لاكتشاف تنسيق الملف.

## الخطوة 1: تهيئة الدلائل لإخراج منظم

إنشاء دلائل لتخزين الملفات استنادًا إلى تنسيقها المكتشف.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

// تأكد من وجود الدلائل
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

هذا الهيكل يسهل إدارة الملفات.

## الخطوة 2: استرداد قائمة الملفات

قم بتصفية المستندات التالفة أو غير المدعومة لتبسيط المعالجة.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

تضمن القائمة المفلترة العمل مع الملفات الصالحة فقط.

## الخطوة 3: اكتشاف تنسيقات الملفات وتصنيفها

قم بالمرور على كل ملف لتحديد تنسيقه ونقله إلى الدليل المناسب.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    // تم اكتشاف تنسيق الإخراج
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

 ال`FileFormatUtil.DetectFileFormat` تعتبر الطريقة أساسية لتحديد خصائص الوثيقة.

## خاتمة

من خلال الاستفادة من Aspose.Words لـ .NET، يصبح اكتشاف تنسيقات ملفات المستندات مهمة سهلة. تضمن القدرة على تحديد وتصنيف التنسيقات المختلفة إدارة المستندات بسلاسة، مما يعزز الإنتاجية وكفاءة سير العمل.

## الأسئلة الشائعة

### ما هو الهدف الرئيسي من الكشف عن تنسيقات المستندات؟  
يساعد اكتشاف التنسيقات على تبسيط التعامل مع المستندات من خلال تصنيف الملفات لعمليات سير العمل أو التطبيقات المحددة.

### هل يدعم Aspose.Words الملفات المشفرة؟  
نعم، يمكنه اكتشاف التشفير ومعالجة المستندات المشفرة وفقًا لذلك.

### هل يمكنني توسيع هذا الحل لأنواع الملفات الأخرى؟  
نعم، يمكنك تعديل الكود ليشمل تنسيقات إضافية أو دمج مكتبات Aspose الأخرى.

### كيف أتعامل مع التنسيقات غير المعروفة؟  
قم بتخزين التنسيقات غير المعروفة بشكل منفصل للفحص اليدوي أو المعالجة الإضافية باستخدام أدوات متخصصة.

### أين يمكنني العثور على وثائق إضافية؟  
 قم بزيارة[توثيق Aspose.Words](https://reference.aspose.com/words/net/) للحصول على أدلة وأمثلة شاملة.
