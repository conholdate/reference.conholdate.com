---
title: แยกข้อความที่เน้นจาก PDF โดยใช้ Aspose.PDF สำหรับ .NET
linktitle: แยกข้อความที่เน้นจาก PDF โดยใช้ Aspose.PDF สำหรับ .NET
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: ปลดล็อกศักยภาพของเอกสาร PDF ของคุณโดยเรียนรู้วิธีการแยกข้อความที่มีไฮไลต์ด้วย Aspose.PDF สำหรับ .NET คู่มือที่ครอบคลุมนี้จะแนะนำคุณในแต่ละขั้นตอนตั้งแต่การตั้งค่าจนถึงการใช้งาน
type: docs
weight: 60
url: /th/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## การแนะนำ

เมื่อทำงานกับไฟล์ PDF การแยกข้อความที่เน้นข้อความอาจมีความจำเป็นสำหรับการวิเคราะห์ข้อมูล การตรวจสอบเนื้อหา หรือการจัดระเบียบบันทึกย่อ หากคุณใช้ Aspose.PDF สำหรับ .NET คุณโชคดีแล้ว บทช่วยสอนนี้ให้คำแนะนำแบบทีละขั้นตอนที่ชัดเจนเกี่ยวกับวิธีการแยกข้อความที่เน้นข้อความจากเอกสาร PDF อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.PDF สำหรับไลบรารี .NET: ดาวน์โหลดไลบรารีจาก[หน้าวางจำหน่าย](https://releases.aspose.com/pdf/net/).
- สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการทำงานเช่น Visual Studio
- ความรู้พื้นฐานเกี่ยวกับ C#: ต้องมีความคุ้นเคยกับ C# และการเขียนโปรแกรมเชิงวัตถุ
-  ใบอนุญาต Aspose: ในขณะที่คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรี[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือใบอนุญาตเต็มรูปแบบจาก[ที่นี่](https://purchase.aspose.com/buy) จะให้การเข้าถึงแบบไม่มีข้อจำกัด

## นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

เนมสเปซเหล่านี้ให้การเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการจัดการเอกสาร PDF และคำอธิบายประกอบ

## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีโครงการของคุณ

ระบุไดเรกทอรีที่ไฟล์ PDF ของคุณตั้งอยู่:

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

อย่าลืมแทนที่เส้นทางด้วยไดเร็กทอรีจริงของไฟล์ PDF ของคุณ

## ขั้นตอนที่ 2: โหลดเอกสาร PDF

โหลดเอกสาร PDF ด้วยโค้ดต่อไปนี้:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

ตรวจสอบให้แน่ใจว่าไฟล์ที่ระบุมีอยู่ในไดเร็กทอรีที่กำหนด

## ขั้นตอนที่ 3: เข้าถึงคำอธิบายบนหน้า

หากต้องการเข้าถึงคำอธิบาย ให้วนซ้ำผ่านคำอธิบายในหน้าที่คุณต้องการ (ในกรณีนี้คือหน้าแรก)

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 โค้ดนี้กรองสำหรับ`TextMarkupAnnotation` ประเภทซึ่งแสดงถึงไฮไลท์

## ขั้นตอนที่ 4: แยกข้อความที่เน้นไว้

ตอนนี้แยกและแสดงข้อความจากคำอธิบายที่เน้นไว้:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

การดำเนินการนี้จะเรียกเศษข้อความที่ทำเครื่องหมายไว้ทั้งหมดที่เชื่อมโยงกับไฮไลต์ และพิมพ์ไปยังคอนโซล

## บทสรุป

การแยกข้อความที่เน้นข้อความจาก PDF โดยใช้ Aspose.PDF สำหรับ .NET เป็นเรื่องง่ายและช่วยปรับปรุงกระบวนการจัดการเอกสารของคุณได้อย่างมาก หากปฏิบัติตามขั้นตอนที่ระบุไว้ข้างต้น คุณจะสามารถรวบรวมข้อความที่เน้นข้อความได้อย่างมีประสิทธิภาพสำหรับแอปพลิเคชันต่างๆ เช่น การจัดเตรียมรายงานหรือการวิเคราะห์ข้อมูล

## คำถามที่พบบ่อย

### ฉันสามารถดึงคำอธิบายประเภทอื่นออกมาได้หรือไม่
 ใช่ เพียงแค่ปรับ`if` เงื่อนไขในการรวมประเภทคำอธิบายประกอบที่แตกต่างกัน เช่น`TextAnnotation` หรือ`StampAnnotation`.

### ฉันจะแยกข้อความที่เน้นสีจากทุกหน้า PDF ได้อย่างไร
คุณสามารถวนซ้ำผ่านหน้าทั้งหมดได้โดยใช้:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### จำเป็นต้องมีใบอนุญาตสำหรับ Aspose.PDF สำหรับ .NET หรือไม่
 มีการทดลองใช้ฟรี แต่โปรดพิจารณา[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) หรือใบอนุญาตเต็มรูปแบบเพื่อการเข้าถึงอย่างครบถ้วน

### ฉันสามารถบันทึกข้อความที่แยกออกมาลงในไฟล์ได้หรือไม่
แน่นอน! คุณสามารถแก้ไขโค้ดเพื่อเขียนข้อความที่แยกออกมาลงในไฟล์ข้อความได้

### Aspose.PDF รองรับแพลตฟอร์มอื่น ๆ หรือไม่?
ใช่ Aspose.PDF รองรับ Java และแพลตฟอร์มอื่นๆ ด้วย และมีฟังก์ชันการทำงานที่คล้ายคลึงกัน