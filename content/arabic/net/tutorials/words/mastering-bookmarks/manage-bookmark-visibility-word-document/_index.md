---
title: إدارة ظهور الإشارات المرجعية في مستندات Word
linktitle: إدارة ظهور الإشارات المرجعية في مستندات Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: اكتشف كيفية التحكم ببراعة في مدى رؤية المحتوى في مستندات Word باستخدام Aspose.Words for .NET. هذا الدليل خطوة بخطوة.
type: docs
weight: 10
url: /ar/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## مقدمة

هل أنت مستعد لرفع مستوى مهاراتك في التعامل مع المستندات باستخدام Aspose.Words for .NET؟ سواء كنت مطورًا متمرسًا يقوم بأتمتة مهام المستندات أو فردًا فضوليًا يستكشف التحكم البرمجي في ملفات Word، فإن هذا الدليل مصمم خصيصًا لك. اليوم، سنتعمق في كيفية إظهار المحتوى وإخفائه بناءً على الإشارات المرجعية في مستند Word. لنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Visual Studio: أي إصدار متوافق مع .NET.
2. Aspose.Words for .NET: قم بتنزيله[هنا](https://releases.aspose.com/words/net/).
3. المعرفة الأساسية بلغة C#: ستكون المعرفة بكيفية كتابة برامج C# البسيطة كافية.
4. نموذج مستند Word: قم بإعداد مستند Word (على سبيل المثال، "Bookmarks.docx") يحتوي على إشارات مرجعية لهذا البرنامج التعليمي.

### إنشاء مشروع جديد

1. افتح Visual Studio وأنشئ مشروع تطبيق وحدة تحكم جديد (.NET Core). قم بتسميته بشيء مثل "BookmarkVisibilityManager".

### تثبيت Aspose.Words لـ .NET

أضف Aspose.Words إلى مشروعك عبر NuGet Package Manager:

1. انتقل إلى الأدوات > مدير حزم NuGet > إدارة حزم NuGet للحل.
2. ابحث عن "Aspose.Words".
3. تثبيت الحزمة.

بعد إعداد مشروعك، دعنا ننتقل إلى تحميل المستند.

## استيراد المساحات الاسمية

ابدأ باستيراد مساحات الأسماء الأساسية. توفر هذه المساحات الفئات والطرق اللازمة لمعالجة مستندات Word باستخدام Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## الخطوة 1: تحميل المستند

للتعامل مع مستند Word، نحتاج إلى تحميله أولاً. وإليك كيفية القيام بذلك:

```csharp
// قم بتحديد المسار إلى دليل المستند الخاص بك.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 تحدد هذه القطعة المسار إلى دليل المستند الخاص بك وتحمل المستند في`Document` هدف.

## الخطوة 2: إظهار/إخفاء المحتوى المُضاف إلى الإشارات المرجعية

 الآن، دعنا ننشئ طريقة لتبديل إمكانية رؤية المحتوى بناءً على الإشارات المرجعية. سنسمي هذه الطريقة`ShowHideBookmarkedContent`.

وهنا تنفيذ الطريقة:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  استرجاع الإشارة المرجعية:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` يقوم بجلب الإشارة المرجعية المحددة.
- عبور العقدة: نقوم بالتكرار عبر العقد الموجودة داخل الإشارة المرجعية.
-  تبديل الرؤية: لكل`Run` العقدة (التي تمثل جزءًا من النص)، نقوم بتعيينها`Hidden` الممتلكات القائمة على`isHidden` المعلمة.

## الخطوة 3: تطبيق الطريقة

الآن بعد أن أصبحت طريقتنا جاهزة، فلنستخدمها لإظهار أو إخفاء المحتوى داخل إشارة مرجعية محددة:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // إخفاء المحتوى داخل "MyBookmark1"
```

سيقوم هذا السطر بإخفاء المحتوى المرتبط بالإشارة المرجعية المسماة "MyBookmark1".

## الخطوة 4: حفظ المستند

بمجرد إجراء التغييرات، لا تنس حفظ المستند المعدّل:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

يؤدي هذا إلى حفظ المستند بإعدادات الرؤية المحدثة.

## خاتمة

تهانينا! لقد نجحت في تعلم كيفية إظهار وإخفاء المحتوى الذي تمت الإشارة إليه في مستند Word باستخدام Aspose.Words for .NET. تعمل هذه المكتبة القوية على تبسيط معالجة المستندات، مما يجعلها مثالية لأتمتة التقارير أو إنشاء القوالب أو تجربة ملفات Word. استمتع بالبرمجة!

## الأسئلة الشائعة

### هل يمكنني تبديل إشارات مرجعية متعددة مرة واحدة؟
 نعم، فقط اتصل بـ`ShowHideBookmarkedContent` الطريقة لكل إشارة مرجعية تريد تبديلها.

### هل يؤثر إخفاء المحتوى على بنية المستند؟
لا، إخفاء المحتوى يؤثر فقط على ظهوره، ويبقى المحتوى سليمًا داخل المستند.

### هل يمكنني استخدام هذه الطريقة لأنواع أخرى من المحتوى؟
تم تصميم هذه الطريقة خصيصًا لعمليات تشغيل النصوص. بالنسبة لأنواع المحتوى الأخرى، ستحتاج إلى تكييف منطق عبور العقدة وفقًا لذلك.

### هل Aspose.Words لـ .NET مجاني؟
 يقدم Aspose.Words نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) ولكن يلزم الحصول على ترخيص كامل للاستخدام الإنتاجي. يمكنك شراؤه[هنا](https://purchase.aspose.com/buy).

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 للحصول على الدعم، قم بزيارة منتدى مجتمع Aspose[هنا](https://forum.aspose.com/c/words/8).