---
title: บันทึกแหล่งที่มาของข้อมูลเมตาของเอกสารใน GroupDocs การเปรียบเทียบสำหรับ .NET
linktitle: การบันทึกแหล่งข้อมูลเมตาของเอกสารในการเปรียบเทียบ GroupDocs สำหรับ .NET
second_title: API การเปรียบเทียบ GroupDocs .NET
description: ปลดล็อกศักยภาพทั้งหมดของการเปรียบเทียบเอกสารในแอปพลิเคชัน .NET ของคุณโดยใช้ประโยชน์จากการเปรียบเทียบ GroupDocs สำหรับ .NET บทช่วยสอนแบบทีละขั้นตอนนี้จะแนะนำคุณเกี่ยวกับการเปรียบเทียบเอกสารอย่างง่ายดาย โดยเน้นที่การบันทึกแหล่งข้อมูลเมตาของเอกสาร
type: docs
weight: 14
url: /th/net/tutorials/comparison/load-and-save-documents/save-documents-metadata-source/
---
## การแนะนำ

ในการพัฒนาซอฟต์แวร์ โดยเฉพาะอย่างยิ่งในอุตสาหกรรมต่างๆ เช่น กฎหมาย การเงิน และการศึกษา ความสามารถในการเปรียบเทียบเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญที่สุด GroupDocs Comparison for .NET มอบโซลูชันที่แข็งแกร่งเพื่อเปรียบเทียบเอกสารภายในแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการใช้ไลบรารีที่มีประสิทธิภาพนี้เพื่อบันทึกแหล่งข้อมูลเมตาของเอกสาร เพื่อให้แน่ใจว่าคุณสามารถใช้ศักยภาพของไลบรารีนี้ให้เกิดประโยชน์สูงสุดสำหรับงานเปรียบเทียบเอกสารของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสิ่งต่อไปนี้แล้ว:

1. สภาพแวดล้อมการพัฒนา: สภาพแวดล้อมการพัฒนา .NET พร้อมใช้งานบนเครื่องของคุณแล้ว
2. การติดตั้งการเปรียบเทียบ GroupDocs: ดาวน์โหลดและติดตั้งการเปรียบเทียบ GroupDocs สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/comparison/net/).
3. ไฟล์เอกสาร: เตรียมไฟล์เอกสารต้นฉบับและไฟล์เอกสารเป้าหมายที่คุณต้องการเปรียบเทียบ
4. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับพื้นฐานของการเขียนโปรแกรม C# จะช่วยให้คุณเข้าใจตัวอย่างโค้ดที่ให้มา

## นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโครงการของคุณ:

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอาต์พุตและชื่อไฟล์

ก่อนอื่นให้ระบุว่าเอกสารที่เปรียบเทียบจะถูกบันทึกที่ไหนและชื่อ:

```csharp
string outputDirectory = "Your Document Directory"; // เช่น "C:\\Documents"
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```

## ขั้นตอนที่ 2: เริ่มต้นวัตถุ Comparer

 สร้าง`Comparer` อินสแตนซ์ที่ใช้เส้นทางไปยังเอกสารต้นฉบับของคุณ:

```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
 นี่คือการเริ่มต้น`Comparer` วัตถุซึ่งเป็นพื้นฐานสำหรับการเปรียบเทียบเอกสารของคุณ

## ขั้นตอนที่ 3: เพิ่มเอกสารเป้าหมาย

จากนั้นรวมเอกสารเป้าหมายลงในการเปรียบเทียบ:

```csharp
comparer.Add("TARGET.docx");
```
ขั้นตอนนี้ระบุเอกสารที่คุณต้องการเปรียบเทียบกับแหล่งที่มา

## ขั้นตอนที่ 4: เปรียบเทียบเอกสารและบันทึกแหล่งข้อมูลเมตา

ตอนนี้ถึงเวลาดำเนินการเปรียบเทียบและบันทึกแหล่งข้อมูลเมตาของเอกสาร:

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
 ที่นี่`Compare`วิธีการเปรียบเทียบเอกสารต้นฉบับและเอกสารเป้าหมาย โดยใช้`CloneMetadataType`คุณแน่ใจว่าข้อมูลเมตาจากเอกสารต้นทางได้รับการเก็บรักษาไว้

## ขั้นตอนที่ 5: แสดงข้อความเอาท์พุต

หลังจากการเปรียบเทียบเสร็จสิ้น ให้ส่งข้อเสนอแนะเกี่ยวกับการดำเนินการ:

```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
ข้อความนี้ยืนยันการเปรียบเทียบสำเร็จ และระบุว่าจะค้นหาเอกสารผลลัพธ์ได้ที่ใด

## บทสรุป

การเปรียบเทียบ GroupDocs สำหรับ .NET เป็นเครื่องมืออันทรงคุณค่าสำหรับการทำงานเปรียบเทียบเอกสารภายในแอปพลิเคชัน .NET เมื่อปฏิบัติตามคู่มือนี้ คุณจะได้เรียนรู้วิธีการบันทึกแหล่งข้อมูลเมตาของเอกสารอย่างมีประสิทธิภาพ ซึ่งจะช่วยปรับปรุงกระบวนการเปรียบเทียบเอกสารและประสิทธิภาพโดยรวมของคุณ

## คำถามที่พบบ่อย

### การเปรียบเทียบ GroupDocs สำหรับ .NET สามารถเปรียบเทียบเอกสารที่มีรูปแบบต่างกันได้หรือไม่

ใช่ รองรับรูปแบบต่างๆ มากมาย รวมถึง DOCX, PDF, PPTX และอื่นๆ อีกมากมาย

### มีเวอร์ชันทดลองใช้งานไหม?

 คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ได้จาก[ที่นี่](https://releases.groupdocs.com/).

### ฉันสามารถปรับแต่งรูปแบบผลลัพธ์ของเอกสารที่เปรียบเทียบได้หรือไม่

แน่นอน! การเปรียบเทียบ GroupDocs ช่วยให้ปรับแต่งรูปแบบผลลัพธ์ได้อย่างกว้างขวาง

### มีการสนับสนุนด้านเทคนิคให้ผู้ใช้หรือไม่?

 ใช่ คุณสามารถขอความช่วยเหลือได้ผ่านทาง[ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/comparison/12).

### ฉันสามารถซื้อใบอนุญาตได้ที่ไหน?

 สามารถซื้อใบอนุญาตได้จากเว็บไซต์ GroupDocs[ที่นี่](https://purchase.groupdocs.com/buy).