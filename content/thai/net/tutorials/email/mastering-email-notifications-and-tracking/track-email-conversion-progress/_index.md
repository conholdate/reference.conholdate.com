---
title: ติดตามความคืบหน้าการแปลงอีเมลด้วย Aspose.Email สำหรับ .NET
linktitle: ติดตามความคืบหน้าการแปลงอีเมลด้วย Aspose.Email สำหรับ .NET
second_title: API การประมวลผลอีเมล Aspose.Email .NET
description: เรียนรู้วิธีติดตามความคืบหน้าการแปลงอีเมลใน C# ทีละขั้นตอนโดยใช้ Aspose.Email สำหรับ .NET เพิ่มประสิทธิภาพโครงการของคุณด้วยบทช่วยสอนโดยละเอียดนี้
type: docs
weight: 12
url: /th/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## การแนะนำ

การจัดการเอกสารอีเมลอย่างมีประสิทธิภาพมักเกี่ยวข้องกับการติดตามความคืบหน้าของการแปลง Aspose.Email สำหรับ .NET มีเครื่องมือที่แข็งแกร่งเพื่อให้บรรลุเป้าหมายนี้ ช่วยให้นักพัฒนาสามารถจัดการการดำเนินการอีเมลได้อย่างราบรื่น บทช่วยสอนนี้จะเจาะลึกถึงวิธีติดตามความคืบหน้าในการแปลงเอกสารอีเมลใน C# โดยแบ่งกระบวนการออกเป็นขั้นตอนต่างๆ เพื่อให้เข้าใจได้ง่าย  

## ข้อกำหนดเบื้องต้น  

ก่อนที่เราจะเจาะลึกในบทช่วยสอน เรามาตรวจสอบกันก่อนว่าคุณได้ตั้งค่าทุกอย่างเรียบร้อยแล้ว:  

