---
title: แปลงแผนภูมิ Excel เป็น PDF โดยใช้ Aspose.Cells สำหรับ .NET
linktitle: แปลงแผนภูมิ Excel เป็น PDF โดยใช้ Aspose.Cells สำหรับ .NET
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: เรียนรู้วิธีการแปลงแผนภูมิ Excel เป็นรูปแบบ PDF ใน .NET ได้อย่างง่ายดายโดยใช้ Aspose.Cells คำแนะนำทีละขั้นตอนของเราครอบคลุมถึงข้อกำหนดเบื้องต้น การตั้งค่า ตัวอย่างโค้ด และคำถามที่พบบ่อย
type: docs
weight: 11
url: /th/net/tutorials/cells/conversion-to-pdf-file/convert-excel-charts-to-pdf/
---
## การแนะนำ

คุณต้องการคำแนะนำในการแปลงแผนภูมิจากสเปรดชีต Excel เป็นรูปแบบ PDF ในสภาพแวดล้อม .NET หรือไม่ บทความนี้เป็นแหล่งข้อมูลครบวงจรที่ครอบคลุมทุกรายละเอียดเพื่อช่วยให้คุณเชี่ยวชาญกระบวนการด้วย Aspose.Cells สำหรับ .NET ปฏิบัติตามคำแนะนำที่มีโครงสร้างนี้เพื่อแปลงแผนภูมิ Excel เป็น PDF คุณภาพสูงได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้น

### การตั้งค่าสภาพแวดล้อม .NET
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework หรือ .NET Core แล้ว สภาพแวดล้อมทั้งสองนี้เข้ากันได้กับ Aspose.Cells ดังนั้นคุณจึงสามารถเลือกใช้สภาพแวดล้อมที่เหมาะกับโครงการของคุณได้ดีที่สุด

