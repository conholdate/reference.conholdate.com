---
title: การเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF
linktitle: การเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF
second_title: API ของ GroupDocs.Annotation .NET
description: ค้นพบวิธีการเพิ่มความสมบูรณ์ให้กับเอกสาร PDF ของคุณโดยการเพิ่มส่วนประกอบของกล่องกาเครื่องหมายแบบโต้ตอบโดยใช้ GroupDocs.Annotation สำหรับ .NET SDK บทช่วยสอนที่ครอบคลุมนี้ให้คำแนะนำทีละขั้นตอนที่ชัดเจน
type: docs
weight: 11
url: /th/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## การแนะนำ

ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET SDK ฟีเจอร์นี้ช่วยให้คุณปรับปรุงเอกสาร PDF ของคุณด้วยองค์ประกอบแบบโต้ตอบ ทำให้เอกสารน่าสนใจยิ่งขึ้นสำหรับผู้ใช้

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  GroupDocs.Annotation สำหรับ .NET SDK: ดาวน์โหลดจาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET บนเครื่องของคุณ

## ขั้นตอนที่ 1: นำเข้าเนมสเปซที่จำเป็น

ขั้นแรก ให้รวมเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## ขั้นตอนที่ 2: กำหนดเส้นทางเอาต์พุต

ระบุตำแหน่งที่จะบันทึกเอกสาร PDF ที่แก้ไข:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ขั้นตอนที่ 3: เริ่มต้น Annotator

 สร้างอินสแตนซ์ของ`Annotator` คลาสที่มีเส้นทางไปยังเอกสาร PDF อินพุตของคุณ:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## ขั้นตอนที่ 4: สร้างส่วนประกอบกล่องกาเครื่องหมาย

ตอนนี้มาสร้างและปรับแต่งส่วนประกอบกล่องกาเครื่องหมายกัน:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // กำหนดตำแหน่งและขนาด
    PenColor = 65535, // ตั้งค่าสี (ในกรณีนี้คือสีเหลือง)
    Style = BoxStyle.Star, // เลือกสไตล์สำหรับกล่องกาเครื่องหมาย
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## ขั้นตอนที่ 5: เพิ่มช่องกาเครื่องหมายลงในเอกสาร

เพิ่มส่วนประกอบกล่องกาเครื่องหมายที่สร้างขึ้นลงใน PDF:

```csharp
annotator.Add(checkBox);
```

## ขั้นตอนที่ 6: บันทึกเอกสารที่แก้ไข

บันทึกเอกสาร PDF ที่อัปเดตโดยใส่ช่องกาเครื่องหมายไว้ด้วย:

```csharp
annotator.Save("result.pdf");
```

## ขั้นตอนที่ 7: แสดงเส้นทางเอาต์พุต

สุดท้าย แจ้งให้ผู้ใช้ทราบว่าเอกสารที่แก้ไขถูกบันทึกไว้ที่ไหน:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้เพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF สำเร็จแล้วโดยใช้ GroupDocs.Annotation สำหรับ .NET ฟังก์ชันนี้ช่วยให้คุณสร้าง PDF แบบโต้ตอบได้ ซึ่งจะช่วยปรับปรุงประสบการณ์และการมีส่วนร่วมของผู้ใช้

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะของช่องกาเครื่องหมายได้ไหม

แน่นอน! คุณสามารถปรับเปลี่ยนคุณสมบัติต่างๆ เช่น สี สไตล์ และขนาด เพื่อให้ตรงตามความต้องการเฉพาะของคุณได้

### GroupDocs.Annotation สำหรับ .NET เหมาะสำหรับการใช้งานเชิงพาณิชย์หรือไม่

ใช่ GroupDocs.Annotation สำหรับ .NET ให้ใบอนุญาตเชิงพาณิชย์สำหรับธุรกิจ

### ฉันสามารถทดลองใช้ GroupDocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่

 ใช่ มีรุ่นทดลองใช้งานฟรี คุณสามารถเข้าถึงได้[ที่นี่](https://releases.groupdocs.com/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน

 การสนับสนุนและทรัพยากรเพิ่มเติมมีให้บริการบน[ฟอรั่ม GroupDocs](https://forum.groupdocs.com/c/annotation/10).

### ฉันต้องมีใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการทดสอบหรือไม่?

 คุณสามารถขอใบอนุญาตชั่วคราวเพื่อการทดสอบได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).