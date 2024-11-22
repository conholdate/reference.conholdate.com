---
title: แปลง DOCX เป็น MHTML และส่งอีเมลโดยใช้ Aspose.Words สำหรับ .NET
linktitle: แปลง DOCX เป็น MHTML และส่งอีเมลโดยใช้ Aspose.Words สำหรับ .NET
second_title: API การประมวลผลเอกสาร Aspose.Words
description: คู่มือครอบคลุมนี้มีบทช่วยสอนทีละขั้นตอนในการแปลงเอกสาร DOCX เป็นรูปแบบ MHTML และการส่งอีเมลโดยใช้ไลบรารี Aspose.Words และ Aspose.Email ใน .NET
type: docs
weight: 10
url: /th/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## การแนะนำ

ในภูมิทัศน์ดิจิทัลของปัจจุบัน การแปลงเอกสารระหว่างรูปแบบต่างๆ และการส่งอีเมลถือเป็นงานทั่วไป คู่มือนี้จะแนะนำคุณเกี่ยวกับการแปลงไฟล์ DOCX เป็นรูปแบบ MHTML และส่งทางอีเมลโดยใช้ไลบรารี Aspose.Words และ Aspose.Email อันทรงพลังสำหรับ .NET เราจะอธิบายแต่ละขั้นตอนอย่างชัดเจน เพื่อให้คุณทำตามได้อย่างง่ายดาย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มดำเนินการ ให้แน่ใจว่าคุณได้ตั้งค่าสิ่งต่อไปนี้แล้ว:

1.  Aspose.Words สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีนี้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในเครื่องของคุณแล้ว
4. เซิร์ฟเวอร์ SMTP: คุณจะต้องเข้าถึงเซิร์ฟเวอร์ SMTP เพื่อส่งอีเมล

## การนำเข้าเนมสเปซที่จำเป็น

หากต้องการใช้ Aspose.Words และ Aspose.Email ในโปรเจ็กต์ของคุณ คุณต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มคำสั่ง using ต่อไปนี้ที่ด้านบนของไฟล์ C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## ขั้นตอนที่ 1: โหลดเอกสาร DOCX

 เริ่มต้นด้วยการโหลดเอกสาร DOCX ที่คุณต้องการแปลง ใช้`Document` คลาสจาก Aspose.Words ที่จะบรรลุสิ่งนี้

```csharp
// ระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## ขั้นตอนที่ 2: บันทึกเอกสารเป็น MHTML

 ขั้นตอนต่อไปคือการแปลงเอกสารที่โหลดมาเป็นรูปแบบ MHTML ซึ่งทำได้โดยใช้`Save` วิธีการของ`Document`ระดับ.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // รีเซ็ตตำแหน่งสตรีมไปที่จุดเริ่มต้นเพื่อการอ่าน
    stream.Position = 0;
}
```

## ขั้นตอนที่ 3: สร้างข้อความอีเมล์

ตอนนี้สร้างข้อความอีเมลจากสตรีม MHTML โดยใช้ Aspose.Email คุณจะใช้`MailMessage` ชั้นเรียนสำหรับจุดประสงค์นี้

```csharp
// โหลดสตรีม MHTML ลงในข้อความอีเมล MIME ของ Aspose.Email
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## ขั้นตอนที่ 4: ส่งอีเมล

 สุดท้ายให้ส่งอีเมลโดยใช้ไคลเอนต์ SMTP กำหนดค่าไคลเอนต์ SMTP ด้วยรายละเอียดเซิร์ฟเวอร์ของคุณและใช้`Send` วิธีการส่งข้อความ

```csharp
// กำหนดค่าและส่งข้อความโดยใช้ Aspose.Email
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## บทสรุป

ขอแสดงความยินดี! คุณได้แปลงเอกสาร DOCX เป็น MHTML และส่งทางอีเมลโดยใช้ Aspose.Words และ Aspose.Email สำหรับ .NET สำเร็จแล้ว ขั้นตอนนี้เกี่ยวข้องกับการโหลดเอกสาร แปลงเป็น MHTML สร้างข้อความอีเมล และส่งผ่านไคลเอนต์ SMTP ด้วยขั้นตอนเหล่านี้ คุณสามารถทำให้การแปลงและส่งอีเมลเอกสารในแอปพลิเคชันของคุณเป็นไปอย่างอัตโนมัติและราบรื่น

## คำถามที่พบบ่อย

### ฉันสามารถใช้วิธีนี้เพื่อแปลงรูปแบบเอกสารอื่นได้หรือไม่
แน่นอน! Aspose.Words รองรับรูปแบบต่างๆ มากมาย ช่วยให้คุณแปลง DOC, DOCX, RTF และอื่นๆ เป็น MHTML ได้

### ฉันจะเพิ่มไฟล์แนบไปในอีเมล์ได้อย่างไร?
 คุณสามารถเพิ่มสิ่งที่แนบมาได้อย่างง่ายดายโดยใช้`Attachments` ทรัพย์สินของ`MailMessage`ระดับ.

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
ใช่ Aspose.Words เข้ากันได้กับ .NET Core จึงเหมาะสำหรับใช้ในแอปพลิเคชัน .NET Core

### ฉันต้องมีใบอนุญาตสำหรับ Aspose.Words และ Aspose.Email หรือไม่?
 ใช่ ห้องสมุดทั้งสองแห่งต้องมีใบอนุญาต คุณสามารถขอใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้จาก[หน้าสั่งซื้อ Aspose](https://purchase.conholdate.com/temporary-license/).

### ฉันสามารถหาเอกสารเพิ่มเติมได้ที่ไหน
 สำหรับเอกสารโดยละเอียด โปรดดูที่ Aspose.Words[ที่นี่](https://reference.aspose.com/words/net/) และ Aspose.อีเมล[ที่นี่](https://reference.aspose.com/email/net/).