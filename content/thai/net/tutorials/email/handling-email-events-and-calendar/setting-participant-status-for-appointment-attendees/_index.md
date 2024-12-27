---
title: การกำหนดสถานะผู้เข้าร่วมสำหรับผู้เข้าร่วมการนัดหมายด้วย C#
linktitle: การกำหนดสถานะผู้เข้าร่วมสำหรับผู้เข้าร่วมการนัดหมายด้วย C#
second_title: API การประมวลผลอีเมล Aspose.Email .NET
description: เรียนรู้วิธีจัดการสถานะผู้เข้าร่วมประชุมโดยใช้ C# และ Aspose.Email สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมโค้ดต้นฉบับ
type: docs
weight: 16
url: /th/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## การแนะนำ

Aspose.Email สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพและมีคุณสมบัติมากมายซึ่งออกแบบมาเพื่อปรับปรุงการจัดการอีเมลในแอปพลิเคชัน .NET คู่มือนี้ให้คำแนะนำทีละขั้นตอนในการสร้างและจัดการการนัดหมาย การเพิ่มผู้เข้าร่วม และการกำหนดสถานะของผู้เข้าร่วม เพื่อให้แน่ใจว่าสามารถบูรณาการกับโครงการ .NET ของคุณได้อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- การติดตั้ง Visual Studio หรือ C# IDE ที่เข้ากันได้
- เวอร์ชันล่าสุดของไลบรารี Aspose.Email สำหรับ .NET
- ความรู้พื้นฐานเกี่ยวกับ C# และการเขียนโปรแกรมเชิงวัตถุ

 สำหรับการติดตั้งห้องสมุด โปรดดูที่[หน้าดาวน์โหลด](https://releases.aspose.com/).

## นำเข้าเนมสเปซที่จำเป็น

ในการเริ่มต้น ให้รวมเนมสเปซที่จำเป็นสำหรับการเข้าถึงฟังก์ชันการทำงานสำหรับการจัดการการนัดหมายและส่วนประกอบอีเมล

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## สร้างอินสแตนซ์การนัดหมาย

การนัดหมายใน Aspose.Email แสดงถึงเหตุการณ์ที่กำหนดไว้ เช่น การประชุมหรือภารกิจต่างๆ วิธีสร้างการนัดหมายมีดังนี้:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- ตำแหน่ง: ระบุตำแหน่งที่การนัดหมายจะเกิดขึ้น
- StartTime และ EndTime: กำหนดระยะเวลาการนัดหมาย
- ผู้จัดและผู้เข้าร่วม: กำหนดผู้เข้าร่วมและบทบาทของพวกเขา

## การเพิ่มผู้เข้าร่วมในการนัดหมาย

Aspose.Email ช่วยให้คุณสามารถจัดการผู้เข้าร่วมโดยใช้โปรแกรมโดยใช้ที่อยู่อีเมลและสถานะการมีส่วนร่วมของพวกเขา

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## การจัดการสถานะผู้เข้าร่วม

 การ`ParticipantStatus` คุณสมบัติช่วยกำหนดว่าผู้เข้าร่วมได้ยอมรับ ปฏิเสธ หรือยอมรับคำเชิญนัดหมายอย่างชั่วคราวหรือไม่ ใช้ค่าการแจกแจงต่อไปนี้:

- ได้รับการยอมรับ
- ปฏิเสธ
- เบื้องต้น

ตัวอย่าง:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## การส่งการนัดหมายเป็นการเชิญประชุม

เมื่อเตรียมการนัดหมายเรียบร้อยแล้ว คุณสามารถส่งเป็นอีเมลเชิญได้:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## บทสรุป

Aspose.Email สำหรับ .NET ช่วยลดความซับซ้อนในการจัดการการนัดหมายในแอปพลิเคชัน .NET โดยให้เครื่องมือสำหรับการสร้าง ปรับแต่ง และจัดการกิจกรรมตามกำหนดการอย่างมีประสิทธิภาพ ด้วย API ที่ใช้งานง่าย คุณสามารถปรับกระบวนการสื่อสารให้เหมาะสมและรับรองการบูรณาการที่ราบรื่น

## คำถามที่พบบ่อย

### Aspose.Email สำหรับ .NET คืออะไร?

Aspose.Email สำหรับ .NET เป็นไลบรารีที่ครอบคลุมสำหรับการจัดการข้อความอีเมล การนัดหมาย และฟังก์ชันอื่นๆ ที่เกี่ยวข้องในแอปพลิเคชัน .NET

### ฉันสามารถปรับแต่งคุณสมบัติการนัดหมายได้หรือไม่

ใช่ คุณสมบัติเช่นตำแหน่ง เวลาเริ่มต้น และผู้เข้าร่วมสามารถปรับแต่งได้อย่างเต็มที่

### ห้องสมุดรองรับการนัดหมายแบบต่อเนื่องหรือไม่?

ใช่ Aspose.Email สำหรับ .NET รองรับการนัดหมายแบบเกิดซ้ำโดยใช้ API รูปแบบการเกิดซ้ำ

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Email สำหรับ .NET ได้จากที่ไหน

 คุณสามารถเข้าถึงเอกสารรายละเอียดและการสนับสนุนจากชุมชนได้ที่[หน้าสนับสนุน](https://forum.aspose.com/c/email/11).