---
title: การแยกเสียงและวิดีโอจาก PowerPoint
linktitle: การแยกเสียงและวิดีโอจาก PowerPoint
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: ค้นพบวิธีการแยกองค์ประกอบเสียงและวิดีโอจากงานนำเสนอ PowerPoint ได้อย่างง่ายดายโดยใช้ Aspose.Slides สำหรับ .NET คำแนะนำโดยละเอียดนี้มีแนวทางทีละขั้นตอน
type: docs
weight: 10
url: /th/net/tutorials/slides/extract-audio-and-video/extracting-audio-and-video/
---
## การแนะนำ

ในภูมิทัศน์ดิจิทัลของปัจจุบัน การนำเสนอแบบมัลติมีเดียมีบทบาทสำคัญในการสื่อสาร การศึกษา และความบันเทิง สไลด์ PowerPoint มักรวมเอาองค์ประกอบเสียงและวิดีโอเข้าด้วยกัน ทำให้องค์ประกอบเหล่านี้มีความจำเป็นในการนำเสนอข้อมูลอย่างมีประสิทธิภาพ ไม่ว่าจะเพื่อการเก็บถาวร การนำเนื้อหาไปใช้ใหม่ หรือการปรับปรุงการนำเสนอ การแยกองค์ประกอบมัลติมีเดียเหล่านี้ออกมามักมีความจำเป็น

คู่มือนี้จะแนะนำคุณเกี่ยวกับกระบวนการแยกเสียงและวิดีโอจากสไลด์ PowerPoint โดยใช้ Aspose.Slides สำหรับ .NET Aspose.Slides เป็นไลบรารีที่มีประสิทธิภาพที่ช่วยให้ผู้พัฒนา .NET สามารถจัดการการนำเสนอ PowerPoint ได้ด้วยโปรแกรม ทำให้การดึงข้อมูลมัลติมีเดียเป็นเรื่องง่ายขึ้น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณได้ตั้งค่าสิ่งต่อไปนี้แล้ว:

1. Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio สำหรับการพัฒนา .NET
2.  Aspose.Slides สำหรับ .NET: ดาวน์โหลดและติดตั้ง Aspose.Slides สำหรับ .NET จาก[เว็บไซต์อาโพส](https://releases.aspose.com/slides/net/).
3. การนำเสนอ PowerPoint: เตรียมการนำเสนอ PowerPoint ที่มีองค์ประกอบเสียงและวิดีโอสำหรับการฝึกฝน

เมื่อมีข้อกำหนดเบื้องต้นเหล่านี้แล้ว เรามาเริ่มขั้นตอนการสกัดกันเลย

## การแยกเสียงจากสไลด์ PowerPoint

### ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

สร้างโครงการใหม่ใน Visual Studio และนำเข้าเนมสเปซ Aspose.Slides ที่จำเป็น:

```csharp
using Aspose.Slides;
using Aspose.Slides.SlideShow;
```

### ขั้นตอนที่ 2: โหลดงานนำเสนอ

โหลดงานนำเสนอ PowerPoint ที่มีเสียงที่คุณต้องการแยก:

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "AudioSlide.ppt";
Presentation pres = new Presentation(presName);
```

### ขั้นตอนที่ 3: เข้าถึงสไลด์ที่ต้องการ

 ใช้`ISlide` อินเทอร์เฟซสำหรับการเข้าถึงสไลด์ที่เฉพาะเจาะจง:

```csharp
ISlide slide = pres.Slides[0]; // เข้าถึงสไลด์แรก
```

### ขั้นตอนที่ 4: แยกเสียงออกมา

ดึงข้อมูลเสียงจากเอฟเฟ็กต์การเปลี่ยนภาพสไลด์:

```csharp
ISlideShowTransition transition = slide.SlideShowTransition;
byte[] audio = transition.Sound.BinaryData;
System.Console.WriteLine("Audio Length: " + audio.Length);
```

## การแยกวิดีโอจากสไลด์ PowerPoint

### ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

เช่นเดียวกับการแยกเสียง เริ่มต้นด้วยการสร้างโปรเจ็กต์ใหม่และนำเข้าเนมสเปซที่จำเป็น

### ขั้นตอนที่ 2: โหลดงานนำเสนอ

โหลดงานนำเสนอ PowerPoint ที่มีวิดีโอที่คุณต้องการแยก:

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "Video.pptx";
Presentation pres = new Presentation(presName);
```

### ขั้นตอนที่ 3: ทำซ้ำผ่านสไลด์และรูปร่าง

วนซ้ำผ่านสไลด์และรูปร่างเพื่อระบุเฟรมวิดีโอ:

```csharp
foreach (ISlide slide in pres.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is IVideoFrame videoFrame)
        {
            // ดึงข้อมูลเฟรมวิดีโอ
            string contentType = videoFrame.EmbeddedVideo.ContentType;
            string fileType = contentType.Substring(contentType.LastIndexOf('/') + 1);
            
            // รับข้อมูลวิดีโอเป็นอาร์เรย์ไบต์
            byte[] buffer = videoFrame.EmbeddedVideo.BinaryData;
            
            // บันทึกวิดีโอลงในไฟล์
            using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileType, FileMode.Create, FileAccess.Write, FileShare.Read))
            {
                stream.Write(buffer, 0, buffer.Length);
            }
        }
    }
}
```

## บทสรุป

Aspose.Slides สำหรับ .NET ช่วยให้สามารถแยกเสียงและวิดีโอจากงานนำเสนอ PowerPoint ได้อย่างง่ายดาย ไม่ว่าคุณจะกำลังจัดเก็บเนื้อหา ปรับเปลี่ยนการใช้งานมัลติมีเดีย หรือวิเคราะห์งานนำเสนอ ไลบรารีนี้มอบเครื่องมือที่คุณต้องการเพื่อปรับปรุงกระบวนการให้มีประสิทธิภาพ

## คำถามที่พบบ่อย

### Aspose.Slides สำหรับ .NET เข้ากันได้กับรูปแบบ PowerPoint ล่าสุดหรือไม่
ใช่ Aspose.Slides สำหรับ .NET รองรับรูปแบบ PowerPoint ล่าสุด รวมถึง PPTX

### ฉันสามารถแยกเสียงและวิดีโอจากสไลด์หลาย ๆ ภาพในครั้งเดียวได้ไหม
แน่นอน! คุณสามารถแก้ไขโค้ดเพื่อวนซ้ำผ่านสไลด์หลาย ๆ อันและแยกมัลติมีเดียจากแต่ละอันได้

### มีตัวเลือกการออกใบอนุญาตสำหรับ Aspose.Slides สำหรับ .NET หรือไม่
 Aspose นำเสนอตัวเลือกการออกใบอนุญาตต่างๆ รวมถึงการทดลองใช้ฟรีและใบอนุญาตชั่วคราว เยี่ยมชม[เว็บไซต์](https://purchase.aspose.com/buy) สำหรับข้อมูลเพิ่มเติม

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Slides สำหรับ .NET ได้อย่างไร
 สำหรับการสนับสนุนด้านเทคนิคและการสนทนาของชุมชน โปรดดู Aspose.Slides[ฟอรั่ม](https://forum.aspose.com/).

### ฉันสามารถดำเนินการงานอื่นๆ อะไรได้อีกบ้างด้วย Aspose.Slides สำหรับ .NET
 Aspose.Slides สำหรับ .NET นำเสนอคุณลักษณะต่างๆ มากมาย รวมถึงการสร้าง ปรับเปลี่ยน และแปลงงานนำเสนอ PowerPoint อ่านเอกสารประกอบเพื่อดูรายละเอียดเพิ่มเติม:[เอกสาร Aspose.Slides สำหรับ .NET](https://reference.aspose.com/slides/net/).