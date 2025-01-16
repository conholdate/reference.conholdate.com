---
title: ตัวเลือกเครื่องหมายแผนภูมิบนจุดข้อมูลใน Aspose.Slides .NET
linktitle: ตัวเลือกเครื่องหมายแผนภูมิบนจุดข้อมูลใน Aspose.Slides .NET
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: เรียนรู้วิธีปรับปรุงแผนภูมิ PowerPoint ของคุณด้วยตัวเลือกเครื่องหมายที่กำหนดเองโดยใช้ Aspose.Slides สำหรับ .NET คำแนะนำทีละขั้นตอนนี้ครอบคลุมถึงข้อกำหนดเบื้องต้น การสร้างแผนภูมิ การจัดรูปแบบจุดข้อมูล และอื่นๆ อีกมากมาย
type: docs
weight: 11
url: /th/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## การแนะนำ

การนำเครื่องมือช่วยสร้างภาพมาใช้ในงานนำเสนอถือเป็นสิ่งสำคัญสำหรับการสื่อสารที่มีประสิทธิภาพ Aspose.Slides สำหรับ .NET มอบเครื่องมือที่มีประสิทธิภาพสำหรับการสร้างและปรับแต่งแผนภูมิ ช่วยให้นักพัฒนาสามารถปรับปรุงการนำเสนอข้อมูลของตนได้ หนึ่งในคุณสมบัติที่โดดเด่นคือความสามารถในการใช้ตัวเลือกเครื่องหมายแผนภูมิกับจุดข้อมูล ช่วยให้ปรับแต่งแผนภูมิให้ดูเป็นมืออาชีพได้อย่างแม่นยำ บทความนี้จะแนะนำคุณเกี่ยวกับทุกขั้นตอนที่จำเป็นเพื่อให้บรรลุสิ่งนี้

## ข้อกำหนดเบื้องต้น

ก่อนที่จะดำเนินการต่อ โปรดตรวจสอบสิ่งต่อไปนี้:

-  ติดตั้ง Aspose.Slides สำหรับ .NET: ดาวน์โหลดจาก[ที่นี่](https://releases.aspose.com/slides/net/).
- การตั้งค่าพื้นฐาน: ไฟล์การนำเสนอ เช่น "Test.pptx" ในไดเร็กทอรีการทำงานของคุณ
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือเทียบเท่า กำหนดค่าสำหรับ .NET

## การนำเข้าเนมสเปซที่จำเป็น

เพิ่มเนมสเปซที่จำเป็นให้กับโครงการของคุณเพื่อการพัฒนาที่ราบรื่น:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## ขั้นตอนที่ 1: สร้างแผนภูมิในงานนำเสนอของคุณ

เริ่มต้นด้วยการสร้างแผนภูมิเริ่มต้นบนสไลด์แรกของการนำเสนอของคุณ:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 นี่เพิ่ม`LineWithMarkers` แผนภูมิไปยังสไลด์ของคุณพร้อมขนาดที่ระบุ

## ขั้นตอนที่ 2: ดึงดัชนีแผ่นงานข้อมูลแผนภูมิ

ดัชนีเวิร์กชีตข้อมูลแผนภูมิเริ่มต้นมีความจำเป็นสำหรับการปรับแต่งเพิ่มเติม:

```csharp
int defaultWorksheetIndex = 0;
```

## ขั้นตอนที่ 3: เข้าถึงสมุดงานข้อมูลแผนภูมิ

ในการจัดการข้อมูลแผนภูมิ ให้ดึงสมุดงานที่เกี่ยวข้อง:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## ขั้นตอนที่ 4: กำหนดค่าชุดแผนภูมิและเพิ่มจุดข้อมูล

ล้างซีรีส์เริ่มต้นและเพิ่มจุดข้อมูลใหม่สำหรับซีรีส์ของคุณ:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// เพิ่มจุดข้อมูลลงในชุดข้อมูล
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## ขั้นตอนที่ 5: ใช้การเติมรูปภาพกับเครื่องหมายจุดข้อมูล

รูปภาพที่กำหนดเองสามารถทำให้เครื่องหมายข้อมูลดูน่าสนใจได้:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// ตั้งค่ารูปภาพที่กำหนดเองสำหรับเครื่องหมาย
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## ขั้นตอนที่ 6: ปรับแต่งขนาดเครื่องหมาย

ปรับเปลี่ยนขนาดของเครื่องหมายเพื่อเพิ่มการมองเห็น:

```csharp
series.Marker.Size = 20;
```

## ขั้นตอนที่ 7: บันทึกการนำเสนอที่อัปเดต

บันทึกการนำเสนอที่กำหนดเองไปยังตำแหน่งที่คุณต้องการ:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## บทสรุป

Aspose.Slides สำหรับ .NET ช่วยให้ผู้พัฒนามีเครื่องมือในการสร้างแผนภูมิระดับมืออาชีพพร้อมตัวเลือกการปรับแต่งที่หลากหลาย ด้วยการใช้ประโยชน์จากตัวเลือกตัวระบุแผนภูมิ คุณสามารถปรับปรุงความน่าสนใจและความคมชัดของการนำเสนอของคุณได้อย่างมาก คำแนะนำทีละขั้นตอนนี้ช่วยให้การปรับแต่งที่ซับซ้อนนั้นง่ายต่อการนำไปใช้

## คำถามที่พบบ่อย

### ฉันสามารถใช้รูปแบบภาพใด ๆ เพื่อปรับแต่งเครื่องหมายได้หรือไม่
ใช่ Aspose.Slides รองรับรูปแบบภาพต่างๆ รวมถึง JPEG, PNG และ BMP เพื่อการปรับแต่งเครื่องหมาย

### ฉันจะเปลี่ยนประเภทแผนภูมิหลังจากสร้างได้อย่างไร?
 หากต้องการเปลี่ยนประเภทแผนภูมิ ให้เข้าถึง`chart.Type` ทรัพย์สินและมอบหมายให้แตกต่างกัน`ChartType`.

### Aspose.Slides สำหรับ .NET เข้ากันได้กับ PowerPoint เวอร์ชันเก่ากว่าหรือไม่
ใช่ รองรับความเข้ากันได้ย้อนหลังกับรูปแบบ PowerPoint รุ่นเก่า ช่วยให้มีความคล่องตัว

### ฉันสามารถอัพเดตข้อมูลแผนภูมิแบบไดนามิกได้หรือไม่
 แน่นอน ใช้`IChartDataWorkbook` เพื่ออัปเดตข้อมูลแผนภูมิโดยโปรแกรม

### ฉันสามารถหาแหล่งข้อมูลเพิ่มเติมได้จากที่ไหน
 สำรวจ[เอกสารประกอบ Aspose.Slides](https://reference.aspose.com/slides/net/)หรือเข้าร่วม[ฟอรั่มชุมชน](https://forum.aspose.com/) เพื่อรองรับ