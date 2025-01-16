---
title: تخصيص الرسم البياني المتقدم باستخدام Aspose.Slides لـ .NET
linktitle: تخصيص الرسم البياني المتقدم باستخدام Aspose.Slides لـ .NET
second_title: واجهة برمجة تطبيقات معالجة PowerPoint الخاصة بـ Aspose.Slides .NET
description: استخدم الإمكانات الكاملة لبرنامج Aspose.Slides for .NET من خلال إتقان تقنيات تخصيص المخططات المتقدمة. يغطي هذا الدليل التفصيلي كل شيء بدءًا من إنشاء المخططات الأساسية وحتى التفاصيل المعقدة مثل خطوط الشبكة وعناوين المحاور والألوان المخصصة.
type: docs
weight: 10
url: /ar/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## مقدمة

إن إنشاء مخططات جذابة بصريًا ومفيدة أمر بالغ الأهمية لتقديم البيانات بشكل فعّال. توفر Aspose.Slides for .NET أدوات قوية لتخصيص المخططات، مما يتيح لك تخصيص كل جانب من جوانب مخططاتك. في هذا البرنامج التعليمي، سوف نستكشف التقنيات المتقدمة لتخصيص المخططات باستخدام Aspose.Slides for .NET.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:

1.  مكتبة Aspose.Slides لـ .NET: قم بتنزيل مكتبة Aspose.Slides وتثبيتها من[هنا](https://releases.aspose.com/slides/net/).
2. بيئة تطوير .NET: قم بإعداد بيئة تطوير .NET، مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: ستكون المعرفة ببرمجة C# مفيدة، حيث سنقوم بكتابة كود C#.

الآن، دعونا نقوم بتقسيم عملية تخصيص الرسم البياني المتقدمة إلى خطوات واضحة.

## الخطوة 1: إنشاء عرض تقديمي جديد

ابدأ بإنشاء عرض تقديمي جديد لحمل الرسم البياني الخاص بك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "Your Document Directory";

// إنشاء الدليل إذا لم يكن موجودًا.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// إنشاء عرض تقديمي
Presentation pres = new Presentation();
```

## الخطوة 2: الوصول إلى الشريحة الأولى

بعد ذلك، قم بالوصول إلى الشريحة الأولى التي تريد إضافة الرسم البياني إليها.

```csharp
// الوصول إلى الشريحة الأولى
ISlide slide = pres.Slides[0];
```

## الخطوة 3: إضافة مخطط عينة

الآن، دعونا نضيف مخططًا خطيًا به علامات إلى الشريحة.

```csharp
// إضافة مخطط عينة
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## الخطوة 4: تعيين عنوان الرسم البياني

يؤدي تعيين عنوان لمخططك إلى توفير سياق أساسي.

```csharp
// تعيين عنوان الرسم البياني
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## الخطوة 5: تخصيص خطوط الشبكة الرئيسية

بإمكانك تحسين خطوط الشبكة لمحور القيمة لتحسين إمكانية القراءة.

```csharp
// تخصيص خطوط الشبكة الرئيسية لمحور القيمة
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## الخطوة 6: تخصيص خطوط الشبكة الثانوية

وبالمثل، قم بتخصيص خطوط الشبكة الثانوية لمحور القيمة.

```csharp
// تخصيص خطوط الشبكة الثانوية لمحور القيمة
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## الخطوة 7: تحديد تنسيق رقم محور القيمة

يمكنك تنسيق الأرقام المعروضة على محور القيمة.

```csharp
// تعيين تنسيق رقم محور القيمة
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## الخطوة 8: تعيين الحد الأقصى والحد الأدنى للقيم

قم بتحديد الحد الأقصى والحد الأدنى للقيم في الرسم البياني.

```csharp
// تعيين الحد الأقصى والحد الأدنى لقيم الرسم البياني
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## الخطوة 9: تخصيص خصائص نص محور القيمة

يؤدي تحسين خصائص النص الخاصة بمحور القيمة إلى تحسين إمكانية القراءة.

```csharp
// تخصيص خصائص نص محور القيمة
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## الخطوة 10: إضافة عنوان محور القيمة

إن إضافة عنوان إلى محور القيمة قد يوضح ما تمثله البيانات.

```csharp
// تعيين عنوان محور القيمة
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## الخطوة 11: تخصيص خطوط الشبكة الرئيسية لمحور الفئة

الآن، دعونا نقوم بتعزيز خطوط الشبكة الرئيسية لمحور الفئة.

```csharp
// تخصيص خطوط الشبكة الرئيسية لمحور الفئة
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## الخطوة 12: تخصيص خطوط الشبكة الثانوية لمحور الفئة

وبالمثل، قم بتخصيص خطوط الشبكة الثانوية لمحور الفئة.

```csharp
// تخصيص خطوط الشبكة الثانوية لمحور الفئة
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## الخطوة 13: تخصيص خصائص نص محور الفئة

تحسين نمط الخط ومظهر علامات محور الفئة.

```csharp
// تخصيص خصائص نص محور الفئة
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## الخطوة 14: إضافة عنوان محور الفئة

إذا لزم الأمر، يمكنك أيضًا إضافة عنوان لمحور الفئة.

```csharp
// تعيين عنوان محور الفئة
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## الخطوة 15: التخصيصات الإضافية

قم بتعزيز الرسم البياني الخاص بك بشكل أكبر باستخدام التخصيصات الإضافية، مثل الأساطير، وألوان الجدران، وإعدادات منطقة الرسم البياني.

```csharp
// تخصيصات إضافية (اختياري)

// تخصيص خصائص نص الأساطير
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// إظهار أساطير الرسم البياني دون تداخل الرسم البياني
chart.Legend.Overlay = true;

// مخطط ضبط لون الحائط الخلفي
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// تعيين لون أرضية الرسم البياني
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// تعيين لون مساحة الرسم
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// حفظ العرض التقديمي
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## خاتمة

في هذا الدليل الشامل، قمنا بتغطية تقنيات تخصيص المخططات المتقدمة باستخدام Aspose.Slides for .NET. لقد تعلمت كيفية إنشاء عرض تقديمي وإضافة مخطط وتحسين مظهره وتخصيص عناصر المخطط المختلفة مثل خطوط الشبكة وعناوين المحاور والأساطير. 

## الأسئلة الشائعة

### ما هي إصدارات .NET التي يدعمها Aspose.Slides لـ .NET؟
يدعم Aspose.Slides for .NET إصدارات .NET المختلفة، بما في ذلك .NET Framework و.NET Core. راجع الوثائق للحصول على قائمة كاملة بالإصدارات المدعومة.

### هل يمكنني إنشاء مخططات بيانية من مصادر بيانات مثل ملفات Excel؟
نعم، يتيح لك Aspose.Slides إنشاء مخططات بيانية من مصادر بيانات خارجية مثل جداول بيانات Excel. راجع الوثائق للحصول على أمثلة مفصلة.

### كيف يمكنني إضافة تسميات بيانات مخصصة إلى سلسلة المخططات الخاصة بي؟
 لإضافة تسميات بيانات مخصصة، قم بالوصول إلى`DataLabels` خصائص السلسلة وتخصيص العلامات حسب الحاجة. يمكنك العثور على عينات التعليمات البرمجية في الوثائق.

### هل من الممكن تصدير الرسم البياني إلى تنسيقات مختلفة، مثل PDF أو الصور؟
بالتأكيد! يتيح لك Aspose.Slides تصدير عروضك التقديمية مع المخططات إلى تنسيقات مختلفة، بما في ذلك تنسيقات PDF والصور.

### أين يمكنني العثور على المزيد من البرامج التعليمية والأمثلة لـ Aspose.Slides لـ .NET؟
 قم بزيارة موقع Aspose.Slides[موقع إلكتروني](https://reference.aspose.com/slides/net/) للحصول على دروس تعليمية موسعة، وأمثلة برمجية، ووثائق.