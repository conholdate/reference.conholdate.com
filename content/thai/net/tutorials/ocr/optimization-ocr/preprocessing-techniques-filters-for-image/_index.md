---
title: เทคนิคการประมวลผลล่วงหน้า ตัวกรองสำหรับภาพใน OCR การจดจำภาพ
linktitle: เทคนิคการประมวลผลล่วงหน้า ตัวกรองสำหรับภาพใน OCR การจดจำภาพ
second_title: API ของ Aspose.OCR .NET
description: ปลดล็อกศักยภาพของการจดจำอักขระด้วยแสง (OCR) ในแอปพลิเคชัน .NET ของคุณด้วย Aspose.OCR คู่มือนี้อธิบายวิธีการทีละขั้นตอนในการนำ OCR ไปใช้โดยใช้ตัวกรองก่อนการประมวลผล
type: docs
weight: 12
url: /th/net/tutorials/ocr/optimization-ocr/preprocessing-techniques-filters-for-image/
---
## การแนะนำ

การจดจำอักขระด้วยแสง (OCR) จะแปลงรูปภาพเป็นข้อความที่แก้ไขได้ ช่วยเพิ่มการเข้าถึงและการใช้งานข้อมูล ในคู่มือนี้ เราจะสำรวจวิธีการผสานรวมและเพิ่มประสิทธิภาพ Aspose.OCR ในแอปพลิเคชัน .NET ของคุณโดยใช้ตัวกรองก่อนการประมวลผลเพื่อให้ได้ผลลัพธ์การจดจำรูปภาพที่ดีที่สุด

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.OCR สำหรับ .NET: ติดตั้งไลบรารีเพื่อใช้ประโยชน์จากความสามารถ เข้าถึงเอกสารประกอบ[ที่นี่](https://reference.aspose.com/ocr/net/) และดาวน์โหลดเวอร์ชั่นล่าสุด[ที่นี่](https://releases.aspose.com/ocr/net/).

- ไดเรกทอรีเอกสาร: สร้างไดเรกทอรีสำหรับจัดเก็บเอกสารของคุณและจดบันทึกเส้นทางเพื่อใช้ในคู่มือนี้

## การนำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการเพิ่มเนมสเปซที่จำเป็นในแอปพลิเคชัน .NET ของคุณ:

```csharp
using System;
using System.IO;
using Aspose.OCR.Models.PreprocessingFilters;
```

## 1. เริ่มต้น Aspose.OCR และตั้งค่าเส้นทางของภาพ

เริ่มต้นด้วยการตั้งค่าอินสแตนซ์ Aspose.OCR และกำหนดเส้นทางของรูปภาพ

```csharp
// ตั้งค่าเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "Your Document Directory Path";

// เริ่มต้นอินสแตนซ์ของ AsposeOcr
AsposeOcr api = new AsposeOcr();

// กำหนดเส้นทางของภาพ
string fullPath = Path.Combine(dataDir, "black.png");
```

## 2. เริ่มต้นใช้งานฟิลเตอร์และประมวลผลภาพเบื้องต้น

ใช้ประโยชน์จากฟิลเตอร์ก่อนการประมวลผลเพื่อปรับปรุงภาพของคุณก่อนที่จะดำเนินการ OCR

```csharp
// เริ่มต้นตัวกรองก่อนการประมวลผล
PreprocessingFilter filters = new PreprocessingFilter
{
    PreprocessingFilter.Invert(),
    PreprocessingFilter.Dilate()
};

// ประมวลผลภาพล่วงหน้าและบันทึกลงใน MemoryStream
using (MemoryStream img = api.PreprocessImage(fullPath, filters))
{
    using (FileStream fs = new FileStream(Path.Combine(dataDir, "preprocessed.png"), FileMode.Create))
    {
        img.WriteTo(fs);
    }
}
```

## 3. จดจำภาพด้วยการประมวลผลล่วงหน้าแบบกำหนดเอง

ตอนนี้เรามาแยกข้อความจากรูปภาพที่ผ่านการประมวลผลล่วงหน้าโดยใช้ Aspose.OCR กัน

```csharp
// จดจำภาพโดยใช้ฟิลเตอร์พรีโพรเซสเซอร์แบบกำหนดเอง
RecognitionResult result = api.RecognizeImage(fullPath, new RecognitionSettings
{
    PreprocessingFilters = filters
});

// แสดงผลข้อความที่ได้รับการยอมรับ
Console.WriteLine($"Text Recognized:\n{result.RecognitionText}");
Console.WriteLine("Image recognition with preprocessing executed successfully.");
```

## บทสรุป

Aspose.OCR สำหรับ .NET นำเสนอฟังก์ชันอันทรงพลังที่ช่วยลดความซับซ้อนของกระบวนการแปลงรูปภาพเป็นข้อความ ด้วยการใช้ตัวกรองก่อนการประมวลผล คุณสามารถปรับปรุงคุณภาพของผลลัพธ์ OCR ได้อย่างมาก ไลบรารีนี้เหมาะอย่างยิ่งสำหรับแอปพลิเคชันต่างๆ ตั้งแต่การแปลงเอกสารเป็นดิจิทัลไปจนถึงการแยกข้อความในหลากหลายอุตสาหกรรม

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.OCR สำหรับ .NET ในแอพพลิเคชันเดสก์ท็อปและเว็บได้หรือไม่  
ใช่ Aspose.OCR มีความหลากหลายและรองรับทั้งแอพพลิเคชันเดสก์ท็อปและเว็บที่พัฒนาใน .NET

### มีตัวเลือกการออกใบอนุญาตอะไรบ้างสำหรับ Aspose.OCR?  
 คุณสามารถสำรวจตัวเลือกการอนุญาตสิทธิ์และทำการซื้อได้[ที่นี่](https://purchase.conholdate.com/buy) . ยังมีรุ่นทดลองใช้งานฟรีอีกด้วย[ที่นี่](https://releases.aspose.com/) และสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.conholdate.com/temporary-license/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.OCR ได้ที่ไหน  
 หากต้องการความช่วยเหลือ โปรดไปที่[ฟอรั่ม Aspose.OCR](https://forum.aspose.com/c/ocr/16) เพื่อชุมชนและการสนับสนุน

### Aspose.OCR รองรับรูปแบบภาพใดบ้าง  
Aspose.OCR รองรับรูปแบบต่างๆ รวมถึง PNG, JPEG, GIF, BMP และ TIFF

### ฉันสามารถรวม Aspose.OCR เข้ากับโครงการ .NET ที่มีอยู่ได้หรือไม่  
แน่นอน! ทำตามขั้นตอนที่ให้ไว้ในบทช่วยสอนนี้เพื่อเพิ่มฟังก์ชัน Aspose.OCR ให้กับโปรเจ็กต์ของคุณได้อย่างราบรื่น