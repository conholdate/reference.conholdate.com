---
title: คู่มือการใช้ OCR กับภาพจาก URL ใน OCR Image Recognition
linktitle: คู่มือการใช้ OCR กับภาพจาก URL ใน OCR Image Recognition
second_title: API ของ Aspose.OCR .NET
description: ค้นพบวิธีการนำ Optical Character Recognition (OCR) ไปใช้ในแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดายโดยใช้ Aspose.OCR คำแนะนำทีละขั้นตอนนี้จะแนะนำคุณตลอดกระบวนการทั้งหมด
type: docs
weight: 10
url: /th/net/tutorials/ocr/optimization-ocr/guide-to-ocr-on-image-from-url/
---
## การแนะนำ

การจดจำอักขระด้วยแสง (OCR) เป็นเทคโนโลยีที่จำเป็นสำหรับการแยกข้อความจากภาพ ช่วยให้นักพัฒนาสามารถสร้างแอปพลิเคชันที่สามารถอ่านและประมวลผลข้อมูลข้อความได้อย่างราบรื่น Aspose.OCR สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งออกแบบมาเพื่อลดความซับซ้อนในการรวมความสามารถ OCR เข้ากับแอปพลิเคชัน .NET ของคุณ คู่มือนี้จะอธิบายวิธีการดำเนินการ OCR กับภาพโดยตรงจาก URL ในขั้นตอนง่ายๆ เพียงไม่กี่ขั้นตอน

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

-  Aspose.OCR สำหรับ .NET: ดาวน์โหลดและรวมไลบรารี Aspose.OCR ลงในโครงการ .NET ของคุณจาก[หน้าวางจำหน่าย](https://releases.aspose.com/ocr/net/).
- สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET บนเครื่องของคุณ (แนะนำให้ใช้ Visual Studio)

## ขั้นตอนที่ 1: นำเข้าเนมสเปซที่จำเป็น

หากต้องการใช้ประโยชน์จากคุณลักษณะต่างๆ ที่ Aspose.OCR นำเสนอ ให้ทำการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
using Aspose.OCR.Models;
```

## ขั้นตอนที่ 2: ระบุไดเรกทอรีเอกสาร

 กำหนดไดเรกทอรีสำหรับเอกสารของคุณ แทนที่`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีการทำงานของคุณ:

```csharp
string dataDir = "Your Document Directory";
```

## ขั้นตอนที่ 3: ระบุ URL ของรูปภาพ

ระบุ URL ของรูปภาพที่คุณต้องการแยกข้อความออกมา ตรวจสอบให้แน่ใจว่ารูปภาพสามารถเข้าถึงได้โดยสาธารณะ:

```csharp
string uri = "https://example.com/image.jpg";
```

## ขั้นตอนที่ 4: เริ่มต้น Aspose.OCR

 สร้างอินสแตนซ์ของ`AsposeOcr` คลาสที่คุณจะใช้ในการดำเนินการ OCR:

```csharp
AsposeOcr api = new AsposeOcr();
```

## ขั้นตอนที่ 5: จดจำข้อความจากภาพ

 ใช้`RecognizeImageFromUri` วิธีการดึงข้อความจาก URL ของรูปภาพ คุณสามารถปรับการตั้งค่าการจดจำต่างๆ ได้ตามความต้องการเฉพาะของคุณ:

```csharp
RecognitionResult result = api.RecognizeImageFromUri(uri, new RecognitionSettings
{
    DetectAreas = true,
    RecognizeSingleLine = false,
    AutoSkew = true,
    RecognitionAreas = new List<Rectangle>
    {
        new Rectangle(1, 3, 390, 70),
        new Rectangle(1, 72, 390, 70)
    }
});
```

## ขั้นตอนที่ 6: แสดงผลลัพธ์การจดจำ

ส่งออกข้อความที่รู้จักพร้อมกับข้อมูลที่เกี่ยวข้อง รวมถึงพื้นที่ที่รู้จักและคำเตือน:

```csharp
Console.WriteLine($"Text:\n {result.RecognitionText}");
Console.WriteLine("Areas:");
result.RecognitionAreasText.ForEach(a => Console.WriteLine($"{a}"));
Console.WriteLine("Warnings:");
result.Warnings.ForEach(w => Console.WriteLine($"{w}"));
Console.WriteLine($"JSON: {result.GetJson()}");
```

## ขั้นตอนที่ 7: ดำเนินการสมัครของคุณ

เรียกใช้แอปพลิเคชันของคุณ หากทุกอย่างได้รับการกำหนดค่าอย่างถูกต้อง คุณควรเห็นการดำเนินการ OCR สำเร็จ:

```csharp
Console.WriteLine("OCR process executed successfully.");
```

## บทสรุป

การรวมความสามารถ OCR เข้ากับแอปพลิเคชัน .NET ของคุณนั้นทำได้ง่ายด้วย Aspose.OCR คู่มือนี้จะพาคุณผ่านขั้นตอนสำคัญต่างๆ ในการทำ OCR กับรูปภาพจาก URL และสร้างรากฐานสำหรับการพัฒนาแอปพลิเคชันที่ใช้ประโยชน์จากเทคโนโลยีการจดจำข้อความ

## คำถามที่พบบ่อย

### Aspose.OCR เหมาะสำหรับการจดจำหลายภาษาหรือไม่

ใช่ Aspose.OCR รองรับภาษาต่างๆ จึงเหมาะอย่างยิ่งสำหรับแอปพลิเคชันที่กำหนดเป้าหมายไปที่ผู้ใช้ต่างประเทศ

### Aspose.OCR สามารถจัดการกับการจดจำข้อความทั้งบรรทัดเดียวและหลายบรรทัดได้หรือไม่

แน่นอน! ไลบรารีนี้มีความยืดหยุ่น รองรับการจดจำข้อความทั้งแบบบรรทัดเดียวและหลายบรรทัดตามความต้องการของโครงการของคุณ

### มีตัวเลือกการออกใบอนุญาตอะไรบ้างสำหรับ Aspose.OCR?

 คุณสามารถเรียนรู้เกี่ยวกับตัวเลือกการอนุญาตสิทธิ์ที่แตกต่างกันและทำการซื้อจาก[ร้านอาโพส](https://purchase.conholdate.com/buy).

### มี Aspose.OCR เวอร์ชันทดลองใช้หรือไม่

 ใช่ มีการทดลองใช้ฟรี คุณสามารถทดลองใช้ได้ที่[หน้าวางจำหน่าย](https://releases.aspose.com/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.OCR ได้ที่ไหน

หากต้องการความช่วยเหลือหรือหารือกับชุมชนเกี่ยวกับ Aspose.OCR โปรดไปที่[ฟอรั่ม Aspose.OCR](https://forum.aspose.com/c/ocr/16).