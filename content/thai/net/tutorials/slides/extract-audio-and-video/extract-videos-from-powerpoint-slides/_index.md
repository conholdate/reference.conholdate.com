---
title: ดึงวิดีโอจากสไลด์ PowerPoint ด้วย Aspose.Slides
linktitle: ดึงวิดีโอจากสไลด์ PowerPoint
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: ค้นพบวิธีการแยกไฟล์วิดีโอที่ฝังไว้จากงานนำเสนอ PowerPoint ได้อย่างง่ายดายโดยใช้ Aspose.Slides สำหรับ .NET คำแนะนำทีละขั้นตอนที่ครอบคลุมนี้ครอบคลุมทุกอย่างตั้งแต่การตั้งค่าสภาพแวดล้อมของคุณไปจนถึงการบันทึกวิดีโอที่แยกออกมา
type: docs
weight: 14
url: /th/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## การแนะนำ

Aspose.Slides สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถโต้ตอบกับการนำเสนอ PowerPoint ได้ด้วยโปรแกรม ในคู่มือนี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการแยกวิดีโอที่ฝังอยู่ในสไลด์ PowerPoint โดยใช้ Aspose.Slides สำหรับ .NET 

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Slides สำหรับ .NET: รับและติดตั้งไลบรารีจาก[เว็บไซต์อาโพส](https://purchase.aspose.com/buy).
-  การนำเสนอ PowerPoint: เตรียมไฟล์ PowerPoint (เช่น`Video.pptx`) พร้อมวิดีโอที่คุณต้องการแยก

## เนมสเปซที่จำเป็น

ในการใช้งาน Aspose.Slides สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่เหมาะสม โดยใส่สิ่งต่อไปนี้ในโค้ดของคุณ:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## ขั้นตอนที่ 1: ระบุไดเรกทอรีเอกสาร

ขั้นแรก ให้กำหนดเส้นทางไปยังการนำเสนอ PowerPoint ของคุณ:

```csharp
string dataDir = "Your Document Directory";
```

 แทนที่`"Your Document Directory"` โดยมีเส้นทางจริงไปยังไดเร็กทอรีที่มีไฟล์ PowerPoint ของคุณ

## ขั้นตอนที่ 2: โหลดงานนำเสนอ

 โหลดการนำเสนอ PowerPoint ลงใน`Presentation` วัตถุ:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 นี่คือการเริ่มต้น`Presentation` วัตถุที่มีไฟล์ PowerPoint ที่คุณระบุ

## ขั้นตอนที่ 3: ทำซ้ำผ่านสไลด์และรูปร่าง

ขั้นตอนต่อไปคือการวนซ้ำผ่านแต่ละสไลด์ในงานนำเสนอและตรวจสอบเฟรมวิดีโอ:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // ดำเนินการแยกวิดีโอ
        }
    }
}
```

## ขั้นตอนที่ 4: แยกข้อมูลวิดีโอ

เมื่อคุณพบเฟรมวิดีโอแล้ว ให้แยกคุณสมบัติและข้อมูลไบนารีของมัน:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // จัดเก็บรูปร่างเป็นเฟรมวิดีโอ
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// รับนามสกุลไฟล์
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## ขั้นตอนที่ 5: บันทึกวิดีโอ

สุดท้ายเขียนข้อมูลวิดีโอที่แยกออกมาลงในไฟล์:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

โค้ดนี้จะสร้างไฟล์ใหม่ในไดเร็กทอรีที่คุณระบุและเขียนข้อมูลวิดีโอลงไป

## บทสรุป

การแยกวิดีโอจากสไลด์ PowerPoint เป็นกระบวนการที่ง่ายดายด้วย Aspose.Slides สำหรับ .NET เมื่อทำตามคำแนะนำนี้ คุณจะสามารถจัดการเนื้อหามัลติมีเดียภายในแอปพลิเคชัน .NET ได้อย่างง่ายดาย ช่วยเพิ่มประสบการณ์และฟังก์ชันการใช้งานของผู้ใช้

## คำถามที่พบบ่อย

### Aspose.Slides สำหรับ .NET คืออะไร?
Aspose.Slides สำหรับ .NET เป็นไลบรารีที่ออกแบบมาเพื่อทำงานกับงานนำเสนอ PowerPoint โดยช่วยให้ผู้ใช้สามารถสร้าง แก้ไข และจัดการไฟล์งานนำเสนอผ่านโปรแกรมได้

### ฉันสามารถหาเอกสารสำหรับ Aspose.Slides สำหรับ .NET ได้จากที่ไหน
 คุณสามารถเข้าถึงเอกสารฉบับเต็มได้[ที่นี่](https://reference.aspose.com/slides/net/).

### Aspose.Slides สำหรับ .NET มีให้ทดลองใช้งานฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีได้จาก[ลิงค์นี้](https://releases.aspose.com/).

### ฉันจะรับใบอนุญาตชั่วคราวสำหรับ Aspose.Slides สำหรับ .NET ได้อย่างไร
 สามารถทำการขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Slides สำหรับ .NET ได้จากที่ไหน
 การสนับสนุนมีให้บริการผ่าน[ฟอรั่ม Aspose.Slides](https://forum.aspose.com/).