---
title: การเพิ่มสารบัญลงในเอกสาร PDF
linktitle: การเพิ่มสารบัญลงในเอกสาร PDF
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: บทช่วยสอนนี้สาธิตวิธีการเพิ่มสารบัญ (TOC) ลงในเอกสาร PDF โดยใช้ Aspose.Pdf สำหรับ .NET
type: docs
weight: 40
url: /th/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## การแนะนำ

การสร้างสารบัญ (TOC) ในเอกสาร PDF จะช่วยปรับปรุงการนำทางและการเข้าถึงเอกสารได้อย่างมาก ในคู่มือนี้ เราจะสาธิตวิธีการเพิ่มสารบัญลงในไฟล์ PDF โดยใช้ Aspose.Pdf สำหรับ .NET

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1.   Aspose.PDF สำหรับ .NET: ดาวน์โหลดและติดตั้งเวอร์ชันล่าสุดจาก[ที่นี่](https://releases.aspose.com/pdf/net/).
2.  สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET เช่น Visual Studio
3.   ใบอนุญาต: ขอใบอนุญาตชั่วคราวหากจำเป็น กรุณาเยี่ยมชม[หน้าการอนุญาตสิทธิ์ Aspose.Pdf](https://asposepdf.com/developers) สำหรับข้อมูลเพิ่มเติม

การนำเข้าไลบรารีที่จำเป็น

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## ขั้นตอนที่ 1: โหลดเอกสาร PDF

โหลดไฟล์ PDF ที่มีอยู่ของคุณในตำแหน่งที่คุณต้องการเพิ่ม TOC ระบุเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## ขั้นตอนที่ 2: แทรกหน้าใหม่สำหรับ TOC

แทรกหน้าใหม่ที่จุดเริ่มต้นของเอกสาร PDF หน้านี้จะทำหน้าที่เป็นสารบัญ (TOC)

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## ขั้นตอนที่ 3: สร้างวัตถุข้อมูล TOC

สร้างวัตถุที่จะแสดงข้อมูล TOC เพิ่มชื่อเรื่องและลิงก์ไปยังวัตถุนั้นเพื่อการนำทางที่ดีขึ้น

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## ขั้นตอนที่ 4: กำหนดองค์ประกอบ TOC

กำหนดองค์ประกอบ (หรือหัวข้อ) ที่จะแสดงใน TOC องค์ประกอบเหล่านี้สามารถช่วยให้ผู้อ่านนำทางไปยังส่วนต่างๆ ที่ต้องการในเอกสารได้

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## ขั้นตอนที่ 5: สร้างหัวข้อ TOC

สร้างหัวข้อสำหรับสององค์ประกอบแรกใน TOC หัวข้อเหล่านี้จะเชื่อมโยงไปยังหน้าที่เกี่ยวข้อง

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## ขั้นตอนที่ 6: บันทึก PDF ด้วย TOC

ขั้นสุดท้ายให้บันทึกไฟล์ PDF ที่อัปเดต

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## ข้อความยืนยัน

แสดงข้อความยืนยันเพื่อให้ผู้ใช้ทราบว่ากระบวนการเสร็จสิ้นแล้ว

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## บทสรุป

ด้วย Aspose.PDF สำหรับ .NET การเพิ่มสารบัญลงใน PDF ไม่เพียงแต่ทำได้ง่ายแต่ยังปรับแต่งได้อีกด้วย ไม่ว่าคุณจะต้องสร้างลิงก์การนำทางที่เรียบง่ายหรือโครงสร้างที่ซับซ้อน เครื่องมือนี้ช่วยคุณได้ ดังนั้น ครั้งต่อไปที่คุณทำงานกับ PDF ที่ยาว อย่าลืมเพิ่มสารบัญเพื่อให้ดูเป็นมืออาชีพ

## คำถามที่พบบ่อย

### ฉันสามารถปรับแต่งลักษณะของ TOC ใน Aspose.PDF ได้หรือไม่

ใช่ คุณสามารถปรับแต่งลักษณะของ TOC ได้อย่างเต็มที่ รวมถึงรูปแบบแบบอักษร ขนาด และการจัดตำแหน่ง

### ฉันจะเพิ่มหัวข้อย่อยลงใน TOC ได้อย่างไร?

คุณสามารถเพิ่มหัวข้อย่อยได้โดยการปรับ`Heading` ระดับ (เช่น`Heading(2)`-

### สามารถอัพเดต TOC โดยอัตโนมัติหากเอกสารมีการเปลี่ยนแปลงได้หรือไม่?

ไม่ TOC จะไม่อัปเดตโดยอัตโนมัติ คุณจะต้องสร้างใหม่หากโครงสร้างเอกสารมีการเปลี่ยนแปลง

### ฉันสามารถเชื่อมโยงรายการ TOC กับเอกสารภายนอกได้หรือไม่

ใช่ คุณสามารถใช้ไฮเปอร์ลิงก์เพื่อเชื่อมโยงรายการ TOC ไปยัง PDF หรือ URL ภายนอกได้

### Aspose.PDF รองรับ TOC หลายระดับหรือไม่

ใช่ Aspose.PDF รองรับ TOC หลายระดับสำหรับเอกสารที่มีความซับซ้อนพร้อมหัวข้อย่อย
