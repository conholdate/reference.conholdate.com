---
title: تحويل ملفات التعريف إلى Emf أو WMF
linktitle: تحويل ملفات التعريف إلى Emf أو WMF
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تحويل صور SVG إلى تنسيقات EMF أو WMF في مستندات Word بسهولة باستخدام Aspose.Words for .NET. دليل خطوة بخطوة مع أمثلة التعليمات البرمجية للحصول على نتائج دقيقة ومتوافقة.
type: docs
weight: 10
url: /ar/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## مقدمة

إن إدارة وتحويل تنسيقات الصور بكفاءة يشكل جزءًا أساسيًا من إنشاء مستندات Word احترافية. في هذا الدليل، نتعمق في استخدام Aspose.Words for .NET لتحويل صور SVG إلى تنسيقات EMF (Enhanced Metafile) أو WMF (Windows Metafile) لتحقيق التكامل السلس. يوفر هذا البرنامج التعليمي تعليمات واضحة خطوة بخطوة لمساعدة المطورين على تنفيذ التحويل بسهولة.

## المتطلبات الأساسية لتحويل SVG إلى EMF أو WMF

لضمان تجربة تطوير سلسة، تأكد من استيفاء المتطلبات الأساسية التالية:

- Aspose.Words لـ .NET: احصل على أحدث إصدار من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: تحقق من تثبيت .NET Framework (أو .NET Core/5/6 حسب بيئتك).
- بيئة التطوير: يوصى باستخدام Visual Studio لميزاته القوية.
- إتقان لغة C#: المعرفة الأساسية ببرمجة لغة C# أمر ضروري.

## استيراد المساحات المطلوبة

في مشروعك، قم باستيراد المساحات الأساسية اللازمة للوصول إلى وظائف Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحديد دليل المستندات

قم بإعداد مسار الدليل الذي سيتم تخزين مستندات Word فيه. يعد هذا أمرًا ضروريًا لإدارة ملفات الإخراج بشكل فعال.

```csharp
string dataDir = @"C:\MyDocuments\";
```

 يستبدل`@"C:\MyDocuments\"` مع المسار الذي تريده.

## الخطوة 2: تحضير سلسلة HTML التي تحتوي على SVG

قم بإنشاء سلسلة HTML تتضمن محتوى SVG الخاص بك. يتيح هذا لـ Aspose.Words عرض ومعالجة SVG.

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' عرض='300' ارتفاع='100' viewBox='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## الخطوة 3: تكوين خيارات تحميل HTML

 لضمان التعامل السليم مع تحويل SVG، قم بتكوين`HtmlLoadOptions` مع`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## الخطوة 4: تحميل HTML إلى مستند Word

استخدم خيارات التحميل المُهيأة لإنشاء`Document` كائن من سلسلة HTML.

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## الخطوة 5: تكوين خيارات الحفظ لـ EMF/WMF

 قم بتخصيص خيارات الحفظ لتحديد تنسيق الملف التعريفي المطلوب. هنا، نختار`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## الخطوة 6: حفظ المستند

احفظ المستند باستخدام خيارات الحفظ المحددة.

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

سيحتوي الملف الناتج على محتوى SVG المحول إلى تنسيق EMF.

## خاتمة

لقد أوضح هذا البرنامج التعليمي كيفية تحويل صور SVG إلى تنسيقات EMF أو WMF باستخدام Aspose.Words for .NET. باتباع هذه الخطوات، يمكنك تحسين التوافق والدقة المرئية لمستندات Word الخاصة بك. سواء كنت تقوم بأتمتة إنشاء المستندات أو إعداد تقارير عالية الجودة، فإن هذه الطريقة تضمن نتائج سلسة.

## الأسئلة الشائعة

### هل يمكنني استخدام هذه الطريقة لمعالجة دفعات من ملفات SVG المتعددة؟
نعم، يمكنك التكرار عبر ملفات HTML متعددة تحتوي على SVGs، وتطبيق نفس العملية في حلقة.

### ما هو الفرق بين EMF و WMF؟
EMF هو إصدار محسّن من WMF، حيث يوفر دعمًا أفضل للرسومات المعقدة وأحجام البيانات الأكبر.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، يدعم Aspose.Words for .NET .NET Core و.NET 5/6، مما يجعله مناسبًا لتطبيقات الأنظمة الأساسية المتعددة الحديثة.

### هل يمكنني الاحتفاظ بتنسيق SVG الأصلي في الإخراج؟
لا، هذه الطريقة تقوم على وجه التحديد بتحويل SVG إلى EMF/WMF. ومع ذلك، يمكنك الاحتفاظ بملف SVG الأصلي عن طريق تضمينه مباشرة في المستند دون تحويل.

### أين يمكنني تنزيل نسخة تجريبية مجانية من Aspose.Words؟
 يمكنك تنزيل نسخة تجريبية مجانية من[صفحة إصدارات Aspose](https://releases.aspose.com/).