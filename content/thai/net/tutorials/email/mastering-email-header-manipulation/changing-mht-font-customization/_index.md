---
title: การเปลี่ยนแปลงการปรับแต่งฟอนต์ MHT โดยใช้ C#
linktitle: การเปลี่ยนแปลงการปรับแต่งฟอนต์ MHT โดยใช้ C#
second_title: API การประมวลผลอีเมล Aspose.Email .NET
description: เรียนรู้วิธีการเปลี่ยนแบบอักษรระหว่างการแปลง MHT โดยใช้ Aspose.Email สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนนี้เพื่อปรับแต่งได้อย่างง่ายดาย
type: docs
weight: 11
url: /th/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## การแนะนำ

ในโลกแห่งการสื่อสารบนเว็บ ไฟล์ MHT (MHTML) เป็นวิธีที่สะดวกในการจัดเก็บและแบ่งปันเนื้อหาบนเว็บ ซึ่งประกอบด้วยรูปภาพ ลิงก์ และรูปแบบ แต่จะเกิดอะไรขึ้นเมื่อคุณต้องปรับปรุงไฟล์ MHT เหล่านั้นด้วยการเปลี่ยนแบบอักษร ด้วย Aspose.Email สำหรับ .NET งานนี้จึงกลายเป็นเรื่องง่าย ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการเปลี่ยนแบบอักษรระหว่างการแปลง MHT ทีละขั้นตอน ไม่ว่าคุณจะกำลังพัฒนาแอปพลิเคชันที่จัดการการจัดรูปแบบอีเมลหรือต้องการปรับแต่งเอกสารสำหรับธุรกิจของคุณ คู่มือนี้จะช่วยให้คุณมีความรู้ที่จำเป็น

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มเขียนโค้ด มีสิ่งสำคัญบางประการที่คุณควรเตรียมไว้:

