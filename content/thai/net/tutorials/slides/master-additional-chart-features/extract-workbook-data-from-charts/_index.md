---
title: ดึงข้อมูลสมุดงานจากแผนภูมิด้วย Aspose.Slides สำหรับ .NET
linktitle: ดึงข้อมูลสมุดงานจากแผนภูมิด้วย Aspose.Slides สำหรับ .NET
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: ปลดล็อกศักยภาพของการนำเสนอ PowerPoint ของคุณโดยการเรียนรู้วิธีการกู้คืนข้อมูลเวิร์กบุ๊กจากแผนภูมิโดยใช้ Aspose.Slides สำหรับ .NET บทช่วยสอนทีละขั้นตอนนี้จะแนะนำคุณตลอดกระบวนการ ทำให้สามารถดึงและใช้ข้อมูลแผนภูมิได้อย่างมีประสิทธิภาพ
type: docs
weight: 12
url: /th/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## การแนะนำ

การทำงานกับงานนำเสนอ PowerPoint อาจเป็นเรื่องท้าทาย โดยเฉพาะอย่างยิ่งเมื่อต้องดึงข้อมูลที่มีค่าจากแผนภูมิที่ฝังไว้ โชคดีที่ Aspose.Slides สำหรับ .NET มีโซลูชันที่แข็งแกร่งซึ่งช่วยลดความซับซ้อนของกระบวนการนี้ ในบทช่วยสอนนี้ เราจะแนะนำคุณทีละขั้นตอนเกี่ยวกับวิธีการกู้คืนเวิร์กบุ๊กจากแผนภูมิภายในงานนำเสนอ PowerPoint

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด โปรดตรวจสอบให้แน่ใจว่าคุณได้เตรียมสิ่งต่อไปนี้แล้ว:

### Aspose.Slides สำหรับ .NET

คุณต้องติดตั้ง Aspose.Slides สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ หากคุณยังไม่ได้ติดตั้ง คุณสามารถดาวน์โหลดจากเว็บไซต์:

[ดาวน์โหลด Aspose.Slides สำหรับ .NET](https://releases.aspose.com/slides/net/)

### การนำเสนอ PowerPoint

เตรียมไฟล์การนำเสนอ PowerPoint ของคุณให้พร้อม โดยเฉพาะไฟล์ที่มีแผนภูมิพร้อมข้อมูลที่เกี่ยวข้องซึ่งคุณต้องการกู้คืน

## ขั้นตอนที่ 1: นำเข้าเนมสเปซที่จำเป็น

ในการทำงานกับ Aspose.Slides ได้อย่างมีประสิทธิภาพ ขั้นแรกคุณจะต้องนำเข้าเนมสเปซที่จำเป็น:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## ขั้นตอนที่ 2: กำหนดไดเรกทอรีเอกสาร

ระบุไดเร็กทอรีที่ไฟล์การนำเสนอของคุณตั้งอยู่:

```csharp
string dataDir = "Your Document Directory"; // ปรับเปลี่ยนเส้นทางนี้ตามความจำเป็น
```

## ขั้นตอนที่ 3: โหลดงานนำเสนอ

คุณสามารถโหลดงานนำเสนอ PowerPoint ได้ในขณะที่เปิดใช้งานการกู้คืนเวิร์กบุ๊กจากแคชของแผนภูมิ โดยทำดังนี้:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // การเข้าถึงและทำงานกับข้อมูลแผนภูมิ
    // โค้ดของคุณจะอยู่ที่นี่
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 ในขั้นตอนนี้`LoadOptions` วัตถุช่วยให้คุณสามารถเปิดใช้งานการกู้คืนสมุดงานโดยใช้`RecoverWorkbookFromChartCache` คุณสมบัติ.

## ขั้นตอนที่ 4: ดึงแผนภูมิและเข้าถึงสมุดงาน

ตอนนี้ถึงเวลาที่จะเจาะลึกแผนภูมิและดึงข้อมูลที่เกี่ยวข้อง:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // ปรับดัชนีตามต้องการ
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// ตอนนี้คุณสามารถทำงานกับข้อมูลเวิร์กบุ๊กตามความต้องการของคุณได้
```

เมื่อเข้าถึงรูปร่างแรกของสไลด์แรก (ซึ่งคาดว่าจะเป็นแผนภูมิ) คุณจะได้รับสมุดงานข้อมูลแผนภูมิ และสามารถจัดการหรือแยกข้อมูลตามต้องการได้

## บทสรุป

ในบทช่วยสอนนี้ เราได้สาธิตวิธีการกู้คืนสมุดงานจากแผนภูมิในงานนำเสนอ PowerPoint ได้อย่างมีประสิทธิภาพโดยใช้ Aspose.Slides สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้แล้ว คุณสามารถดึงและใช้ข้อมูลแผนภูมิเพื่อตอบสนองความต้องการในการวิเคราะห์ของคุณได้อย่างง่ายดาย

## คำถามที่พบบ่อย

### Aspose.Slides สำหรับ .NET คืออะไร?

Aspose.Slides สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงการนำเสนอ Microsoft PowerPoint ด้วยโปรแกรมได้

### ฉันสามารถทดลองใช้ Aspose.Slides สำหรับ .NET ก่อนซื้อได้หรือไม่

 ใช่! Aspose นำเสนอ Aspose.Slides สำหรับ .NET รุ่นทดลองใช้งานฟรี คุณสามารถประเมินความสามารถก่อนตัดสินใจซื้อได้[รับการทดลองใช้ฟรีได้ที่นี่](https://releases.aspose.com/).

### ฉันสามารถหาเอกสารสำหรับ Aspose.Slides สำหรับ .NET ได้จากที่ไหน

 คุณสามารถเข้าถึงเอกสารประกอบที่ครอบคลุมสำหรับ Aspose.Slides สำหรับ .NET ได้[ที่นี่](https://reference.aspose.com/slides/net/)ซึ่งรวมถึงตัวอย่างและการอ้างอิง API

### ฉันจะซื้อใบอนุญาตสำหรับ Aspose.Slides สำหรับ .NET ได้อย่างไร

 หากต้องการซื้อใบอนุญาต ให้ไปที่เว็บไซต์ Aspose และใช้ลิงก์ต่อไปนี้:[ซื้อ Aspose.Slides สำหรับ .NET](https://purchase.aspose.com/buy).