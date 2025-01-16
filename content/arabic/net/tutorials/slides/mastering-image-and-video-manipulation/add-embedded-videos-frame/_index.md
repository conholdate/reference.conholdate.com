---
title: إضافة إطار فيديو مضمّن في عروض .NET التقديمية
linktitle: إضافة إطار فيديو مضمّن في عروض .NET التقديمية
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: أطلق العنان لإمكانات عروضك التقديمية من خلال تعلم كيفية تضمين مقاطع الفيديو باستخدام Aspose.Slides for .NET. يرشدك هذا البرنامج التعليمي الشامل خلال عملية دمج عناصر الوسائط المتعددة خطوة بخطوة.
type: docs
weight: 19
url: /ar/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## مقدمة

في عالم العروض التقديمية السريع الوتيرة اليوم، يمكن أن يؤدي دمج عناصر الوسائط المتعددة إلى تعزيز المشاركة والاحتفاظ بالجمهور بشكل كبير. يوفر Aspose.Slides for .NET حلاً قويًا لتضمين إطارات الفيديو في الشرائح الخاصة بك. سيرشدك هذا البرنامج التعليمي خلال العملية خطوة بخطوة، مما يضمن تجربة سلسة من البداية إلى النهاية.

## المتطلبات الأساسية

قبل البدء، تأكد من توفر ما يلي:

-  Aspose.Slides لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من[صفحة الإصدار](https://releases.aspose.com/slides/net/).
- المحتوى الإعلامي: ملف فيديو (على سبيل المثال، "Wildlife.mp4") الذي تريد تضمينه في العرض التقديمي الخاص بك.

## استيراد المساحات الاسمية الضرورية

ابدأ باستيراد المساحات المطلوبة في مشروع .NET الخاص بك:

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## الخطوة 1: إعداد الدلائل الخاصة بك

تأكد من أن مشروعك يتضمن الدلائل اللازمة للملفات الوثائقية والوسائط:

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// إنشاء الدليل إذا لم يكن موجودًا
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## الخطوة 2: إنشاء مثيل لفئة العرض التقديمي

 إنشاء مثيل لـ`Presentation` الفئة التي تمثل ملف PPTX الخاص بك:

```csharp
using (Presentation pres = new Presentation())
{
    // احصل على الشريحة الأولى
    ISlide sld = pres.Slides[0];
```

## الخطوة 3: تضمين الفيديو

قم بتضمين الفيديو في العرض التقديمي الخاص بك باستخدام الكود التالي:

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## الخطوة 4: إضافة إطار فيديو

بعد ذلك، أضف إطار فيديو إلى الشريحة:

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## الخطوة 5: تكوين خصائص الفيديو

ضبط خصائص الفيديو، بما في ذلك وضع التشغيل ومستوى الصوت:

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // تشغيل الفيديو تلقائيا
vf.Volume = AudioVolumeMode.Loud; // ضبط مستوى الصوت
```

## الخطوة 6: احفظ العرض التقديمي الخاص بك

وأخيرًا، قم بحفظ ملف PPTX المعدّل على القرص:

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

بإمكانك تكرار هذه الخطوات لكل مقطع فيديو ترغب بتضمينه في العرض التقديمي الخاص بك.

## خاتمة

تهانينا! لقد نجحت في تضمين إطار فيديو في عرضك التقديمي باستخدام Aspose.Slides for .NET. يمكن لهذه الميزة الديناميكية أن ترفع عروضك التقديمية إلى المستوى التالي، فتجذب انتباه جمهورك من خلال الوسائط المتعددة المتكاملة بسلاسة.

## الأسئلة الشائعة

### هل يمكنني تضمين مقاطع فيديو في أي شريحة من العرض التقديمي؟

 نعم، يمكنك تحديد أي شريحة عن طريق ضبط الفهرس في`pres.Slides[index]`.

### ما هي صيغ الفيديو المدعومة؟

يدعم Aspose.Slides تنسيقات الفيديو المختلفة، بما في ذلك MP4، وAVI، وWMV.

### هل يمكنني تخصيص حجم وموضع إطار الفيديو؟

 بالتأكيد! يمكنك تعديل المعلمات في`AddVideoFrame(x, y, width, height, video)` لتناسب احتياجاتك.

### هل هناك حد لعدد مقاطع الفيديو التي يمكنني تضمينها؟

يعتمد الحد الأقصى لمقاطع الفيديو المضمنة عادةً على سعة برنامج العرض التقديمي لديك.

### أين يمكنني الحصول على مزيد من المساعدة أو مشاركة تجربتي؟

 لا تتردد في زيارة[منتدى Aspose.Slides](https://forum.aspose.com/c/slides/11) للدعم المجتمعي والمناقشات.