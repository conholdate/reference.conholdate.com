---
title: การเพิ่มส่วนประกอบของปุ่มด้วย GroupDocs.Annotation สำหรับ .NET
linktitle: การเพิ่มส่วนประกอบของปุ่ม
second_title: API ของ GroupDocs.Annotation .NET
description: ค้นพบวิธีการยกระดับเอกสาร PDF ของคุณโดยการเพิ่มส่วนประกอบปุ่มแบบโต้ตอบโดยใช้ GroupDocs.Annotation สำหรับ .NET บทช่วยสอนแบบทีละขั้นตอนนี้
type: docs
weight: 10
url: /th/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## การแนะนำ

ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนง่ายๆ ในการเพิ่มส่วนประกอบปุ่มลงในเอกสาร PDF โดยใช้ไลบรารี GroupDocs.Annotation สำหรับ .NET เมื่ออ่านคู่มือนี้จบ คุณจะพร้อมที่จะปรับปรุงเอกสาร PDF ของคุณด้วยคุณลักษณะแบบโต้ตอบ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมโดยติดตั้ง .NET framework

## ขั้นตอนที่ 1: นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโครงการของคุณ:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## ขั้นตอนที่ 2: เริ่มต้นเส้นทางเอาต์พุต

กำหนดเส้นทางเอาต์พุตที่จะบันทึก PDF ที่แก้ไขแล้ว:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ขั้นตอนที่ 3: เพิ่มส่วนประกอบปุ่ม

ตอนนี้มาสร้างและเพิ่มส่วนประกอบปุ่มลงใน PDF ของคุณกัน:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // ตำแหน่งและขนาดของปุ่ม
        PenColor = 65535,                       // สีเส้นขอบปุ่ม
        Style = BorderStyle.Dashed,             // สไตล์ขอบ
        BorderWidth = 0,                        // ความกว้างของเส้นขอบ
        BorderColor = 0,                        // สีเส้นขอบ
        AlternateName = "Name",                 // ชื่ออื่นสำหรับปุ่ม
        PartialName = "Partial Name",           // ชื่อบางส่วนของปุ่ม
        NormalCaption = "Caption",               // ข้อความที่แสดงบนปุ่ม
        ButtonColor = 16761035,                 // สีพื้นหลังของปุ่ม
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // เพิ่มปุ่มลงในคำอธิบายประกอบ
    annotator.Save("result.pdf"); // บันทึก PDF ที่แก้ไขแล้ว
}
```

## ขั้นตอนที่ 4: แสดงเส้นทางเอาท์พุต

สุดท้าย แจ้งให้ผู้ใช้ทราบว่าไฟล์เอาต์พุตถูกบันทึกอยู่ที่ไหน:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

ขอแสดงความยินดี! คุณได้เพิ่มส่วนประกอบปุ่มลงในเอกสาร PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET สำเร็จแล้ว

## บทสรุป

ในบทช่วยสอนนี้ เราได้สาธิตวิธีการรวมส่วนประกอบของปุ่มเข้ากับเอกสาร PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET หากทำตามขั้นตอนเหล่านี้ คุณจะปรับปรุงการโต้ตอบของเอกสาร PDF ได้อย่างมีนัยสำคัญ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของปุ่มได้ไหม

แน่นอน! คุณสามารถปรับเปลี่ยนคุณสมบัติต่างๆ เช่น ขนาด สี และรูปแบบให้เหมาะกับความต้องการของคุณได้

### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับ PDF ทุกเวอร์ชันหรือไม่

ใช่ GroupDocs.Annotation สำหรับ .NET รองรับ PDF เวอร์ชันต่างๆ มากมาย ช่วยให้มั่นใจได้ว่าจะเข้ากันได้กับเอกสารส่วนใหญ่

### ฉันสามารถเพิ่มส่วนประกอบปุ่มหลายรายการลงในเอกสาร PDF เดียวได้หรือไม่

ใช่ คุณสามารถเพิ่มส่วนประกอบปุ่มได้มากเท่าที่ต้องการในเอกสาร PDF

### GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบไฟล์อื่น ๆ หรือไม่

ใช่ รองรับรูปแบบเอกสารต่างๆ รวมถึง DOCX, PPTX และ XLSX นอกเหนือจาก PDF

### มีเวอร์ชันทดลองใช้สำหรับการทดสอบหรือไม่

 ใช่ คุณสามารถเข้าถึงรุ่นทดลองใช้งานฟรีของ GroupDocs.Annotation สำหรับ .NET ได้จาก[ที่นี่](https://releases.groupdocs.com/).
