---
title: เรียนรู้เอฟเฟกต์ After-Animation ด้วย Aspose.Slides สำหรับ .NET
linktitle: เรียนรู้เอฟเฟกต์ After-Animation ด้วย Aspose.Slides สำหรับ .NET
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: ปลดล็อกศักยภาพทั้งหมดของการนำเสนอของคุณโดยเรียนรู้เอฟเฟกต์ภาพเคลื่อนไหวภายหลังด้วย Aspose.Slides สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะให้ข้อมูลสำคัญแก่คุณ
type: docs
weight: 11
url: /th/net/tutorials/slides/master-slide-animation-control/control-after-animation-effects/
---
## การแนะนำ

แอนิเมชั่นแบบไดนามิกสามารถปรับปรุงการนำเสนอของคุณได้อย่างมาก ทำให้ดึงดูดและดึงดูดสายตามากขึ้น ด้วย Aspose.Slides สำหรับ .NET คุณสามารถควบคุมเอฟเฟกต์หลังแอนิเมชั่นได้อย่างง่ายดาย ช่วยให้คุณสร้างประสบการณ์แบบโต้ตอบสำหรับผู้ชมได้ บทช่วยสอนนี้จะแนะนำคุณทีละขั้นตอนเกี่ยวกับกระบวนการจัดการเอฟเฟกต์เหล่านี้ในสไลด์ของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET
-  ติดตั้งไลบรารี Aspose.Slides สำหรับ .NET แล้ว ดาวน์โหลด[ที่นี่](https://releases.aspose.com/slides/net/).
- สภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เช่น Visual Studio

## นำเข้าเนมสเปซ

หากต้องการเข้าถึงฟังก์ชันการทำงานที่จำเป็นของ Aspose.Slides ให้รวมเนมสเปซต่อไปนี้ไว้ในโค้ดของคุณ:

```csharp
using System.Drawing;
using System.IO;
using Aspose.Slides.Animation;
using Aspose.Slides.SlideShow;
using Aspose.Slides.Export;
```

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีเอกสาร

เริ่มต้นด้วยการตรวจสอบให้แน่ใจว่าไดเร็กทอรีสำหรับเอกสารของคุณมีอยู่ หากไม่มี ให้สร้างขึ้น:

```csharp
string dataDir = "Your Document Directory";
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## ขั้นตอนที่ 2: กำหนดเส้นทางไฟล์เอาท์พุต

ระบุเส้นทางไฟล์เอาท์พุตสำหรับการนำเสนอที่คุณแก้ไข:

```csharp
string outPath = Path.Combine(dataDir, "AnimationAfterEffect-out.pptx");
```

## ขั้นตอนที่ 3: โหลดงานนำเสนอ

 โหลดงานนำเสนอที่มีอยู่ของคุณโดยใช้`Presentation` ระดับ:

```csharp
using (Presentation pres = new Presentation(dataDir + "AnimationAfterEffect.pptx"))
```

## ขั้นตอนที่ 4: แก้ไขเอฟเฟกต์ After Animation บนสไลด์ที่ 1

โคลนสไลด์แรกและตั้งเอฟเฟกต์หลังการเคลื่อนไหวเป็น "ซ่อนเมื่อคลิกเมาส์ครั้งถัดไป"

```csharp
ISlide slide1 = pres.Slides.AddClone(pres.Slides[0]);
ISequence seq = slide1.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideOnNextMouseClick;
```

## ขั้นตอนที่ 5: แก้ไขเอฟเฟกต์ After Animation บนสไลด์ที่ 2

โคลนสไลด์แรกอีกครั้งโดยเปลี่ยนเอฟเฟกต์หลังการเคลื่อนไหวเป็น "สี" ด้วยโทนสีเขียว:

```csharp
ISlide slide2 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide2.Timeline.MainSequence;
foreach (IEffect effect in seq)
{
    effect.AfterAnimationType = AfterAnimationType.Color;
    effect.AfterAnimationColor.Color = Color.Green;
}
```

## ขั้นตอนที่ 6: แก้ไขเอฟเฟกต์ After Animation บนสไลด์ที่ 3

สำหรับสไลด์ที่สาม ให้ตั้งค่าเอฟเฟ็กต์หลังการเคลื่อนไหวเป็น "ซ่อนหลังการเคลื่อนไหว"

```csharp
ISlide slide3 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide3.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideAfterAnimation;
```

## ขั้นตอนที่ 7: บันทึกการนำเสนอที่แก้ไขแล้ว

สุดท้ายให้บันทึกการนำเสนอที่แก้ไขของคุณ:

```csharp
pres.Save(outPath, SaveFormat.Pptx);
```

## บทสรุป

ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการควบคุมเอฟเฟกต์ภาพเคลื่อนไหวหลังการนำเสนอบนสไลด์โดยใช้ Aspose.Slides สำหรับ .NET สำเร็จแล้ว อย่าลังเลที่จะทดลองใช้เอฟเฟกต์ต่างๆ เพื่อสร้างงานนำเสนอที่มีชีวิตชีวาและน่าดึงดูดใจที่จะดึงดูดผู้ชมของคุณ

## คำถามที่พบบ่อย

### ฉันสามารถใช้เอฟเฟ็กต์หลังการเคลื่อนไหวที่แตกต่างกันกับองค์ประกอบแต่ละองค์ประกอบภายในสไลด์ได้หรือไม่

ใช่ คุณสามารถปรับแต่งเอฟเฟ็กต์หลังการเคลื่อนไหวสำหรับองค์ประกอบแต่ละองค์ประกอบได้โดยการทำซ้ำและปรับคุณสมบัติขององค์ประกอบเหล่านั้นให้เหมาะสม

### Aspose.Slides เข้ากันได้กับ .NET เวอร์ชันล่าสุดหรือไม่

แน่นอน! Aspose.Slides ได้รับการอัปเดตเป็นประจำเพื่อให้มั่นใจว่าสามารถใช้งานร่วมกับ .NET framework เวอร์ชันล่าสุดได้

### ฉันจะเพิ่มแอนิเมชั่นแบบกำหนดเองลงในสไลด์โดยใช้ Aspose.Slides ได้อย่างไร

 สำหรับข้อมูลโดยละเอียดเกี่ยวกับการเพิ่มแอนิเมชั่นแบบกำหนดเอง โปรดดูที่[เอกสารประกอบ Aspose.Slides](https://reference.aspose.com/slides/net/).

### Aspose.Slides รองรับรูปแบบไฟล์ใดบ้างสำหรับการบันทึกงานนำเสนอ?

Aspose.Slides รองรับรูปแบบต่างๆ เช่น PPTX, PPT, PDF และอื่นๆ อีกมากมาย โปรดดูเอกสารประกอบเพื่อดูรายการทั้งหมด

### ฉันจะได้รับการสนับสนุนหรือถามคำถามที่เกี่ยวข้องกับ Aspose.Slides ได้จากที่ไหน

 สำหรับการสนับสนุนและการมีปฏิสัมพันธ์กับชุมชน โปรดไปที่[ฟอรั่ม Aspose.Slides](https://forum.aspose.com/c/slides/11).