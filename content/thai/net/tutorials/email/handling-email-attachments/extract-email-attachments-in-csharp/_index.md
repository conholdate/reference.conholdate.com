---
title: การแยกไฟล์แนบอีเมลใน C# - บทช่วยสอน Aspose.Email
linktitle: การแยกไฟล์แนบอีเมลใน C# - บทช่วยสอน Aspose.Email
second_title: API การประมวลผลอีเมล Aspose.Email .NET
description: เรียนรู้วิธีแยกไฟล์แนบอีเมลใน C# โดยใช้ Aspose.Email สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างสำหรับ PDF รูปภาพ และอื่นๆ
type: docs
weight: 14
url: /th/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## การแนะนำ

คุณเคยพบว่าตัวเองต้องดาวน์โหลดไฟล์แนบในอีเมลทีละไฟล์ด้วยตนเองหรือไม่ การทำเช่นนี้ไม่เพียงแต่ใช้เวลานานเท่านั้น แต่ยังเสี่ยงต่อข้อผิดพลาดอีกด้วย โชคดีที่ Aspose.Email สำหรับ .NET นำเสนอวิธีที่มีประสิทธิภาพและทรงพลังในการทำให้กระบวนการนี้เป็นไปโดยอัตโนมัติ ไม่ว่าคุณจะจัดการกับไฟล์ PDF รูปภาพ หรือไฟล์ประเภทอื่นใด คุณสามารถแยกไฟล์แนบได้อย่างง่ายดายโดยใช้ C#

ในคู่มือนี้ เราจะแนะนำคุณเกี่ยวกับบทช่วยสอนแบบครบถ้วน เริ่มตั้งแต่ข้อกำหนดเบื้องต้นไปจนถึงตัวอย่างที่ใช้งานได้เต็มรูปแบบ พร้อมที่จะประหยัดเวลาการทำงานด้วยตนเองเป็นเวลาหลายชั่วโมงหรือยัง มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ติดตั้ง Visual Studio ลงบนเครื่องของคุณแล้ว
-  Aspose.Email สำหรับไลบรารี .NET คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/email/net/) หรือติดตั้งผ่าน NuGet
- บัญชีอีเมลที่ถูกต้อง (รองรับ IMAP/POP3)
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

 หากคุณเพิ่งใช้งาน Aspose.Email โปรดพิจารณาส่งคำขอ[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) เพื่อปลดล็อคคุณสมบัติเต็มรูปแบบ

## แพ็คเกจนำเข้า

ก่อนจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นแล้ว เพิ่มสิ่งต่อไปนี้ที่ด้านบนของไฟล์ C#:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

เรามาแบ่งกระบวนการออกเป็นขั้นตอนย่อยๆ ปฏิบัติตามแต่ละขั้นตอนอย่างระมัดระวังเพื่อให้มั่นใจว่าจะดำเนินไปอย่างราบรื่น


## ขั้นตอนที่ 1: ตั้งค่าไคลเอนต์ IMAP ของคุณ

ขั้นตอนแรกคือการเชื่อมต่อกับเซิร์ฟเวอร์อีเมลของคุณโดยใช้โปรโตคอล IMAP IMAP ช่วยให้เราเข้าถึงและดึงข้อความอีเมลจากเซิร์ฟเวอร์ได้

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  แทนที่`imap.example.com` ด้วยที่อยู่เซิร์ฟเวอร์ IMAP ของผู้ให้บริการอีเมลของคุณ (เช่น`imap.gmail.com` สำหรับ Gmail)
-  ใช้อีเมลจริงของคุณ`username` และ`password`.
- `SelectFolder(ImapFolderInfo.InBox)`ระบุว่าเราต้องการทำงานกับกล่องจดหมาย


## ขั้นตอนที่ 2: ดึงอีเมลจากกล่องจดหมาย