1.  Aspose.Email สำหรับ .NET: ดาวน์โหลดและติดตั้ง[Aspose.Email สำหรับ .NET](https://releases.aspose.com/email/net/) ห้องสมุด.  
2. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ IDE อื่นๆ ที่เข้ากันได้กับ .NET  
3. .NET Framework: ตรวจสอบให้แน่ใจว่าติดตั้ง .NET Framework 4.5 หรือใหม่กว่า  
4.  ใบอนุญาตชั่วคราว: พิจารณาการขอรับใบอนุญาต[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อสำรวจคุณสมบัติทั้งหมดของ Aspose.Email  
5.  ไฟล์อีเมลตัวอย่าง: เตรียม`.eml` ไฟล์ (เช่น`test.eml`) เพื่อใช้เป็นตัวอย่าง  

## แพ็คเกจนำเข้า  

หากต้องการใช้ Aspose.Email ในโปรเจ็กต์ของคุณ คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ  

เริ่มต้นด้วยการสร้างแอปพลิเคชันคอนโซล C# ใหม่ใน Visual Studio ซึ่งจะเป็นพื้นฐานสำหรับการนำการติดตามการแปลงเอกสารอีเมลไปใช้  
  
1. เปิด Visual Studio และสร้างโปรเจ็กต์แอปพลิเคชันคอนโซลใหม่  
2. ติดตั้งแพ็กเกจ Aspose.Email NuGet:  
```sh
Install-Package Aspose.Email
```  
3.  เพิ่ม`.eml` ไฟล์ไปยังไดเร็กทอรีโครงการของคุณ  

## ขั้นตอนที่ 2: โหลดไฟล์อีเมล์  

 ตอนนี้โหลดไฟล์อีเมลลงใน`MailMessage` วัตถุ นี่เป็นขั้นตอนแรกในการทำงานกับข้อมูลอีเมล  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: ระบุไดเรกทอรีที่ไฟล์อีเมล์ของคุณตั้งอยู่  
- `MailMessage.Load` : อ่าน`.eml` จัดเก็บไฟล์และเตรียมไว้เพื่อดำเนินการต่อไป  

## ขั้นตอนที่ 3: เริ่มต้นสตรีมหน่วยความจำ  

 ขั้นต่อไปสร้าง`MemoryStream` วัตถุที่จะเก็บข้อมูลอีเมล์ที่แปลงแล้วไว้ชั่วคราว  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 เอ`MemoryStream` ถูกใช้ที่นี่เพื่อจัดการเอาท์พุตของกระบวนการแปลงโดยไม่ต้องบันทึกข้อมูลลงในดิสก์โดยตรง  

## ขั้นตอนที่ 4: กำหนดตัวเลือกการแปลง  

 ตั้งค่า`EmlSaveOptions` พร้อมตัวจัดการความคืบหน้าแบบกำหนดเองเพื่อติดตามความคืบหน้าการแปลง  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: ระบุรูปแบบผลลัพธ์  
- `CustomProgressHandler`:กำหนดฟังก์ชันตัวจัดการแบบกำหนดเองเพื่อติดตามความคืบหน้า  

## ขั้นตอนที่ 5: บันทึกอีเมลลงในสตรีมหน่วยความจำ  

บันทึก`MailMessage` วัตถุที่ใช้ตัวเลือกที่ระบุ ทำให้สามารถใช้งานฟังก์ชันการติดตามความคืบหน้าได้  
 
```csharp
msg.Save(ms, opt);
```
 
ขั้นตอนนี้จะเริ่มกระบวนการแปลงอีเมลและส่งการอัปเดตไปยังตัวจัดการความคืบหน้า  

## ขั้นตอนที่ 6: นำตัวจัดการความคืบหน้ามาใช้  

 กำหนดความหมาย`ShowEmlConversionProgress` วิธีจัดการความคืบหน้าและแสดงไว้ในคอนโซล  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: ให้รายละเอียดเกี่ยวกับกระบวนการแปลง  
-  สวิตช์เคส: จัดการขั้นตอนต่างๆ ของการแปลง:`MimeStructureCreated`, `MimePartSaved` , และ`SavedToStream`.  

### จะคาดหวังอะไรได้บ้าง?  
เมื่อกระบวนการแปลงดำเนินไป คุณจะเห็นการอัพเดตโดยละเอียดที่พิมพ์ลงในคอนโซล เช่น:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## บทสรุป  

การติดตามความคืบหน้าการแปลงเอกสารอีเมลใน C# ไม่เคยง่ายอย่างนี้มาก่อนด้วย Aspose.Email สำหรับ .NET เมื่อทำตามบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีโหลดไฟล์อีเมล ตั้งค่าตัวจัดการความคืบหน้า และบันทึกข้อมูลอีเมลในขณะที่ตรวจสอบกระบวนการทั้งหมด ฟังก์ชันนี้ช่วยให้คุณได้รับข้อมูลและควบคุมได้ระหว่างการดำเนินการเอกสารอีเมล  

## คำถามที่พบบ่อย  

###  ฉันสามารถใช้โค้ดนี้สำหรับรูปแบบอื่นนอกเหนือจากนี้ได้หรือไม่`.eml`?  
 ใช่ครับ แก้ไข`MailMessageSaveType`เพื่อให้เหมาะกับรูปแบบอื่นๆ เช่น MSG หรือ MHTML  

### ฉันจะจัดการไฟล์อีเมล์ขนาดใหญ่ได้อย่างไร  
 พิจารณาใช้`FileStream` แทนที่จะเป็น`MemoryStream` เพื่อประสิทธิภาพที่ดียิ่งขึ้นกับไฟล์ขนาดใหญ่  

### ใบอนุญาตชั่วคราวคืออะไร และฉันจะได้รับได้อย่างไร  
 ใบอนุญาตชั่วคราวช่วยให้คุณประเมินคุณสมบัติทั้งหมดของห้องสมุดได้ฟรี รับเลย[ที่นี่](https://purchase.aspose.com/temporary-license/).  

### ฉันสามารถรวมโค้ดนี้เข้ากับแอปพลิเคชันเว็บได้หรือไม่  
ใช่แล้ว โค้ดดังกล่าวสามารถใช้งานร่วมกับแอพพลิเคชันเว็บที่ใช้ ASP.NET หรือเฟรมเวิร์กที่คล้ายคลึงกัน  

### ฉันสามารถหาแหล่งข้อมูลเพิ่มเติมได้ที่ไหน  
 ตรวจสอบออก[เอกสารประกอบ](https://reference.aspose.com/email/net/) หรือเยี่ยมชม[ฟอรั่มสนับสนุน](https://forum.aspose.com/c/email/12/) เพื่อขอความช่วยเหลือ  