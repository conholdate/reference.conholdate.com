---
title: تتبع تقدم تحويل البريد الإلكتروني باستخدام Aspose.Email لـ .NET
linktitle: تتبع تقدم تحويل البريد الإلكتروني باستخدام Aspose.Email لـ .NET
second_title: واجهة برمجة تطبيقات معالجة البريد الإلكتروني Aspose.Email .NET
description: تعرف خطوة بخطوة على كيفية تتبع تقدم تحويل البريد الإلكتروني في C# باستخدام Aspose.Email لـ .NET. عزز كفاءة مشروعك من خلال هذا البرنامج التعليمي المفصل.
type: docs
weight: 12
url: /ar/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## مقدمة

غالبًا ما تتضمن إدارة مستندات البريد الإلكتروني بكفاءة تتبع تقدم تحويلها. يوفر Aspose.Email لـ .NET أدوات قوية لإنجاز هذه المهمة، مما يسمح للمطورين بالتعامل مع عمليات البريد الإلكتروني بسلاسة. يتعمق هذا البرنامج التعليمي في كيفية تتبع تقدم تحويل مستندات البريد الإلكتروني بلغة C#، مع تقسيم العملية خطوة بخطوة لسهولة الفهم.  

## المتطلبات الأساسية  

قبل أن نتعمق في البرنامج التعليمي، دعنا نتأكد من إعداد كل شيء:  

1.  Aspose.Email لـ .NET: قم بتنزيل وتثبيت[Aspose.Email لـ .NET](https://releases.aspose.com/email/net/) مكتبة.  
2. بيئة التطوير: قم بتثبيت Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.  
3. .NET Framework: تأكد من تثبيت .NET Framework 4.5 أو الإصدار الأحدث.  
4.  رخصة مؤقتة: فكر في الحصول على رخصة[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) لاستكشاف الميزات الكاملة لـ Aspose.Email.  
5.  نموذج ملف البريد الإلكتروني: قم بإعداد`.eml` ملف (على سبيل المثال،`test.eml`) لاستخدامها كعينة.  

## استيراد الحزم  

لاستخدام Aspose.Email في مشروعك، ستحتاج إلى استيراد مساحات الأسماء المطلوبة. أضف عبارات الاستخدام التالية في أعلى ملفك:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## الخطوة 1: إعداد مشروعك  

ابدأ بإنشاء تطبيق وحدة تحكم C# جديد في Visual Studio. سيعمل هذا التطبيق كأساس لتنفيذ تتبع تحويل مستندات البريد الإلكتروني.  
  
1. افتح Visual Studio وقم بإنشاء مشروع تطبيق وحدة تحكم جديد.  
2. قم بتثبيت حزمة Aspose.Email NuGet:  
```sh
Install-Package Aspose.Email
```  
3.  أضف`.eml` الملف إلى دليل المشروع الخاص بك.  

## الخطوة 2: تحميل ملف البريد الإلكتروني  

 الآن، قم بتحميل ملف البريد الإلكتروني إلى`MailMessage` هذا هو الخطوة الأولى في التعامل مع بيانات البريد الإلكتروني.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`:يحدد الدليل الذي يوجد به ملف البريد الإلكتروني الخاص بك.  
- `MailMessage.Load` :يقرأ`.eml` الملف وإعداده للعمليات الإضافية.  

## الخطوة 3: تهيئة تدفق الذاكرة  

 بعد ذلك، قم بإنشاء`MemoryStream` كائن لتخزين بيانات البريد الإلكتروني المحولة مؤقتًا.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 أ`MemoryStream` يتم استخدامه هنا لإدارة مخرجات عملية التحويل دون حفظ البيانات مباشرة على القرص.  

## الخطوة 4: تحديد خيارات التحويل  

 إعداد`EmlSaveOptions` مع معالج تقدم مخصص لتتبع تقدم التحويل.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`:يحدد تنسيق الإخراج.  
- `CustomProgressHandler`:تعيين وظيفة معالج مخصصة لمراقبة التقدم.  

## الخطوة 5: احفظ البريد الإلكتروني في مجرى الذاكرة  

احفظ`MailMessage` الكائن باستخدام الخيارات المحددة، مما يتيح وظيفة تتبع التقدم.  
 
```csharp
msg.Save(ms, opt);
```
 
تعمل هذه الخطوة على بدء عملية تحويل البريد الإلكتروني وإرسال التحديثات إلى معالج التقدم.  

## الخطوة 6: تنفيذ معالج التقدم  

 تعريف`ShowEmlConversionProgress` طريقة للتعامل مع تحديثات التقدم وعرضها في وحدة التحكم.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`:يوفر تفاصيل حول عملية التحويل.  
-  حالات التبديل: التعامل مع المراحل المختلفة للتحويل:`MimeStructureCreated`, `MimePartSaved` ، و`SavedToStream`.  

### ماذا تتوقع؟  
مع تقدم عملية التحويل، ستشاهد تحديثات مفصلة مطبوعة على وحدة التحكم، مثل:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## خاتمة  

لم يكن تتبع تقدم تحويل مستندات البريد الإلكتروني في C# أسهل من أي وقت مضى، وذلك بفضل Aspose.Email for .NET. باتباع هذا البرنامج التعليمي، تعلمت كيفية تحميل ملف بريد إلكتروني، وإعداد معالج للتقدم، وحفظ بيانات البريد الإلكتروني أثناء مراقبة العملية بأكملها. تضمن لك هذه الوظيفة البقاء على اطلاع والتحكم أثناء عمليات مستند البريد الإلكتروني.  

## الأسئلة الشائعة  

###  هل يمكنني استخدام هذا الكود لتنسيقات أخرى غير`.eml`?  
 نعم، تعديل`MailMessageSaveType`لتتناسب مع التنسيقات الأخرى مثل MSG أو MHTML.  

### كيف أتعامل مع ملفات البريد الإلكتروني الكبيرة؟  
 فكر في استخدام`FileStream` بدلا من`MemoryStream` للحصول على أداء أفضل مع الملفات الكبيرة.  

### ما هو الترخيص المؤقت وكيف أحصل عليه؟  
 يتيح لك الترخيص المؤقت تقييم الميزات الكاملة للمكتبة مجانًا. احصل عليه[هنا](https://purchase.aspose.com/temporary-license/).  

### هل يمكنني دمج هذا الكود في تطبيق ويب؟  
نعم، الكود متوافق مع تطبيقات الويب التي تستخدم ASP.NET أو الأطر المماثلة.  

### أين يمكنني العثور على موارد إضافية؟  
 تحقق من[التوثيق](https://reference.aspose.com/email/net/) أو قم بزيارة[منتدى الدعم](https://forum.aspose.com/c/email/12/) للحصول على المساعدة.  