---
title: คัดลอกข้อมูลภายในเวิร์กบุ๊ก Excel โดยใช้ Aspose.Cells สำหรับ .NET
linktitle: คัดลอกข้อมูลภายในเวิร์กบุ๊ก Excel โดยใช้ Aspose.Cells สำหรับ .NET
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: เรียนรู้วิธีการคัดลอกข้อมูลภายในเวิร์กบุ๊ก Excel อย่างมีประสิทธิภาพโดยใช้ Aspose.Cells สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนนี้เพื่อทำซ้ำแผ่นงาน ถ่ายโอนข้อมูล และจัดการไฟล์ Excel ได้อย่างง่ายดาย
type: docs
weight: 12
url: /th/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## การแนะนำ

ในคู่มือโดยละเอียดนี้ เราจะสาธิตวิธีการคัดลอกข้อมูลภายในเวิร์กบุ๊กเดียวกันโดยใช้ Aspose.Cells สำหรับ .NET โดยปฏิบัติตามคำแนะนำทีละขั้นตอนที่ระบุไว้ด้านล่าง คุณจะเรียนรู้วิธีการทำสำเนาแผ่นงานโดยการเขียนโปรแกรม การเก็บรักษาเนื้อหา และการจัดรูปแบบ

## ข้อกำหนดเบื้องต้นสำหรับการคัดลอกข้อมูลใน Excel ด้วย Aspose.Cells

ก่อนที่จะเริ่มเขียนโค้ด ตรวจสอบให้แน่ใจก่อนว่าคุณจัดเตรียมทุกอย่างเรียบร้อยแล้ว:

