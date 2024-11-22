---
title: แปลงไฟล์ MS Project เป็น PDF ด้วย Aspose.Tasks สำหรับ .NET
linktitle: ตัวเลือกการบันทึก PDF สำหรับ Aspose.Tasks
second_title: API ของ Aspose.Tasks .NET
description: เรียนรู้วิธีการแปลงไฟล์ Microsoft Project (.mpp) เป็น PDF ด้วย Aspose.Tasks สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนนี้เพื่อปรับแต่งเอาต์พุต PDF เลือกหน้าเฉพาะ และดำเนินการแปลงเป็นชุดโดยอัตโนมัติ
type: docs
weight: 13
url: /th/net/tutorials/tasks/guide-to-saving-options/convert-ms-project-files-to-pdf/
---
## การแนะนำ

การจัดการไฟล์โครงการที่มีประสิทธิภาพมีบทบาทสำคัญในกระบวนการทำงานที่มีประสิทธิภาพและความสำเร็จของโครงการ การใช้ Aspose.Tasks สำหรับ .NET ช่วยให้นักพัฒนาสามารถแปลงไฟล์ Microsoft Project เป็นรูปแบบ PDF ได้อย่างแม่นยำและยืดหยุ่น ในคู่มือนี้ เราจะแนะนำขั้นตอนทีละขั้นตอนในการบันทึกไฟล์ Microsoft Project (.mpp) เป็น PDF พร้อมด้วยตัวเลือกที่ปรับแต่งได้

## ข้อกำหนดเบื้องต้นสำหรับการใช้ Aspose.Tasks สำหรับ .NET

ก่อนที่จะดำเนินการต่อ โปรดตรวจสอบให้แน่ใจว่าได้ปฏิบัติตามข้อกำหนดเบื้องต้นต่อไปนี้:

1. Aspose.Tasks สำหรับการติดตั้ง .NET  
    ดาวน์โหลดและติดตั้งไลบรารีจาก[เว็บไซต์](https://releases.aspose.com/tasks/net/).

2. สภาพแวดล้อมการพัฒนา  
   ความรู้ในการใช้งานภาษาการเขียนโปรแกรม C# และสภาพแวดล้อมการพัฒนา .NET ที่ได้รับการกำหนดค่า

3. อินพุตไฟล์ Microsoft Project  
    มีความถูกต้อง`.mpp` ไฟล์พร้อมสำหรับการแปลง

## นำเข้าเนมสเปซที่จำเป็น

ก่อนจะทำการเข้ารหัส ให้ใส่เนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ Aspose.Tasks 

```csharp
using Aspose.Tasks;
using Aspose.Tasks.Saving;
using Aspose.Tasks.Visualization;
using System.Collections.Generic;
```

## ขั้นตอนที่ 1: โหลดไฟล์ Microsoft Project

 ในการเริ่มต้นให้โหลด`.mpp` ไฟล์เข้าใน`Project` วัตถุ. แทนที่`"Your_Project_File_Path.mpp"` พร้อมเส้นทางไปยังไฟล์อินพุตของคุณ

```csharp
var project = new Project("Your_Project_File_Path.mpp");
```

## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการบันทึก PDF

ตั้งค่าตัวเลือกเพื่อปรับแต่งเอาต์พุต PDF Aspose.Tasks สำหรับ .NET ให้ความยืดหยุ่นในการควบคุมการแสดงผลหน้า เค้าโครง และด้านอื่นๆ

```csharp
var options = new PdfSaveOptions
{
    RenderToSinglePage = false, // ไม่ว่าจะแสดงเนื้อหาทั้งหมดในหน้าเดียว
    Pages = new List<int>()     // หน้าที่จะรวมอยู่ใน PDF
};
```

## ขั้นตอนที่ 3: กำหนดจำนวนหน้า

 ใช้`PageCount` คุณสมบัติเพื่อระบุว่าโครงการครอบคลุมกี่หน้า ซึ่งจะช่วยตัดสินใจว่าจะรวมหน้าเฉพาะหรือส่งออกทั้งหมด

```csharp
Console.WriteLine("Total Pages: " + options.PageCount);
```

## ขั้นตอนที่ 4: เลือกหน้าเฉพาะสำหรับการส่งออก (ทางเลือก)

 ระบุหน้าที่แน่นอนที่จะรวมอยู่ใน PDF โดยกรอก`Pages` คุณสมบัติ ตัวอย่างเช่น การส่งออกหน้า 1 และ 4:

```csharp
options.Pages.Add(1);
options.Pages.Add(4);
```

## ขั้นตอนที่ 5: บันทึกไฟล์โครงการเป็น PDF

 สุดท้ายนี้ให้บันทึก`.mpp` ไฟล์เป็น PDF โดยเรียก`Save` วิธีการ ระบุเส้นทางไฟล์เอาท์พุตและส่งตัวเลือกที่กำหนดค่าไว้

```csharp
project.Save("Output_PDF_File_Path.pdf", options);
```

## บทสรุป

การแปลงไฟล์ Microsoft Project เป็น PDF โดยใช้ Aspose.Tasks สำหรับ .NET ช่วยให้ประสบการณ์การใช้งานราบรื่นและปรับแต่งได้ ตั้งแต่การเลือกหน้าเฉพาะไปจนถึงการส่งออกข้อมูลแบบแบตช์อัตโนมัติ เครื่องมือนี้ช่วยให้ผู้พัฒนาสามารถจัดการไฟล์โครงการได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะของ PDF ที่ส่งออกได้หรือไม่
ใช่ Aspose.Tasks อนุญาตให้ปรับแต่งแบบอักษร สี และเค้าโครงหน้าให้ตรงตามความต้องการเฉพาะของคุณได้

###  สามารถแปลงได้ไหม`.mpp` files from older versions of Microsoft Project?
 Aspose.Tasks รองรับ`.mpp` ไฟล์จาก Microsoft Project 2003 เป็นต้นไป

### ฉันจะแสดงข้อมูลโครงการทั้งหมดบนหน้า PDF เดียวได้อย่างไร
 ตั้งค่า`RenderToSinglePage` ทรัพย์สินของ`PdfSaveOptions` คัดค้าน`true`.

```csharp
options.RenderToSinglePage = true;
```

### ฉันสามารถส่งออกข้อมูลโครงการไปยังรูปแบบไฟล์อื่นได้หรือไม่
ใช่ Aspose.Tasks รองรับการส่งออกเป็นรูปแบบต่างๆ รวมถึง Excel, HTML และรูปแบบภาพเช่น PNG และ JPEG

### มี Aspose.Tasks สำหรับ .NET ให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดได้[เวอร์ชันทดลองใช้ฟรีที่นี่](https://releases.aspose.com/).