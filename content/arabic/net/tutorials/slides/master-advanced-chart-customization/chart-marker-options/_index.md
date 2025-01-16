---
title: خيارات علامة الرسم البياني على نقطة البيانات في Aspose.Slides .NET
linktitle: خيارات علامة الرسم البياني على نقطة البيانات في Aspose.Slides .NET
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: تعرف على كيفية تحسين مخططات PowerPoint الخاصة بك باستخدام خيارات العلامات المخصصة باستخدام Aspose.Slides for .NET. يغطي هذا الدليل خطوة بخطوة المتطلبات الأساسية وإنشاء المخططات وتنسيق نقاط البيانات والمزيد.
type: docs
weight: 11
url: /ar/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## مقدمة

إن دمج الوسائل البصرية في العروض التقديمية أمر ضروري للتواصل المؤثر. توفر Aspose.Slides for .NET أدوات قوية لإنشاء المخططات وتخصيصها، مما يتيح للمطورين تحسين عروض البيانات الخاصة بهم. إحدى الميزات البارزة هي القدرة على استخدام خيارات علامة المخطط على نقاط البيانات، مما يسمح بالتخصيص الدقيق للمخططات ذات المظهر الاحترافي. سترشدك هذه المقالة خلال كل خطوة مطلوبة لتحقيق ذلك.

## المتطلبات الأساسية

قبل المتابعة، تأكد مما يلي:

-  تم تثبيت Aspose.Slides لـ .NET: قم بتنزيله من[هنا](https://releases.aspose.com/slides/net/).
- الإعداد الأساسي: ملف عرض تقديمي، مثل "Test.pptx"، في دليل العمل الخاص بك.
- بيئة التطوير: Visual Studio أو ما يعادله، مهيأة لـ .NET.

## استيراد المساحات المطلوبة

أضف مساحات الأسماء الضرورية إلى مشروعك لضمان التطوير السلس:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## الخطوة 1: إنشاء مخطط في العرض التقديمي الخاص بك

ابدأ بإنشاء مخطط افتراضي على الشريحة الأولى من العرض التقديمي الخاص بك:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 وهذا يضيف`LineWithMarkers` قم بإضافة مخطط إلى الشريحة الخاصة بك بالأبعاد المحددة.

## الخطوة 2: استرداد فهرس ورقة عمل بيانات الرسم البياني

يعد فهرس ورقة عمل بيانات الرسم البياني الافتراضية ضروريًا لمزيد من التخصيص:

```csharp
int defaultWorksheetIndex = 0;
```

## الخطوة 3: الوصول إلى مصنف بيانات الرسم البياني

للتعامل مع بيانات الرسم البياني، قم باسترداد المصنف المرتبط:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## الخطوة 4: تكوين سلسلة المخططات وإضافة نقاط البيانات

مسح السلسلة الافتراضية وإضافة نقاط بيانات جديدة لسلسلتك:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// إضافة نقاط البيانات إلى السلسلة
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## الخطوة 5: تطبيق تعبئة الصور على علامات نقاط البيانات

يمكن للصور المخصصة أن تجعل علامات البيانات جذابة بصريًا:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// تعيين صور مخصصة للعلامات
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## الخطوة 6: تخصيص حجم العلامة

تعديل حجم العلامات لتحسين الرؤية:

```csharp
series.Marker.Size = 20;
```

## الخطوة 7: حفظ العرض التقديمي المحدث

احفظ العرض التقديمي المخصص في الموقع المطلوب:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## خاتمة

يزود برنامج Aspose.Slides for .NET المطورين بالأدوات اللازمة لإنشاء مخططات احترافية مع خيارات تخصيص غنية. من خلال الاستفادة من خيارات علامة المخطط، يمكنك تحسين المظهر المرئي ووضوح العروض التقديمية بشكل كبير. يضمن هذا الدليل التفصيلي أن حتى التخصيصات المعقدة يمكن تنفيذها بسهولة.

## الأسئلة الشائعة

### هل يمكنني استخدام أي تنسيق صورة لتخصيص العلامة؟
نعم، يدعم Aspose.Slides تنسيقات الصور المختلفة، بما في ذلك JPEG، وPNG، وBMP، لتخصيص العلامة.

### كيف يمكنني تغيير نوع الرسم البياني بعد إنشائه؟
 لتغيير نوع الرسم البياني، قم بالوصول إلى`chart.Type` الملكية وتعيين مختلفة`ChartType`.

### هل Aspose.Slides for .NET متوافق مع إصدارات PowerPoint الأقدم؟
نعم، فهو يدعم التوافق مع تنسيقات PowerPoint القديمة، مما يضمن التنوع.

### هل يمكنني تحديث بيانات الرسم البياني بشكل ديناميكي؟
 بالتأكيد. استخدم`IChartDataWorkbook` لتحديث بيانات الرسم البياني برمجيًا.

### أين يمكنني العثور على المزيد من الموارد؟
 استكشف[توثيق Aspose.Slides](https://reference.aspose.com/slides/net/)أو انضم إلى[المنتديات المجتمعية](https://forum.aspose.com/) للحصول على الدعم.