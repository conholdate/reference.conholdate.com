---
title: การปรับแต่งแผนภูมิขั้นสูงด้วย Aspose.Slides สำหรับ .NET
linktitle: การปรับแต่งแผนภูมิขั้นสูงด้วย Aspose.Slides สำหรับ .NET
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: ปลดล็อกศักยภาพทั้งหมดของ Aspose.Slides สำหรับ .NET โดยเรียนรู้เทคนิคการปรับแต่งแผนภูมิขั้นสูง คำแนะนำทีละขั้นตอนนี้ครอบคลุมทุกอย่างตั้งแต่การสร้างแผนภูมิพื้นฐานไปจนถึงรายละเอียดที่ซับซ้อน เช่น เส้นตาราง ชื่อแกน และสีที่กำหนดเอง
type: docs
weight: 10
url: /th/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## การแนะนำ

การสร้างแผนภูมิที่ดึงดูดสายตาและให้ข้อมูลเป็นสิ่งสำคัญสำหรับการนำเสนอข้อมูลอย่างมีประสิทธิภาพ Aspose.Slides สำหรับ .NET นำเสนอเครื่องมืออันทรงพลังสำหรับการปรับแต่งแผนภูมิ ช่วยให้คุณปรับแต่งแผนภูมิของคุณได้ทุกแง่มุม ในบทช่วยสอนนี้ เราจะสำรวจเทคนิคขั้นสูงสำหรับการปรับแต่งแผนภูมิโดยใช้ Aspose.Slides สำหรับ .NET

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1.  Aspose.Slides สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งไลบรารี Aspose.Slides จาก[ที่นี่](https://releases.aspose.com/slides/net/).
2. สภาพแวดล้อมการพัฒนา .NET: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET เช่น Visual Studio
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# จะเป็นประโยชน์เนื่องจากเราจะเขียนโค้ด C#

ตอนนี้มาแบ่งกระบวนการปรับแต่งแผนภูมิขั้นสูงออกเป็นขั้นตอนที่ชัดเจน

## ขั้นตอนที่ 1: สร้างงานนำเสนอใหม่

เริ่มต้นด้วยการสร้างการนำเสนอใหม่เพื่อเก็บแผนภูมิของคุณ

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "Your Document Directory";

// สร้างไดเร็กทอรีถ้ายังไม่มีอยู่
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// สร้างตัวอย่างการนำเสนอ
Presentation pres = new Presentation();
```

## ขั้นตอนที่ 2: เข้าถึงสไลด์แรก

ขั้นตอนต่อไปคือเข้าถึงสไลด์แรกที่คุณต้องการเพิ่มแผนภูมิ

```csharp
// เข้าถึงสไลด์แรก
ISlide slide = pres.Slides[0];
```

## ขั้นตอนที่ 3: เพิ่มแผนภูมิตัวอย่าง

ตอนนี้เรามาเพิ่มแผนภูมิเส้นพร้อมเครื่องหมายลงในสไลด์กัน

```csharp
// เพิ่มแผนภูมิตัวอย่าง
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## ขั้นตอนที่ 4: ตั้งชื่อแผนภูมิ

การตั้งชื่อเรื่องให้กับแผนภูมิของคุณจะให้บริบทที่จำเป็น

```csharp
// ตั้งชื่อแผนภูมิ
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

## ขั้นตอนที่ 5: ปรับแต่งเส้นกริดหลัก

คุณสามารถปรับปรุงเส้นตารางสำหรับแกนค่าเพื่อให้สามารถอ่านได้ดีขึ้น

```csharp
// ปรับแต่งเส้นกริดหลักสำหรับแกนค่า
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## ขั้นตอนที่ 6: ปรับแต่งเส้นกริดย่อย

ในทำนองเดียวกัน ปรับแต่งเส้นกริดรองสำหรับแกนค่า

```csharp
// ปรับแต่งเส้นกริดรองสำหรับแกนค่า
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## ขั้นตอนที่ 7: กำหนดรูปแบบตัวเลขแกนค่า

คุณสามารถจัดรูปแบบตัวเลขที่แสดงบนแกนค่าได้

```csharp
// ตั้งค่ารูปแบบหมายเลขแกนค่า
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## ขั้นตอนที่ 8: ตั้งค่าสูงสุดและต่ำสุด

กำหนดค่าสูงสุดและต่ำสุดสำหรับแผนภูมิ

```csharp
// ตั้งค่าสูงสุดและต่ำสุดของแผนภูมิ
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## ขั้นตอนที่ 9: ปรับแต่งคุณสมบัติข้อความแกนค่า

การปรับปรุงคุณสมบัติข้อความของแกนค่าจะช่วยให้อ่านได้ง่ายขึ้น

```csharp
// ปรับแต่งคุณสมบัติข้อความแกนค่า
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## ขั้นตอนที่ 10: เพิ่มชื่อแกนค่า

การเพิ่มชื่อเรื่องให้กับแกนค่าจะช่วยชี้แจงให้ชัดเจนว่าข้อมูลแสดงถึงอะไร

```csharp
// ตั้งค่าชื่อแกนค่า
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

## ขั้นตอนที่ 11: ปรับแต่งเส้นกริดหลักสำหรับแกนหมวดหมู่

ตอนนี้ มาปรับปรุงเส้นกริดหลักของแกนหมวดหมู่กัน

```csharp
// ปรับแต่งเส้นกริดหลักสำหรับแกนหมวดหมู่
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## ขั้นตอนที่ 12: ปรับแต่งเส้นกริดย่อยสำหรับแกนหมวดหมู่

ในทำนองเดียวกัน ปรับแต่งเส้นกริดรองสำหรับแกนหมวดหมู่

```csharp
// ปรับแต่งเส้นกริดย่อยสำหรับแกนหมวดหมู่
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## ขั้นตอนที่ 13: ปรับแต่งคุณสมบัติข้อความแกนหมวดหมู่

ปรับปรุงรูปแบบแบบอักษรและการปรากฏตัวของป้ายแกนหมวดหมู่

```csharp
// ปรับแต่งคุณสมบัติข้อความแกนหมวดหมู่
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## ขั้นตอนที่ 14: เพิ่มชื่อแกนหมวดหมู่

หากจำเป็น คุณยังสามารถเพิ่มชื่อสำหรับแกนหมวดหมู่ได้

```csharp
// ตั้งค่าหมวดหมู่แกนชื่อ
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

## ขั้นตอนที่ 15: การปรับแต่งเพิ่มเติม

ปรับปรุงแผนภูมิของคุณให้ดียิ่งขึ้นด้วยการปรับแต่งเพิ่มเติม เช่น คำอธิบาย สีผนัง และการตั้งค่าพื้นที่พล็อต

```csharp
// การปรับแต่งเพิ่มเติม (ทางเลือก)

// ปรับแต่งคุณสมบัติข้อความตำนาน
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// แสดงคำอธิบายแผนภูมิโดยไม่ทับซ้อนกัน
chart.Legend.Overlay = true;

// แผนภูมิการตั้งค่าสีผนังด้านหลัง
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// ตั้งค่าสีพื้นของแผนภูมิ
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// ตั้งค่าสีพื้นที่พล็อต
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// บันทึกการนำเสนอ
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## บทสรุป

ในคู่มือที่ครอบคลุมนี้ เราได้กล่าวถึงเทคนิคการปรับแต่งแผนภูมิขั้นสูงโดยใช้ Aspose.Slides สำหรับ .NET คุณจะได้เรียนรู้วิธีการสร้างงานนำเสนอ เพิ่มแผนภูมิ ปรับแต่งรูปลักษณ์ของแผนภูมิ และปรับแต่งองค์ประกอบแผนภูมิต่างๆ เช่น เส้นตาราง ป้ายแกน และคำอธิบายแผนภูมิ 

## คำถามที่พบบ่อย

### Aspose.Slides รองรับ .NET เวอร์ชันใดบ้างสำหรับ .NET?
Aspose.Slides สำหรับ .NET รองรับเวอร์ชัน .NET ต่างๆ รวมถึง .NET Framework และ .NET Core โปรดดูเอกสารประกอบเพื่อดูรายการเวอร์ชันที่รองรับทั้งหมด

### ฉันสามารถสร้างแผนภูมิจากแหล่งข้อมูล เช่น ไฟล์ Excel ได้หรือไม่
ใช่ Aspose.Slides ช่วยให้คุณสร้างแผนภูมิจากแหล่งข้อมูลภายนอก เช่น สเปรดชีต Excel โปรดดูเอกสารประกอบเพื่อดูตัวอย่างโดยละเอียด

### ฉันจะเพิ่มป้ายข้อมูลแบบกำหนดเองลงในชุดแผนภูมิของฉันได้อย่างไร
 หากต้องการเพิ่มป้ายข้อมูลที่กำหนดเอง ให้เข้าถึง`DataLabels` คุณสมบัติของซีรีส์และปรับแต่งป้ายกำกับตามต้องการ คุณสามารถดูตัวอย่างโค้ดได้ในเอกสารประกอบ

### สามารถส่งออกแผนภูมิไปยังรูปแบบอื่น เช่น PDF หรือรูปภาพได้หรือไม่
แน่นอน! Aspose.Slides ช่วยให้คุณสามารถส่งออกการนำเสนอพร้อมแผนภูมิไปยังรูปแบบต่างๆ รวมถึง PDF และรูปแบบรูปภาพ

### ฉันสามารถหาบทช่วยสอนและตัวอย่างเพิ่มเติมสำหรับ Aspose.Slides สำหรับ .NET ได้จากที่ไหน
 เยี่ยมชม Aspose.Slides[เว็บไซต์](https://reference.aspose.com/slides/net/) สำหรับบทช่วยสอน ตัวอย่างโค้ด และเอกสารประกอบที่ครอบคลุม