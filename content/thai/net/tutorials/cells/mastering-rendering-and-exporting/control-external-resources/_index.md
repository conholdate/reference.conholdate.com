---
title: ควบคุมทรัพยากรภายนอกด้วย Aspose.Cells สำหรับ .NET
linktitle: ควบคุมทรัพยากรภายนอกด้วย Aspose.Cells สำหรับ .NET
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: ปลดล็อกศักยภาพทั้งหมดของการแปลง Excel เป็น PDF ด้วย Aspose.Cells สำหรับ .NET ในคู่มือที่ครอบคลุมนี้ เรียนรู้วิธีการจัดการทรัพยากรภายนอก เช่น รูปภาพ เพื่อให้แน่ใจว่า PDF ของคุณสะท้อนถึงความต้องการการจัดรูปแบบที่แน่นอนของคุณ
type: docs
weight: 12
url: /th/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## การแนะนำ

ในภูมิทัศน์ดิจิทัลของปัจจุบัน การแปลงสเปรดชีต Excel เป็นเอกสาร PDF ถือเป็นงานทั่วไปและจำเป็น ไม่ว่าคุณจะกำลังเตรียมรายงาน ข้อมูลทางการเงิน หรือเอกสารนำเสนอ การทำให้มั่นใจว่า PDF ของคุณสะท้อนถึงรูปแบบที่คุณต้องการถือเป็นสิ่งสำคัญ Aspose.Cells สำหรับ .NET มีไลบรารีอันทรงพลังที่ช่วยให้คุณควบคุมกระบวนการแปลงนี้ได้อย่างละเอียด โดยเฉพาะเมื่อต้องจัดการกับทรัพยากรภายนอก เช่น รูปภาพ ในคู่มือนี้ เราจะมาสำรวจวิธีการจัดการทรัพยากรภายนอกอย่างมีประสิทธิภาพระหว่างกระบวนการแปลง Excel เป็น PDF โดยใช้ Aspose.Cells มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้พร้อมแล้ว:

1. Visual Studio หรือ IDE ที่เข้ากันได้กับ .NET: นี่จะเป็นสภาพแวดล้อมการพัฒนาของคุณ
2.  Aspose.Cells สำหรับ .NET: หากคุณยังไม่ได้ติดตั้ง โปรดไปที่[ดาวน์โหลด Aspose](https://releases.aspose.com/cells/net/) หน้าเพื่อรับเวอร์ชั่นล่าสุด
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# จะเป็นประโยชน์ หากคุณต้องการคำชี้แจงเกี่ยวกับแนวคิดใดๆ โปรดค้นหา
4. ตัวอย่างไฟล์ Excel: เตรียมไฟล์ Excel เช่น "samplePdfSaveOptions_StreamProvider.xlsx" ที่มีทรัพยากรภายนอกที่คุณต้องการแปลง
5. ไฟล์รูปภาพสำหรับการทดสอบ: ใช้ไฟล์รูปภาพเช่น "newPdfSaveOptions_StreamProvider.png" เป็นทรัพยากรภายนอกในระหว่างการแปลง

## แพ็คเกจนำเข้าที่จำเป็น

ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นจากไลบรารี Aspose.Cells เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์ C# ของคุณ:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

เนมสเปซเหล่านี้ให้คลาสและวิธีการที่จำเป็นสำหรับงานของคุณ

## ขั้นตอนที่ 1: สร้างคลาสผู้ให้บริการสตรีม

 ขั้นแรก ให้สร้างคลาสผู้ให้บริการสตรีมที่ใช้งาน`IStreamProvider` อินเทอร์เฟซ คลาสนี้จะช่วยให้คุณสามารถควบคุมวิธีการโหลดทรัพยากรภายนอกได้

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // โหลดภาพลงในสตรีมหน่วยความจำ
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: วิธีการนี้ถูกเรียกเมื่อสตรีมถูกปิด โดยปัจจุบันกำลังบันทึกข้อความการดีบัก
- InitStream: วิธีนี้จะอ่านไฟล์รูปภาพภายนอกเป็นอาร์เรย์ไบต์ แปลงเป็นสตรีมหน่วยความจำ และกำหนดให้กับ`options.Stream` คุณสมบัติ.

## ขั้นตอนที่ 2: ตั้งค่าไดเร็กทอรีแหล่งที่มาและเอาต์พุต

จากนั้นกำหนดไดเร็กทอรีสำหรับไฟล์ Excel และเอาท์พุต PDF

```csharp
// ไดเรกทอรีแหล่งที่มา
string sourceDir = "Your Document Directory";
// ไดเรกทอรีผลลัพธ์
string outputDir = "Your Document Directory";
```

 แทนที่`"Your Document Directory"` ด้วยเส้นทางจริงบนระบบของคุณซึ่งไฟล์ของคุณตั้งอยู่

## ขั้นตอนที่ 3: โหลดไฟล์ Excel ของคุณ

ตอนนี้โหลดไฟล์ Excel ที่คุณต้องการสร้าง PDF

```csharp
// โหลดไฟล์ Excel ต้นฉบับที่มีรูปภาพภายนอก
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 การ`Workbook` คลาสจาก Aspose.Cells แสดงถึงไฟล์ Excel ของคุณ ซึ่งอาจมีทรัพยากรภายนอกต่างๆ เช่น รูปภาพ

## ขั้นตอนที่ 4: ตั้งค่าตัวเลือกการบันทึก PDF

ก่อนบันทึกสมุดงานเป็น PDF โปรดระบุตัวเลือกการบันทึกที่คุณต้องการ

```csharp
// ระบุตัวเลือกการบันทึก PDF - ผู้ให้บริการสตรีม
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // บันทึกแต่ละแผ่นในหน้าใหม่
};
```

 นี่จะสร้างอินสแตนซ์ของ`PdfSaveOptions` ช่วยให้คุณปรับแต่งรูปแบบ PDF ได้`OnePagePerSheet` ตัวเลือกนี้ทำให้แน่ใจว่าแผ่นงาน Excel แต่ละแผ่นจะปรากฏในหน้าแยกใน PDF ขั้นสุดท้าย

## ขั้นตอนที่ 5: กำหนดผู้ให้บริการสตรีมของคุณ

 เชื่อมต่อของคุณ`Workbook` ตัวอย่างด้วย`MyStreamProvider` ชั้นเรียนที่คุณสร้างไว้ก่อนหน้านี้

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

บรรทัดนี้จะช่วยให้แน่ใจว่าเมื่อใดก็ตามที่พบทรัพยากรภายนอกระหว่างการแปลง ผู้ให้บริการที่คุณกำหนดเองจะจัดการทรัพยากรเหล่านั้นตามนั้น

## ขั้นตอนที่ 6: บันทึกสมุดงานเป็น PDF

ตอนนี้ให้บันทึกเวิร์กบุ๊ก Excel ของคุณเป็น PDF

```csharp
// บันทึกสมุดงานเป็น PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 โดยการโทรหา`Save` วิธีการบนวัตถุเวิร์กบุ๊กและส่งไดเรกทอรีเอาต์พุตพร้อมกับตัวเลือก PDF คุณจะแปลงไฟล์ Excel เป็น PDF ที่มีการจัดรูปแบบที่ดี