1. Visual Studio: คุณจะต้องมีสภาพแวดล้อมการพัฒนาแบบบูรณาการ (IDE) เพื่อทำงานกับโปรเจ็กต์ C# ของคุณ
2.  Aspose.Email สำหรับไลบรารี .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารีแล้ว คุณสามารถดาวน์โหลดได้จาก[ลิงค์](https://releases.aspose.com/email/net/).
3. .NET Framework: โปรเจ็กต์ของคุณควรเข้ากันได้กับ .NET Framework โดยทั่วไป .NET Core หรือเวอร์ชันที่ใหม่กว่าจะทำงานได้ดี

เตรียมพร้อมหรือยัง? เยี่ยมเลย! มาเริ่มกันเลย

## การนำเข้าแพ็คเกจ

ก่อนอื่น ตรวจสอบให้แน่ใจว่าโครงการของคุณได้รับการตั้งค่าให้ใช้เนมสเปซที่จำเป็นแล้ว คุณจะต้องใส่สิ่งต่อไปนี้ไว้ที่ด้านบนของไฟล์ C#:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

แพ็คเกจเหล่านี้จะช่วยให้คุณเข้าถึงฟังก์ชันการทำงานที่จำเป็นในการทำงานกับไฟล์ MHT และแก้ไขเนื้อหาของไฟล์เหล่านั้น

ตอนนี้เรามาดูขั้นตอนต่างๆ ที่เกี่ยวข้องกับการเปลี่ยนแบบอักษรในระหว่างการแปลง MHT กัน

## ขั้นตอนที่ 1: โหลดไฟล์ MHT

 สิ่งแรกที่คุณต้องทำคือโหลดไฟล์ MHT ของคุณลงใน`MailMessage` วัตถุ ที่นี่คุณสามารถเข้าถึงและจัดการเนื้อหาได้

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 คำอธิบาย: ที่นี่`"input.mht"` เป็นเส้นทางไปยังไฟล์ MHT ของคุณ`MhtmlLoadOptions()`ช่วยให้คุณกำหนดค่าวิธีการโหลดไฟล์ได้ เช่น การจัดการสิ่งที่แนบมาหรือทรัพยากรที่เชื่อมโยงแตกต่างกัน

## ขั้นตอนที่ 2: ทำซ้ำผ่านมุมมองทางเลือก

ไฟล์ MHT มักมีมุมมองทางเลือกหลายแบบ โดยเฉพาะอย่างยิ่งหากมีเนื้อหา HTML คุณต้องวนซ้ำมุมมองเหล่านี้เพื่อค้นหามุมมองที่คุณต้องการแก้ไข

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 คำอธิบาย: คุณกำลังตรวจสอบแต่ละ`AlternateView` เพื่อดูว่าเป็นประเภท HTML หรือไม่ หากใช่ คุณสามารถเข้าถึง`LinkedResources`ซึ่งโดยทั่วไปจะเก็บแบบอักษรต่างๆ ที่เชื่อมโยงกับ HTML

## ขั้นตอนที่ 3: ระบุและปรับแต่งแบบอักษร

เมื่อคุณเข้าถึงทรัพยากรที่เชื่อมโยงได้แล้ว คุณสามารถระบุได้ว่าทรัพยากรใดเป็นแบบอักษรและปรับแต่งตามต้องการได้

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // เปลี่ยนเป็นแบบอักษรที่ต้องการ
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // ตรวจสอบให้แน่ใจว่ามีการเข้ารหัสอย่างถูกต้อง
    }
}
```

 คำอธิบาย: ลูปนี้จะตรวจสอบว่าประเภทเนื้อหาของทรัพยากรที่เชื่อมโยงนั้นเป็นแบบอักษร TrueType หรือไม่ หากตรงกัน คุณสามารถเปลี่ยนชื่อแบบอักษรเป็นชื่อที่คุณต้องการได้ (เช่น "Arial" ในตัวอย่างนี้)`TransferEncoding`ควรตั้งค่าเพื่อให้แน่ใจว่าข้อมูลแบบอักษรได้รับการเข้ารหัสอย่างถูกต้องเมื่อบันทึกเอกสาร

## ขั้นตอนที่ 4: บันทึกไฟล์ MHT ที่อัปเดต

หลังจากปรับแต่งแบบอักษรแล้ว ก็ถึงเวลาบันทึกไฟล์ MHT ที่คุณแก้ไขแล้ว คุณจะต้องแน่ใจว่าคุณใช้ตัวเลือกการบันทึกที่ถูกต้องเพื่อรักษาความสมบูรณ์ของไฟล์ของคุณ

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 คำอธิบาย: ในบรรทัดโค้ดนี้`"output.mht"` คือชื่อไฟล์ที่คุณต้องการบันทึกเนื้อหาที่อัปเดต โดยใช้`SaveOptions.DefaultMhtml` ช่วยให้แน่ใจว่าไฟล์ใหม่ยังคงรูปแบบ MHT

## บทสรุป

การเปลี่ยนฟอนต์ในไฟล์ MHT จะช่วยปรับปรุงรูปลักษณ์และความรู้สึกของเอกสารของคุณได้อย่างมาก ด้วยการใช้ประโยชน์จาก Aspose.Email สำหรับ .NET คุณสามารถโหลดไฟล์ MHT แก้ไขเนื้อหา และบันทึกการเปลี่ยนแปลงได้อย่างง่ายดายโดยใช้โค้ดเพียงไม่กี่บรรทัด ไม่ว่าคุณจะทำงานในโปรเจ็กต์ส่วนตัวหรือแอปพลิเคชันขนาดใหญ่ การฝึกฝนทักษะเหล่านี้จะช่วยปรับปรุงวิธีการนำเสนอข้อมูลของคุณได้

## คำถามที่พบบ่อย

### รูปแบบ MHT คืออะไร?
MHT เป็นรูปแบบเก็บถาวรหน้าเว็บที่จัดเก็บเอกสาร HTML รูปภาพ และทรัพยากรอื่นๆ ในไฟล์เดียว

### ฉันสามารถเปลี่ยนแปลงด้านอื่น ๆ ของไฟล์ MHT โดยใช้ Aspose ได้หรือไม่
แน่นอน! Aspose.Email ช่วยให้คุณแก้ไขแทบทุกแง่มุมของไฟล์ MHT รวมถึงไฟล์แนบ ส่วนหัว และอื่นๆ อีกมากมาย

### Aspose.Email สำหรับ .NET ฟรีหรือไม่?
 Aspose เสนอรุ่นทดลองใช้งานฟรี แต่เวอร์ชันเต็มต้องมีใบอนุญาต คุณสามารถรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถหาเอกสารเพิ่มเติมเกี่ยวกับ Aspose.Email ได้จากที่ใด
 คุณสามารถค้นหาเอกสารและตัวอย่างที่ครอบคลุมได้ที่[หน้าเอกสารอีเมล Aspose](https://reference.aspose.com/email/net/).

### จะเกิดอะไรขึ้นหากฉันประสบปัญหาขณะใช้ Aspose?
 หากคุณประสบปัญหาใดๆ คุณสามารถติดต่อขอความช่วยเหลือได้ที่[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/email/12/).