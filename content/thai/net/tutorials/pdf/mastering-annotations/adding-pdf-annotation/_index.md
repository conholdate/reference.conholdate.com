---
title: การเพิ่มคำอธิบาย PDF
linktitle: การเพิ่มคำอธิบาย PDF
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: เรียนรู้วิธีการเพิ่มคำอธิบายประกอบโดยใช้ Aspose.PDF สำหรับ .NET บทช่วยสอนแบบทีละขั้นตอนนี้ครอบคลุมทุกอย่างตั้งแต่การติดตั้งไลบรารีไปจนถึงการปรับแต่งคำอธิบายประกอบของคุณ
type: docs
weight: 10
url: /th/net/tutorials/pdf/mastering-annotations/adding-pdf-annotation/
---
## การแนะนำ

คำอธิบายประกอบช่วยเสริมความสมบูรณ์ให้กับเอกสาร PDF ทำให้เอกสารเป็นแบบโต้ตอบและให้ข้อมูล ไม่ว่าคุณจะทำงานร่วมกับผู้อื่นหรือต้องการข้อมูลเพิ่มเติมสำหรับผู้อ่าน คำอธิบายประกอบก็เป็นเครื่องมือที่จำเป็น ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการเพิ่มคำอธิบายประกอบ PDF ลงในไฟล์ PDF โดยใช้ Aspose.PDF สำหรับ .NET โดยจะแนะนำคุณในแต่ละขั้นตอนเพื่อให้แน่ใจว่าคุณจะเชี่ยวชาญในกระบวนการนี้

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.PDF สำหรับ .NET: ดาวน์โหลดไลบรารีจาก[หน้าดาวน์โหลด Aspose.PDF สำหรับ .NET](https://releases.aspose.com/pdf/net/).
- สภาพแวดล้อมการพัฒนา: ใช้ Visual Studio หรือ IDE C# ใด ๆ ตามที่คุณต้องการ
- ความรู้พื้นฐานเกี่ยวกับ C#: ถือว่ามีความคุ้นเคยกับการเขียนโปรแกรม C#
- ตัวอย่างเอกสาร PDF: ไฟล์ PDF ที่คุณจะเพิ่มคำอธิบายประกอบ

 หากคุณยังไม่ได้รับไลบรารี Aspose.PDF คุณสามารถเริ่มต้นได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือซื้อ[ใบอนุญาต](https://purchase.aspose.com/buy).

## แพ็คเกจนำเข้าที่จำเป็น

ก่อนที่จะทำการเข้ารหัส โปรดตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็น:

```csharp
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
```

เนมสเปซเหล่านี้ให้คลาสและวิธีการที่จำเป็นสำหรับการจัดการและการใส่คำอธิบายประกอบ PDF

## ขั้นตอนที่ 1: โหลดเอกสาร PDF ของคุณ

เริ่มต้นด้วยการโหลดเอกสาร PDF ที่คุณต้องการเพิ่มคำอธิบายประกอบ PDF

```csharp
// ระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "YOUR DATA DIRECTORY";
// โหลดเอกสาร PDF
Document pdfDocument = new Document(dataDir + "AddAnnotation.pdf");
```

 โค้ดสั้นๆ นี้กำหนดไดเรกทอรีสำหรับไฟล์ PDF ของคุณและโหลดลงใน`Document` วัตถุเพื่อให้สามารถแก้ไขเพิ่มเติมได้

## ขั้นตอนที่ 2: สร้างคำอธิบายประกอบ

 ต่อไปเราจะสร้าง`TextAnnotation`เหมาะสำหรับการเพิ่มความคิดเห็นหรือบันทึก

```csharp
// สร้างคำอธิบายข้อความ
TextAnnotation textAnnotation = new TextAnnotation(pdfDocument.Pages[1], new Aspose.Pdf.Rectangle(200, 400, 400, 600))
{
    Title = "Sample Annotation Title",
    Subject = "Sample Subject",
    Contents = "Sample contents for the annotation",
    Open = true,
    Icon = TextIcon.Key
};
```

-  ที่ตั้งและขนาด :`Rectangle`คลาสกำหนดตำแหน่งและขนาดของคำอธิบายประกอบบนหน้า
-  คุณสมบัติ: คุณสามารถตั้งชื่อเรื่อง หัวเรื่อง และเนื้อหาของคำอธิบายประกอบได้`Open` คุณสมบัติจะกำหนดว่าคำอธิบายประกอบจะแสดงแบบเปิดตามค่าเริ่มต้นหรือไม่
-  ไอคอน:`TextIcon.Key` เพิ่มองค์ประกอบภาพให้กับคำอธิบายประกอบ

## ขั้นตอนที่ 3: ปรับแต่งรูปลักษณ์ของคำอธิบายประกอบ

เพิ่มการมองเห็นของคำอธิบายประกอบโดยการปรับแต่งลักษณะที่ปรากฏ

```csharp
// ปรับแต่งขอบของคำอธิบายประกอบ
Border border = new Border(textAnnotation)
{
    Width = 5,
    Dash = new Dash(1, 1)
};
textAnnotation.Border = border;
textAnnotation.Rect = new Aspose.Pdf.Rectangle(200, 400, 400, 600);
```

-  เส้นขอบ : สร้าง`Border` วัตถุ โดยกำหนดความกว้างและรูปแบบ (เส้นประในกรณีนี้) เพื่อให้มองเห็นได้ชัดเจนยิ่งขึ้น

## ขั้นตอนที่ 4: เพิ่มคำอธิบายลงในหน้า PDF

ตอนนี้ถึงเวลาเพิ่มคำอธิบายประกอบลงในหน้า PDF ของคุณแล้ว

```csharp
// เพิ่มคำอธิบายลงในคอลเล็กชันคำอธิบายของหน้า
pdfDocument.Pages[1].Annotations.Add(textAnnotation);
```

บรรทัดนี้จะเพิ่มคำอธิบายประกอบที่คุณเพิ่งสร้างใหม่ลงในหน้าแรกของ PDF เพื่อรวมเข้ากับเอกสาร

## ขั้นตอนที่ 5: บันทึกเอกสาร PDF ที่อัปเดต

สุดท้ายให้บันทึกเอกสารเพื่อคงการเปลี่ยนแปลงของคุณไว้

```csharp
// บันทึกเอกสาร PDF ที่ได้รับการอัพเดต
dataDir = dataDir + "AddAnnotation_out.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nAnnotation added successfully.\nFile saved at " + dataDir);
```

รหัสนี้จะบันทึกเอกสารที่แก้ไขแล้วเป็น`AddAnnotation_out.pdf`โดยรักษาไฟล์ต้นฉบับและยืนยันการเพิ่มคำอธิบายสำเร็จ

## บทสรุป

การเพิ่มคำอธิบายประกอบใน PDF เป็นฟีเจอร์อันทรงพลังที่ทำได้ง่ายด้วย Aspose.PDF สำหรับ .NET ไม่ว่าจะเป็นการตรวจสอบเอกสารหรือบันทึกส่วนตัว คู่มือนี้จะช่วยให้คุณมีความรู้ในการสร้างและปรับแต่งคำอธิบายประกอบอย่างมีประสิทธิภาพ หากทำตามขั้นตอนเหล่านี้ คุณจะปรับปรุงการโต้ตอบและประโยชน์ของเอกสาร PDF ได้

## คำถามที่พบบ่อย

### ฉันสามารถเพิ่มคำอธิบายประเภทใดได้บ้างโดยใช้ Aspose.PDF สำหรับ .NET
คุณสามารถเพิ่มคำอธิบายต่างๆ ได้ เช่น ข้อความ ลิงก์ ไฮไลท์ และคำอธิบายตราประทับ

### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
แน่นอน! คุณสามารถปรับขนาด สี ขอบ และไอคอนของคำอธิบายประกอบของคุณได้

### เป็นไปได้ไหมที่จะเพิ่มคำอธิบายประกอบหลายรายการลงในหน้าเดียว?
ใช่ คุณสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในหน้าใดๆ ใน PDF ของคุณได้

### ฉันสามารถลบคำอธิบายประกอบหลังจากเพิ่มแล้วได้หรือไม่
 ใช่ สามารถลบคำอธิบายประกอบได้โดยใช้`Annotations.Delete`วิธีการนี้จัดทำโดย Aspose.PDF

### ฉันต้องมีใบอนุญาตเพื่อใช้ Aspose.PDF สำหรับ .NET หรือไม่?
 ใช่ ต้องมีใบอนุญาตเพื่อปลดล็อคคุณสมบัติทั้งหมดและหลีกเลี่ยงข้อจำกัด คุณยังสามารถรับได้[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อวัตถุประสงค์ในการประเมินผล