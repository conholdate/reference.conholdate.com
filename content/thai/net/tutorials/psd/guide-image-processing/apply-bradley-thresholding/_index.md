---
title: ใช้ Bradley Thresholding ใน Aspose.PSD สำหรับ .NET
linktitle: ใช้เกณฑ์ Bradley
second_title: API ของ Aspose.PSD .NET
description: เรียนรู้ทีละขั้นตอนเกี่ยวกับวิธีการโหลดไฟล์ PSD ใช้เทคนิคการกำหนดค่าขีดจำกัด และบันทึกผลลัพธ์ในรูปแบบต่างๆ เพื่อปรับปรุงงานการแบ่งส่วนภาพของคุณสำหรับการใช้งานที่หลากหลาย
type: docs
weight: 15
url: /th/net/tutorials/psd/guide-image-processing/apply-bradley-thresholding/
---
## การแนะนำ

ยินดีต้อนรับสู่บทช่วยสอนของเราเกี่ยวกับการใช้เทคนิค Bradley Threshold โดยใช้ Aspose.PSD สำหรับ .NET ไลบรารีอันทรงพลังนี้ช่วยให้สามารถจัดการไฟล์ Photoshop ภายในแอปพลิเคชัน .NET ได้อย่างราบรื่น Bradley Thresholding เป็นวิธีการที่มีประสิทธิภาพในการแปลงภาพเป็นไบนารี ซึ่งช่วยแยกแยะวัตถุจากพื้นหลัง

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มดำเนินการ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

-  Aspose.PSD สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งเวอร์ชันล่าสุดจาก[เอกสารประกอบ](https://reference.aspose.com/psd/net/).
- ไดเร็กทอรีเอกสาร: สร้างไดเร็กทอรีการทำงานเพื่อจัดเก็บไฟล์ PSD ต้นฉบับและภาพไบนารีเอาต์พุต

## นำเข้าเนมสเปซที่จำเป็น

เริ่มโครงการของคุณโดยนำเข้าเนมสเปซที่เกี่ยวข้องเพื่อเข้าถึงฟังก์ชันการทำงานของ Aspose.PSD:

```csharp
// นำเข้าเนมสเปซ Aspose.PSD
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## ขั้นตอนที่ 1: โหลดภาพต้นฉบับของคุณ

กำหนดเส้นทางไปยังไดเร็กทอรีเอกสารของคุณพร้อมกับไฟล์ PSD ต้นฉบับและชื่อสำหรับไฟล์เอาต์พุต:

```csharp
// ระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "Your Document Directory";

string sourceFile = Path.Combine(dataDir, "sample.psd");
string outputFile = Path.Combine(dataDir, "binarized_out.png");
```

## ขั้นตอนที่ 2: ใช้เกณฑ์ Bradley

ขั้นตอนต่อไป โหลดภาพ PSD เลือกค่าขีดจำกัดของคุณ ใช้การกำหนดค่าขีดจำกัด Bradely แล้วบันทึกผลลัพธ์:

```csharp
// โหลดภาพ PSD
using (PsdImage image = (PsdImage)Image.Load(sourceFile))
{
    // ตั้งค่าเกณฑ์ขั้นต่ำ (ทดลองค่านี้ตามต้องการ)
    double threshold = 0.15;

    // แปลงภาพเป็นไบนารีโดยใช้วิธีแบรดลีย์
    image.BinarizeBradley(threshold);

    // บันทึกภาพในรูปแบบไบนารี่ PNG
    image.Save(outputFile, new PngOptions());
}
```

## บทสรุป

ขอแสดงความยินดี! คุณได้นำเทคนิค Bradley Threshold ไปใช้อย่างสำเร็จโดยใช้ Aspose.PSD สำหรับ .NET วิธีการนี้สามารถปรับปรุงการแบ่งส่วนภาพสำหรับแอปพลิเคชันต่างๆ ได้อย่างมาก ตั้งแต่การวิเคราะห์เอกสารไปจนถึงการออกแบบกราฟิก

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Bradley Threshold กับภาพประเภทใดก็ได้หรือไม่

แน่นอน! Bradley Thresholding มีความยืดหยุ่นและสามารถนำไปใช้กับภาพประเภทต่างๆ ได้ส่วนใหญ่เพื่อปรับปรุงการแบ่งส่วน

### ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับ Aspose.PSD ได้จากที่ใด

 สำหรับเอกสารและทรัพยากรโดยละเอียด โปรดไปที่[เอกสาร Aspose.PSD](https://reference.aspose.com/psd/net/).

### มีเวอร์ชันทดลองใช้งานไหม?

 ใช่! คุณสามารถทดลองใช้ Aspose.PSD สำหรับ .NET ได้ด้วยการทดลองใช้ฟรี[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.PSD ได้อย่างไร?

 สำหรับการสนับสนุนและการสนทนาของชุมชน โปรดดูที่[ฟอรั่ม Aspose.PSD](https://forum.aspose.com/c/psd/34).

### ฉันสามารถซื้อใบอนุญาตสำหรับ Aspose.PSD ได้อย่างไร?

 คุณสามารถซื้อใบอนุญาตได้โดยตรง[ที่นี่](https://purchase.conholdate.com/buy).