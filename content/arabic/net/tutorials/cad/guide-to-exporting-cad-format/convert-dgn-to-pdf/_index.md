---
title: تحويل DGN إلى PDF في Aspose.CAD لـ .NET
linktitle: تحويل DGN إلى PDF في Aspose.CAD لـ .NET
second_title: Aspose.CAD .NET - تنسيق ملفات CAD وBIM
description: تعرف على كيفية تحويل ملفات DGN إلى PDF بسهولة باستخدام مكتبة Aspose.CAD القوية لـ .NET. تم تصميم هذا الدليل التفصيلي للمطورين من جميع المستويات.
type: docs
weight: 12
url: /ar/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## مقدمة

قد يكون التنقل في عالم ملفات CAD أمرًا صعبًا، ولكن باستخدام Aspose.CAD for .NET، يمكن للمطورين التعامل بسهولة مع تنسيقات CAD المختلفة وتحويلها. إحدى الاحتياجات الشائعة هي تحويل ملفات DGN إلى ملفات PDF، والتي سنستكشفها خطوة بخطوة في هذا البرنامج التعليمي.

## المتطلبات الأساسية

للمتابعة، تأكد من أن لديك ما يلي:

- الكفاءة الأساسية في لغة C# وإطار عمل .NET.
-  تم تثبيت مكتبة Aspose.CAD لـ .NET. يمكنك تنزيلها[هنا](https://releases.aspose.com/cad/net/).
- نموذج لملف DGN (على سبيل المثال، Nikon_D90_Camera.dgn). 

## الخطوة 1: استيراد المساحات المطلوبة

ابدأ باستيراد المساحات الأسماءية ذات الصلة في مشروع C# الخاص بك:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## الخطوة 2: تحميل ملف DGN

حدد الدليل لملف DGN الخاص بك وقم بتحميله باستخدام الكود التالي:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // سيتم إجراء المعالجة الإضافية هنا...
}
```

## الخطوة 3: تكوين خيارات التنقيح

بعد ذلك، قم بإعداد خيارات التنقيح لتحديد كيفية عرض DGN الخاص بك في ملف PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // ضبط العرض حسب الحاجة
    PageHeight = 300, // ضبط الارتفاع حسب الحاجة
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## الخطوة 4: إنشاء خيارات PDF

قم بتحديد خيارات PDF، ودمج إعدادات التحويل إلى بيانات نقطية التي تم تكوينها مسبقًا:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## الخطوة 5: احفظ DGN بصيغة PDF

وأخيرًا، قم بحفظ ملف DGN بتنسيق PDF باستخدام الخيارات التي قمت بتكوينها:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## خاتمة

تهانينا! لقد نجحت في تحويل ملف DGN إلى ملف PDF باستخدام Aspose.CAD لـ .NET. لقد أرشدك هذا البرنامج التعليمي البسيط خلال تحميل ملف DGN، وتعيين خيارات التنقيح، وحفظ الناتج بتنسيق PDF.

## الأسئلة الشائعة

### هل أحتاج إلى معرفة مسبقة بـ CAD لاستخدام Aspose.CAD؟  
بالتأكيد! تم تصميم Aspose.CAD لتبسيط مهام CAD المعقدة، مما يجعله في متناول جميع المطورين، بغض النظر عن معرفتهم بـ CAD.

### أين يمكنني العثور على المزيد من الموارد والوثائق الخاصة بـ Aspose.CAD؟  
 يمكنك استكشاف الأدلة والأمثلة الشاملة في[توثيق Aspose.CAD](https://reference.aspose.com/cad/net/).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.CAD؟  
 نعم، يمكن الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.CAD؟  
 يمكنك طلب تراخيص مؤقتة[هنا](https://purchase.conholdate.com/temporary-license/).

### هل تحتاج إلى مساعدة أو لديك أسئلة؟  
انضم إلى المحادثة في[منتدى Aspose.CAD](https://forum.aspose.com/c/cad/19) للحصول على الدعم المجتمعي والاستفسارات.