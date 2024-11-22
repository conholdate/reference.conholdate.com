---
title: คู่มือการใช้ภาพจากสตรีมใน OCR Image Recognition
linktitle: คู่มือการใช้ภาพจากสตรีมใน OCR Image Recognition
second_title: API ของ Aspose.OCR .NET
description: บทความนี้จะแนะนำคุณเกี่ยวกับกระบวนการจดจำข้อความจากรูปภาพโดยใช้สตรีม เพื่อให้แน่ใจว่าสามารถบูรณาการกับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น เหมาะสำหรับนักพัฒนาที่มีทักษะทุกระดับ
type: docs
weight: 12
url: /th/net/tutorials/ocr/master-image-and-drawing-recognition/guide-to-image-from-stream/
---
## การแนะนำ

ยินดีต้อนรับสู่โลกอันน่าตื่นตาตื่นใจของการจดจำอักขระด้วยแสง (OCR) โดยใช้ Aspose.OCR สำหรับ .NET ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเป็นผู้ใช้เทคโนโลยี OCR มือใหม่ คู่มือนี้จะพาคุณผ่านกระบวนการจดจำข้อความจากภาพโดยใช้สตรีมอย่างง่ายดาย Aspose.OCR สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ออกแบบมาเพื่อการผสานรวมเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น ทำให้การแยกข้อความจากภาพเป็นเรื่องง่าย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มดำเนินการ ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.  Aspose.OCR สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[เอกสาร Aspose.OCR สำหรับ .NET](https://reference.aspose.com/ocr/net/).
2. ภาพตัวอย่าง: เตรียมภาพตัวอย่าง (เราจะใช้ "sample.png") ที่คุณต้องการจดจำ ตรวจสอบให้แน่ใจว่าภาพนั้นชัดเจนและอ่านออกได้เพื่อผลลัพธ์ OCR ที่ดีที่สุด

## นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นไว้ที่ด้านบนของไฟล์ C# ของคุณ:

```csharp
using System;
using System.IO;
using Aspose.OCR;
```

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสาร

กำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณดังนี้:

```csharp
// ตั้งค่าเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "Your Document Directory"; // แทนที่ด้วยเส้นทางจริง
```

ตรวจสอบให้แน่ใจว่าชี้สิ่งนี้ไปยังตำแหน่งจริงของ "sample.png"

## ขั้นตอนที่ 2: เริ่มต้นอินสแตนซ์ Aspose.OCR

 สร้างอินสแตนซ์ของ`AsposeOcr` คลาสสำหรับการเข้าถึงฟังก์ชัน OCR:

```csharp
// เริ่มต้นอินสแตนซ์ AsposeOcr
AsposeOcr api = new AsposeOcr();
```

## ขั้นตอนที่ 3: จดจำภาพจากสตรีม

 ต่อไปเรามารู้จักข้อความจากรูปภาพกันก่อน เราจะเปิดไฟล์รูปภาพขึ้นมาใช้`MemoryStream`แล้วจึงเรียกใช้วิธีการจดจำ:

```csharp
// การจดจำภาพ
using (MemoryStream ms = new MemoryStream())
using (FileStream file = new FileStream(Path.Combine(dataDir, "sample.png"), FileMode.Open, FileAccess.Read))
{
    file.CopyTo(ms);
    var result = api.RecognizeImage(ms);
    
    // แสดงข้อความที่รู้จัก
    Console.WriteLine("Recognized Text: " + result);
}
```

โค้ดสั้นๆ นี้จะอ่านรูปภาพลงในสตรีมหน่วยความจำและประมวลผล แล้วส่งคืนข้อความที่ได้รับการยอมรับ

## ขั้นตอนที่ 4: การแจ้งเตือนความสำเร็จ

ยืนยันว่ากระบวนการเสร็จสมบูรณ์:

```csharp
Console.WriteLine("Image recognition executed successfully.");
```

## บทสรุป

ขอแสดงความยินดี! คุณได้ใช้ประโยชน์จากความสามารถของ Aspose.OCR สำหรับ .NET เพื่อแยกข้อความจากรูปภาพสำเร็จแล้ว ไลบรารีนี้ใช้งานง่ายและมีคุณลักษณะที่มีประสิทธิภาพ จึงเป็นตัวเลือกที่ยอดเยี่ยมสำหรับการนำ OCR ไปใช้ในโครงการ .NET ของคุณ

## คำถามที่พบบ่อย

### Aspose.OCR สามารถรองรับหลายภาษาได้หรือไม่

ใช่ Aspose.OCR รองรับภาษาต่างๆ มากมาย ทำให้เป็นโซลูชันอเนกประสงค์สำหรับความต้องการ OCR ที่แตกต่างกัน

### มีเวอร์ชันทดลองใช้งานไหม?

 แน่นอน! คุณสามารถลองใช้ Aspose.OCR สำหรับ .NET ด้วยการทดลองใช้ฟรี[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.OCR ได้จากที่ไหน

 หากต้องการความช่วยเหลือ โปรดไปที่[ฟอรั่ม Aspose.OCR](https://forum.aspose.com/c/ocr/16) ซึ่งมีสมาชิกชุมชนและผู้เชี่ยวชาญพร้อมให้ความช่วยเหลือ

### ฉันสามารถขอใบอนุญาตชั่วคราวได้หรือไม่?

 ใช่ครับ สามารถขอใบอนุญาตชั่วคราวเพื่อทำการทดสอบได้ที่นี้ครับ[ลิงค์](https://purchase.conholdate.com/temporary-license/).

### ฉันสามารถซื้อ Aspose.OCR สำหรับ .NET ได้อย่างไร?

 หากต้องการรวม Aspose.OCR เข้ากับชุดเครื่องมือของคุณอย่างถาวร ให้ไปที่[หน้าการซื้อ](https://purchase.conholdate.com/buy).