### การติดตั้งไลบรารี Aspose.Cells
 ไลบรารี Aspose.Cells เป็นสิ่งจำเป็นสำหรับการแปลงแผนภูมิเป็น PDF ดาวน์โหลดเวอร์ชันล่าสุดได้จาก[หน้าดาวน์โหลด Aspose](https://releases.aspose.com/cells/net/).

### ความรู้พื้นฐานเกี่ยวกับ C#
ความเข้าใจพื้นฐานเกี่ยวกับ C# จะทำให้กระบวนการเขียนโค้ดง่ายขึ้น ไม่ต้องกังวลหากคุณเป็นมือใหม่ เพราะคู่มือนี้มีตัวอย่างโค้ดที่ทำตามได้ง่าย

### การตั้งค่า Visual Studio
คุณจะต้องใช้ Visual Studio หรือ IDE ที่เข้ากันได้อื่น ตั้งค่า IDE ของคุณให้จัดการแอปพลิเคชัน .NET ตรวจสอบให้แน่ใจว่าทุกอย่างได้รับการกำหนดค่าอย่างถูกต้องเพื่อเขียนและรันโค้ดของคุณโดยไม่มีปัญหา

## นำเข้าแพ็คเกจที่จำเป็นในโครงการของคุณ

เมื่อทำตามเงื่อนไขเบื้องต้นแล้ว ให้เริ่มต้นด้วยการนำเข้าไลบรารีที่จำเป็นลงในโปรเจ็กต์ของคุณ เปิดโปรเจ็กต์ Visual Studio ของคุณและติดตั้งไลบรารี Aspose.Cells ผ่าน NuGet:

1. คลิกขวาที่โครงการของคุณใน Solution Explorer
2. เลือกจัดการแพ็คเกจ NuGet
3. ค้นหา Aspose.Cells และคลิกติดตั้ง

 เพิ่มสิ่งต่อไปนี้`using` คำสั่งที่จุดเริ่มต้นของไฟล์โค้ดของคุณ:

```csharp
using System;
using System.IO;
using Aspose.Cells;
using Aspose.Cells.Charts;
```

ไลบรารีเหล่านี้มีคลาสและวิธีการสำหรับการจัดการแผนภูมิ Excel และแปลงเป็น PDF

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีไฟล์

เริ่มต้นด้วยการระบุเส้นทางไปยังไดเร็กทอรีที่เก็บเอกสาร Excel ของคุณ ซึ่งจะแจ้งให้ Aspose.Cells ทราบว่าจะค้นหาไฟล์ .xls หรือ .xlsx ที่มีแผนภูมิของคุณได้จากที่ใด

```csharp
// กำหนดเส้นทางไดเร็กทอรี
string dataDir = "Your Document Directory Path";
```

 แทนที่`"Your Document Directory Path"` ด้วยเส้นทางจริงไปยังไฟล์ของคุณ

## ขั้นตอนที่ 2: โหลดสมุดงาน Excel

ตอนนี้โหลดไฟล์ Excel ที่มีแผนภูมิที่คุณต้องการแปลง

```csharp
// โหลดไฟล์ Excel
Workbook workbook = new Workbook(dataDir + "Sample1.xls");
```

ตรวจสอบให้แน่ใจว่าเส้นทางและชื่อไฟล์ตรงกับตำแหน่งไฟล์จริงของคุณ

## ขั้นตอนที่ 3: เข้าถึงเวิร์กชีตด้วยแผนภูมิ

เวิร์กบุ๊ก Excel สามารถมีแผ่นงานได้หลายแผ่น ดังนั้นให้ระบุแผ่นงานที่มีแผนภูมิที่คุณต้องการแปลง

```csharp
// เข้าถึงแผ่นงานที่เฉพาะเจาะจง
Worksheet worksheet = workbook.Worksheets[0];
```

รหัสนี้จะเข้าถึงเวิร์กชีตแรก เปลี่ยนดัชนีหากแผนภูมิของคุณอยู่ในชีตอื่น

## ขั้นตอนที่ 4: เลือกแผนภูมิที่จะแปลง

ขั้นตอนต่อไปคือเข้าถึงแผนภูมิเฉพาะที่คุณต้องการแปลงจากเวิร์กชีตที่เลือก

```csharp
// เข้าถึงแผนภูมิแรกในเวิร์กชีต
Chart chart = worksheet.Charts[0];
```

รหัสนี้จะเลือกแผนภูมิแรก หากมีแผนภูมิหลายรายการ ให้ปรับดัชนีให้เหมาะสม

## ขั้นตอนที่ 5: แปลงแผนภูมิเป็น PDF

ตอนนี้มาแปลงแผนภูมิที่เลือกเป็นไฟล์ PDF กัน

```csharp
// แปลงแผนภูมิเป็นรูปแบบ PDF
chart.ToPdf(dataDir + "ChartOutput.pdf");
```

คำสั่งนี้จะสั่งให้ Aspose.Cells บันทึกแผนภูมิเป็น PDF ในไดเร็กทอรีที่ระบุ

## ขั้นตอนที่ 6: บันทึกแผนภูมิเป็น PDF ในสตรีมหน่วยความจำ (ทางเลือก)

 หากคุณต้องการบันทึกแผนภูมิใน`MemoryStream` แทนที่จะใช้โค้ดโดยตรงในไฟล์ ให้ใช้โค้ดต่อไปนี้ ซึ่งมีประโยชน์อย่างยิ่งสำหรับแอปพลิเคชันบนเว็บหรือเมื่อคุณจำเป็นต้องให้บริการ PDF แบบไดนามิก

```csharp
// บันทึกแผนภูมิลงในสตรีมหน่วยความจำ
MemoryStream pdfStream = new MemoryStream();
chart.ToPdf(pdfStream);
```

 การใช้`MemoryStream` ช่วยให้คุณมีความยืดหยุ่นในการจัดการไฟล์ PDF ภายในแอปพลิเคชันของคุณ

## บทสรุป

การแปลงแผนภูมิ Excel เป็น PDF ด้วย Aspose.Cells สำหรับ .NET เป็นกระบวนการง่ายๆ เมื่อคุณทราบขั้นตอนต่างๆ ตั้งแต่การตั้งค่าสภาพแวดล้อมและการนำเข้าไลบรารีที่จำเป็นไปจนถึงการแปลงและบันทึกไฟล์ แต่ละขั้นตอนนั้นตรงไปตรงมาและง่ายต่อการนำไปใช้ ตอนนี้ คุณมีความรู้ที่จำเป็นในการสร้างไฟล์ PDF จากแผนภูมิ Excel อย่างมีประสิทธิภาพภายในแอปพลิเคชัน .NET ของคุณแล้ว

## คำถามที่พบบ่อย

### Aspose.Cells คืออะไร?

Aspose.Cells เป็นไลบรารี .NET ที่ครอบคลุมซึ่งออกแบบมาสำหรับการสร้าง จัดการ และแปลงไฟล์ Excel ในรูปแบบต่างๆ

### ฉันสามารถใช้ Aspose.Cells โดยไม่ต้องมีใบอนุญาตได้หรือไม่?

 ใช่ คุณสามารถทดลองใช้ Aspose.Cells ได้ฟรีโดยใช้เวอร์ชันทดลองใช้ที่มีใน[เว็บไซต์อาโพส](https://releases.aspose.com/cells/net/).

### ฉันควรทำอย่างไรหากพบข้อผิดพลาดระหว่างการแปลง?

 หากคุณพบปัญหาใด ๆ ให้ตรวจสอบ[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/cells/9) เพื่อขอความช่วยเหลือในการแก้ไขปัญหาหรือคำแนะนำจากผู้ใช้รายอื่น

### สามารถแปลงแผนภูมิเป็นรูปแบบอื่นด้วย Aspose.Cells ได้หรือไม่

ใช่ Aspose.Cells รองรับรูปแบบเอาต์พุตต่างๆ รวมถึงรูปภาพและ HTML นอกเหนือจาก PDF

### ฉันสามารถรับใบอนุญาตสำหรับ Aspose.Cells ได้หรือไม่?

 ใช่คุณสามารถทำได้[ซื้อใบอนุญาต](https://purchase.conholdate.com/buy) เพื่อปลดล็อคความสามารถทั้งหมดของ Aspose.Cells