1. ไลบรารี Aspose.Cells สำหรับ .NET: คุณต้องติดตั้งไลบรารี Aspose.Cells สำหรับ .NET คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[หน้าดาวน์โหลด Aspose.Cells สำหรับ .NET](https://releases.aspose.com/cells/net/).
2. สภาพแวดล้อมการพัฒนา: ต้องใช้ IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio สำหรับการเขียนและรันโค้ดของคุณ
3.  ใบอนุญาต Aspose: คุณสามารถใช้ใบอนุญาตแบบทดลองใช้งานฟรีหรือใบอนุญาตแบบซื้อได้ สำหรับข้อมูลเพิ่มเติม โปรดไปที่[ที่นี่](https://purchase.aspose.com/temporary-license/).

เมื่อกำหนดข้อกำหนดเบื้องต้นเรียบร้อยแล้ว คุณก็พร้อมที่จะเริ่มทำงานกับไลบรารีได้

## การนำเข้าแพ็คเกจที่จำเป็น

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่เกี่ยวข้องจาก Aspose.Cells วิธีนี้ช่วยให้คุณสามารถทำงานกับไฟล์ Excel โดยใช้คลาสและวิธีการที่ Aspose.Cells จัดเตรียมไว้

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 เนมสเปซเหล่านี้จะทำให้คุณสามารถเข้าถึง`Workbook` คลาส (สำหรับการทำงานกับไฟล์ Excel) และ`WorksheetCollection` (สำหรับการเข้าถึงแผ่นงานหลายแผ่นภายในสมุดงาน)

## ขั้นตอนที่ 1: เริ่มต้นเส้นทางไฟล์สำหรับเวิร์กบุ๊ก

หากต้องการให้โค้ดของคุณเป็นระเบียบ คุณจะต้องกำหนดเส้นทางไฟล์ที่เวิร์กบุ๊กของคุณตั้งอยู่และตำแหน่งที่คุณต้องการบันทึกไฟล์ที่แก้ไขแล้ว ต่อไปนี้คือวิธีระบุเส้นทาง:

```csharp
// กำหนดเส้นทางไดเร็กทอรีที่ไฟล์ Excel ตั้งอยู่
string dataDir = "Your Directory Path";

// กำหนดเส้นทางแบบเต็มไปยังเวิร์กบุ๊กอินพุต
string inputPath = dataDir + "book1.xls";
```

 แทนที่`"Your Directory Path"` ด้วยเส้นทางจริงไปยังไดเร็กทอรีของคุณที่มีเวิร์กบุ๊ก ซึ่งช่วยให้มั่นใจได้ว่าโค้ดมีความยืดหยุ่นและคุณสามารถจัดการเส้นทางได้อย่างมีประสิทธิภาพ

## ขั้นตอนที่ 2: เปิดเวิร์กบุ๊กเพื่อเข้าถึงข้อมูล

 เมื่อกำหนดเส้นทางไฟล์แล้ว ขั้นตอนต่อไปคือการโหลดเวิร์กบุ๊ก Excel ลงใน`Workbook` วัตถุ ซึ่งช่วยให้คุณสามารถเข้าถึงเนื้อหาเพื่อการจัดการได้

```csharp
// โหลดไฟล์ Excel ลงในวัตถุเวิร์กบุ๊ก
Workbook wb = new Workbook(inputPath);
```

 ด้วยบรรทัดนี้คุณได้โหลดสำเร็จแล้ว`book1.xls` เข้าไปใน`wb` วัตถุทำให้สามารถเข้าถึงข้อมูลได้

## ขั้นตอนที่ 3: เข้าถึงคอลเลกชันแผ่นงาน

 เมื่อโหลดเวิร์กบุ๊กแล้ว คุณสามารถเข้าถึงแผ่นงานที่อยู่ในนั้นได้ Aspose.Cells จัดเตรียม`Worksheets`คอลเลกชันที่ช่วยให้คุณโต้ตอบกับแต่ละเวิร์กชีตในเวิร์กบุ๊กได้

```csharp
// ดึงคอลเลกชันแผ่นงานจากสมุดงาน
WorksheetCollection sheets = wb.Worksheets;
```

 การ`sheets` วัตถุตอนนี้ช่วยให้คุณเข้าถึงแผ่นงานทั้งหมดภายใน`book1.xls`และคุณสามารถดำเนินการต่างๆ กับข้อมูลเหล่านั้นได้ รวมถึงการคัดลอกข้อมูลจากแผ่นงานหนึ่งไปยังอีกแผ่นงานหนึ่ง

## ขั้นตอนที่ 4: คัดลอกข้อมูลจากแผ่นงานหนึ่งไปยังอีกแผ่นงานหนึ่ง

 ในการคัดลอกข้อมูลจากเวิร์กชีตหนึ่งไปยังอีกเวิร์กบุ๊กหนึ่งภายในเวิร์กบุ๊กเดียวกัน Aspose.Cells เสนอวิธีการที่ใช้งานง่ายที่เรียกว่า`AddCopy`วิธีการนี้จะสร้างสำเนาของเวิร์กชีตที่ระบุและผนวกเข้าในเวิร์กบุ๊ก

```csharp
// คัดลอกข้อมูลจาก "แผ่นงาน 1" ไปยังแผ่นงานใหม่ภายในเวิร์กบุ๊ก
sheets.AddCopy("Sheet1");
```

 ในตัวอย่างนี้ เรากำลังคัดลอกข้อมูลจาก "Sheet1" ไปยังชีตใหม่`AddCopy` วิธีการนี้จะทำซ้ำแผ่นงานทั้งหมดโดยรักษาเนื้อหาทั้งหมดไว้ รวมถึงสูตร การจัดรูปแบบ และค่า

## ขั้นตอนที่ 5: บันทึกสมุดงานที่แก้ไขแล้ว

 หลังจากคัดลอกข้อมูลแล้ว คุณสามารถบันทึกเวิร์กบุ๊กที่แก้ไขด้วยชื่อหรือตำแหน่งใหม่ได้ ซึ่งทำได้โดยเรียกใช้`Save`วิธีการบน`Workbook` วัตถุ.

```csharp
//บันทึกสมุดงานที่แก้ไขด้วยชื่อใหม่
wb.Save(dataDir + "book1_copy.xls");
```

 การดำเนินการนี้จะบันทึกสมุดงานพร้อมแผ่นงานที่คัดลอกเป็น`book1_copy.xls` ในไดเร็กทอรีที่ระบุ คุณสามารถเปลี่ยนชื่อไฟล์และเส้นทางตามความต้องการของคุณได้

## บทสรุป

การคัดลอกข้อมูลภายในเวิร์กบุ๊ก Excel โดยใช้ Aspose.Cells สำหรับ .NET เป็นงานที่ง่าย และคู่มือนี้ให้ขั้นตอนที่จำเป็นในการดำเนินการอย่างมีประสิทธิภาพ ไม่ว่าคุณจะทำซ้ำแผ่นงานทั้งหมดหรือช่วงข้อมูลเฉพาะ Aspose.Cells ก็มี API ที่แข็งแกร่งและยืดหยุ่นที่ทำให้การทำงานอัตโนมัติของ Excel เป็นเรื่องง่ายและมีประสิทธิภาพ

## คำถามที่พบบ่อย

### ฉันสามารถคัดลอกแผ่นงานหลายแผ่นในครั้งเดียวได้ไหม?

Aspose.Cells ไม่รองรับการคัดลอกชีตหลายชีตในครั้งเดียว อย่างไรก็ตาม คุณสามารถวนซ้ำผ่านชีตที่คุณต้องการคัดลอกและคัดลอกทีละชีตได้

### ฉันจะเปลี่ยนชื่อแผ่นงานที่คัดลอกได้อย่างไร

หลังจากการคัดลอกแผ่นงานแล้ว คุณสามารถเปลี่ยนชื่อได้ดังนี้:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells เข้ากันได้กับ .NET Core ได้หรือไม่

ใช่ Aspose.Cells เข้ากันได้ดีกับสภาพแวดล้อมทั้ง .NET Framework และ .NET Core

### Aspose.Cells จัดการการจัดรูปแบบระหว่างการคัดลอกอย่างไร

 การ`AddCopy`วิธีการนี้จะรักษาเนื้อหาและการจัดรูปแบบทั้งหมดเมื่อคัดลอกแผ่นงาน ทำให้แน่ใจว่าข้อมูลที่คัดลอกมีลักษณะเหมือนกับต้นฉบับทุกประการ

### ฉันสามารถคัดลอกแผ่นงานไปยังสมุดงานอื่นได้หรือไม่

 ใช่ คุณสามารถคัดลอกแผ่นงานไปยังสมุดงานอื่นได้โดยใช้`Copy` วิธีการที่มีการอ้างอิงถึงสมุดงานเป้าหมาย

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```