## ขั้นตอนที่ 7: ยืนยันการดำเนินการสำเร็จ

สุดท้ายนี้ ถือเป็นการปฏิบัติที่ดีในการยืนยันว่ากระบวนการเสร็จสมบูรณ์แล้ว

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

ข้อความนี้จะแจ้งให้คุณทราบถึงสถานะการดำเนินการของคุณ และให้ข้อเสนอแนะที่มีประโยชน์

## บทสรุป

ตอนนี้คุณได้เชี่ยวชาญกระบวนการควบคุมทรัพยากรภายนอกระหว่างการแปลง Excel เป็น PDF โดยใช้ Aspose.Cells แล้ว! เมื่อทำตามขั้นตอนเหล่านี้ คุณจะมั่นใจได้ว่าเอกสารของคุณมีรูปภาพและองค์ประกอบภายนอกอื่นๆ อย่างถูกต้อง ส่งผลให้ผลิตภัณฑ์ขั้นสุดท้ายออกมาสมบูรณ์แบบทุกครั้ง

## คำถามที่พบบ่อย

### Aspose.Cells คืออะไร?
Aspose.Cells เป็นไลบรารีอันทรงพลังสำหรับนักพัฒนา .NET ซึ่งช่วยให้สามารถสร้าง จัดการ แปลง และเรนเดอร์ไฟล์ Excel ในรูปแบบต่างๆ ได้

### ฉันจะดาวน์โหลด Aspose.Cells ได้อย่างไร?
 คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จาก[ลิงค์ดาวน์โหลด](https://releases.aspose.com/cells/net/).

### ฉันสามารถทดลองใช้ Aspose.Cells ฟรีได้หรือไม่?
 ใช่! คุณสามารถเข้าถึงการทดลองใช้ฟรีได้โดยเข้าไปที่[หน้าทดลองใช้งานฟรี](https://releases.aspose.com/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.Cells ได้ที่ไหน
 สำหรับคำถามที่เกี่ยวข้องกับการสนับสนุน โปรดไปที่[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/cells/9).

### ฉันจะขอใบอนุญาตชั่วคราวสำหรับ Aspose.Cells ได้อย่างไร
 คุณสามารถสมัครขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).
