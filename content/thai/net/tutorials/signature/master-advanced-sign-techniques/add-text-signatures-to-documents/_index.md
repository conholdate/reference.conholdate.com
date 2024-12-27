---
title: เพิ่มลายเซ็นข้อความลงในเอกสารโดยใช้ GroupDocs.Signature
linktitle: เพิ่มลายเซ็นข้อความลงในเอกสาร
second_title: API ของ GroupDocs.Signature .NET
description: เรียนรู้วิธีลงนามในเอกสารด้วยข้อความโดยใช้ GroupDocs.Signature สำหรับ .NET คำแนะนำทีละขั้นตอนสำหรับการเพิ่มลายเซ็นข้อความด้วยโปรแกรม
type: docs
weight: 17
url: /th/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## การแนะนำ

ในภูมิทัศน์ดิจิทัลของปัจจุบัน การลงนามในเอกสารอิเล็กทรอนิกส์ได้กลายมาเป็นสิ่งจำเป็นสำหรับการปรับปรุงกระบวนการทำงานและประหยัดทรัพยากร GroupDocs.Signature สำหรับ .NET มอบโซลูชันอันทรงพลังสำหรับการเพิ่มลายเซ็นข้อความในรูปแบบเอกสารต่างๆ ด้วยโปรแกรม บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับขั้นตอนต่างๆ ในการลงนามในเอกสารด้วยข้อความโดยใช้ GroupDocs.Signature สำหรับ .NET

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. GroupDocs.Signature สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/signature/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ของคุณ
3. เอกสาร: เตรียมเอกสารที่คุณต้องการลงนาม (เช่น PDF, Word)

## การนำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโครงการ .NET ของคุณ:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## ขั้นตอนที่ 1: โหลดเอกสาร

เริ่มต้นด้วยการโหลดเอกสารที่คุณต้องการลงนาม:

```csharp
string filePath = "sample.pdf"; // เส้นทางไปยังเอกสารของคุณ
string fileName = Path.GetFileName(filePath);
```

## ขั้นตอนที่ 2: กำหนดเส้นทางไฟล์เอาท์พุต

ขั้นตอนต่อไปคือตั้งค่าเส้นทางไฟล์เอาท์พุตที่จะบันทึกเอกสารที่ลงนาม:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## ขั้นตอนที่ 3: สร้างตัวเลือกลายเซ็น

กำหนดค่าตัวเลือกสำหรับลายเซ็นข้อความของคุณ รวมถึงเนื้อหา ตำแหน่ง ขนาด สี และรูปแบบอักษร:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // ตำแหน่ง X
    Top = 200, // ตำแหน่ง Y
    Width = 100, // ความกว้างของลายเซ็น
    Height = 30, // ความสูงของลายเซ็น
    ForeColor = Color.Red, // สีข้อความ
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // การตั้งค่าแบบอักษร
};
```

## ขั้นตอนที่ 4: ลงนามในเอกสาร

สุดท้าย ให้ใช้ GroupDocs.Signature เพื่อใช้ลายเซ็นข้อความและบันทึกเอกสารที่ลงนามแล้ว:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // ลงนามในเอกสาร
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## บทสรุป

ในบทช่วยสอนนี้ เราได้สาธิตวิธีการเพิ่มลายเซ็นข้อความลงในเอกสารโดยใช้โปรแกรม GroupDocs.Signature สำหรับ .NET คุณสามารถปรับปรุงความปลอดภัยและความถูกต้องของเอกสารได้อย่างมีประสิทธิภาพโดยทำตามขั้นตอนเหล่านี้

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของลายเซ็นข้อความได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณลักษณะต่างๆ เช่น สี แบบอักษร ขนาด และตำแหน่งของลายเซ็นข้อความให้เหมาะกับความต้องการของคุณได้

### GroupDocs.Signature เข้ากันได้กับรูปแบบเอกสารหลาย ๆ รูปแบบหรือไม่
แน่นอน! GroupDocs.Signature รองรับรูปแบบต่างๆ มากมาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย

### ฉันสามารถเพิ่มลายเซ็นข้อความหลายรายการลงในเอกสารเดียวได้หรือไม่
ใช่ คุณสามารถเพิ่มลายเซ็นข้อความหลายรายการได้ โดยแต่ละรายการมีตัวเลือกการปรับแต่งของตัวเอง

### GroupDocs.Signature รับประกันความสมบูรณ์ของเอกสารหลังการลงนามหรือไม่
ใช่ ห้องสมุดใช้อัลกอริทึมการเข้ารหัสที่แข็งแกร่งเพื่อให้แน่ใจว่าเอกสารมีความสมบูรณ์และป้องกันการปลอมแปลงหลังการลงนาม

### มีเวอร์ชันทดลองใช้งานเพื่อทดสอบก่อนซื้อหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/) เพื่อสำรวจคุณสมบัติต่างๆ ก่อนตัดสินใจซื้อ