เมื่อเชื่อมต่อแล้ว คุณต้องดึงข้อความอีเมลจากกล่องจดหมาย Aspose.Email มีวิธีง่ายๆ ในการแสดงรายการข้อความทั้งหมด

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` ดึงข้อมูลเมตาของอีเมลทั้งหมดในกล่องจดหมาย
-  การ`ImapMessageInfoCollection` วัตถุประกอบด้วยรายละเอียด เช่น ผู้ส่ง หัวเรื่อง และ ID เฉพาะ


## ขั้นตอนที่ 3: ดึงข้อความอีเมลแต่ละฉบับ

หากต้องการเข้าถึงเนื้อหาและไฟล์แนบ คุณต้องดึงอีเมลแต่ละฉบับโดยใช้ ID เฉพาะตัว


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

-  การ`foreach` ลูปวนซ้ำผ่านข้อความทั้งหมด
- `FetchMessage()` ดึงเนื้อหาอีเมลจริงสำหรับ ID ข้อความที่กำหนด


## ขั้นตอนที่ 4: วนผ่านสิ่งที่แนบมา

 ตอนนี้คุณมีเนื้อหาอีเมลแล้ว ถึงเวลาแยกไฟล์แนบแล้ว`MailMessage` วัตถุประกอบด้วยชุดของสิ่งที่แนบมา

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

-  การ`Attachments` คุณสมบัติแสดงรายการสิ่งที่แนบมาทั้งหมดในอีเมล
-  ใช้`attachment.Name` เพื่อรับชื่อไฟล์


## ขั้นตอนที่ 5: บันทึกสิ่งที่แนบมาลงในดิสก์

สุดท้าย ให้บันทึกไฟล์แนบไว้ในเครื่องของคุณ คุณสามารถกรองไฟล์ตามประเภท ขนาด หรือเกณฑ์อื่นๆ ได้

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  แทนที่`"C:\\Attachments"`ตามเส้นทางโฟลเดอร์ที่คุณต้องการ
-  การ`attachment.Save()` วิธีการเขียนไฟล์ลงดิสก์


## ขั้นตอนที่ 6: ประมวลผลสิ่งที่แนบมาตามประเภท

หากคุณต้องจัดการไฟล์แนบต่างกันขึ้นอยู่กับประเภทของไฟล์ (เช่น PDF เทียบกับ JPEG) Aspose.Email จะช่วยทำให้เรื่องนี้เป็นเรื่องง่าย

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` ระบุประเภทไฟล์ (เช่น`application/pdf` สำหรับ PDF`image/jpeg` สำหรับรูปภาพ)
- เพิ่มตรรกะแบบกำหนดเองสำหรับประเภทไฟล์ต่างๆ ตามต้องการ


## บทสรุป

และแล้วคุณก็ทำได้! การแยกไฟล์แนบจากอีเมลไม่ใช่เรื่องที่น่าเบื่ออีกต่อไป ด้วย Aspose.Email สำหรับ .NET คุณสามารถทำให้กระบวนการนี้เป็นแบบอัตโนมัติได้ด้วยโค้ดเพียงไม่กี่บรรทัด ตั้งแต่การตั้งค่าไคลเอนต์ IMAP ไปจนถึงการบันทึกไฟล์แนบในเครื่อง คู่มือนี้ได้ครอบคลุมทุกสิ่งที่คุณต้องการเพื่อเริ่มต้นใช้งาน 

 แล้วทำไมถึงต้องรอล่ะ?[ดาวน์โหลด Aspose.Email](https://releases.aspose.com/email/net/) และเริ่มปรับกระบวนการทำงานอีเมลของคุณให้มีประสิทธิภาพวันนี้!


## คำถามที่พบบ่อย

### ฉันสามารถใช้รหัสนี้กับ Gmail หรือ Outlook ได้หรือไม่?
 ใช่ครับ เปลี่ยนแทน`imap.example.com` ด้วย Gmail (`imap.gmail.com`) หรือของ Outlook (`outlook.office365.com`) ที่อยู่เซิร์ฟเวอร์ IMAP

### ใช้ Aspose.Email ฟรีหรือไม่?
 Aspose.Email ต้องมีใบอนุญาตเพื่อใช้ฟีเจอร์ทั้งหมด คุณสามารถร้องขอได้[ทดลองใช้งานฟรี](https://releases.aspose.com/) หรือ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/).

### ฉันจะจัดการความปลอดภัยของรหัสผ่านได้อย่างไร
พิจารณาใช้ตัวแปรสภาพแวดล้อมหรือที่จัดเก็บข้อมูลรับรองที่ปลอดภัยแทนการเข้ารหัสรหัสผ่านแบบฮาร์ดโค้ด

### ฉันสามารถดึงสิ่งที่แนบมาจากรายการที่ส่งได้หรือไม่
 ใช่เพียงแค่ใช้`SelectFolder(ImapFolderInfo.Sent)` แทนกล่องจดหมาย

### Aspose.Email รองรับ POP3 หรือไม่?
แน่นอน! นอกจาก IMAP แล้ว ยังรองรับ POP3 และ SMTP อีกด้วย