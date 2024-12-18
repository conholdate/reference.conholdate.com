---
title: ฟอร์มกล่องรวม HTML พร้อมประเภทการควบคุมที่ต้องการ
linktitle: ฟอร์มกล่องรวม HTML พร้อมประเภทการควบคุมที่ต้องการ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแทรกฟิลด์ฟอร์มกล่องรวมในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนนี้ครอบคลุมตัวเลือกการโหลด HTML ประเภทการควบคุมที่ต้องการ และเคล็ดลับการปรับแต่งขั้นสูงสำหรับการทำงานอัตโนมัติของเอกสารอย่างราบรื่น
type: docs
weight: 10
url: /th/net/tutorials/words/use-htmlloadoptions/html-combo-box-form-fields-with-preferred-control-types/
---
## การแนะนำ

ในโลกที่เปลี่ยนแปลงอย่างรวดเร็วของการทำงานอัตโนมัติของเอกสาร การผสานรวมเนื้อหา HTML เข้ากับเอกสาร Word ได้อย่างราบรื่นถือเป็นความท้าทายที่เกิดขึ้นบ่อยครั้ง การใช้ Aspose.Words สำหรับ .NET ช่วยให้เราจัดการ HTML ได้อย่างแม่นยำและแสดงผลในเอกสาร Word คู่มือนี้จะอธิบายวิธีการใช้ตัวเลือกการโหลด HTML เพื่อควบคุมวิธีแทรกฟิลด์ฟอร์มกล่องรวม เพื่อให้มั่นใจว่าการแสดงผลและการทำงานจะแม่นยำ

## ข้อกำหนดเบื้องต้น

ก่อนที่จะดำเนินการต่อ ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Words สำหรับไลบรารี .NET: ดาวน์โหลดจาก[เว็บไซต์](https://releases.aspose.com/words/net/). 
- สภาพแวดล้อมการพัฒนา: ตั้งค่า Visual Studio หรือ IDE ที่เทียบเท่า  
- ความรู้ด้านการเขียนโปรแกรม C#: ความเข้าใจในการใช้งาน C#  
- พื้นฐาน HTML: ความคุ้นเคยกับโครงสร้าง HTML โดยเฉพาะการควบคุมแบบฟอร์ม  

## การนำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็น:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

เนมสเปซเหล่านี้ให้เครื่องมือที่จำเป็นในการทำงานกับเอกสารและจัดการเนื้อหา HTML อย่างมีประสิทธิภาพ

## ขั้นตอนที่ 1: กำหนดเนื้อหา HTML

เตรียมโค้ด HTML ที่มีฟิลด์ฟอร์มคอมโบบ็อกซ์ที่คุณต้องการแทรก นี่คือตัวอย่าง:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>Option 1</option>
            <option value='val2'>Option 2</option>
        </select>
    </html>";
```

โค้ดนี้จะสร้างกล่องคอมโบง่ายๆ ที่มีตัวเลือกให้เลือกสองแบบ

## ขั้นตอนที่ 2: ระบุไดเรกทอรีเอกสาร

ระบุและกำหนดเส้นทางไดเร็กทอรีที่จะบันทึกเอกสาร การใช้ไดเร็กทอรีส่วนกลางช่วยให้การจัดการไฟล์ง่ายขึ้น

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

 แทนที่`"YOUR_DOCUMENT_DIRECTORY"` พร้อมด้วยเส้นทางโฟลเดอร์จริงบนระบบของคุณ

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการโหลด HTML

 การ`HtmlLoadOptions` คลาสใน Aspose.Words ช่วยให้เราระบุได้ว่าเนื้อหา HTML จะถูกตีความอย่างไร หากต้องการให้คอมโบบ็อกซ์แสดงผลเป็นแท็กเอกสารที่มีโครงสร้าง ให้ทำดังนี้:

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    PreferredControlType = HtmlControlType.StructuredDocumentTag
};
```

วิธีนี้จะช่วยให้แน่ใจว่ากล่องคอมโบจะปรากฏเป็นฟิลด์ฟอร์มแบบโต้ตอบในเอกสาร Word

## ขั้นตอนที่ 4: โหลด HTML ลงในเอกสาร Word

 แปลงสตริง HTML ให้เป็นสตรีมไบต์และโหลดลงใน`Document` วัตถุ แนวทางนี้ช่วยให้การแยกวิเคราะห์และการแสดงผล HTML ถูกต้องแม่นยำ

```csharp
Document doc = new Document(
    new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 ที่นี่,`MemoryStream` ใช้สำหรับจัดการเนื้อหา HTML ในหน่วยความจำ ซึ่งจะช่วยลดโอเวอร์เฮด I/O ของไฟล์

## ขั้นตอนที่ 5: บันทึกเอกสาร Word

สุดท้ายให้บันทึกเอกสาร Word ไปยังไดเร็กทอรีที่ระบุในรูปแบบที่คุณต้องการ เช่น DOCX:

```csharp
doc.Save(dataDir + "ComboBoxFormField.docx", SaveFormat.Docx);
```

ซึ่งจะสร้างไฟล์ Word ที่มีฟิลด์ฟอร์มกล่องรวมที่แสดงผลอย่างถูกต้อง

## บทสรุป

 การรวมเนื้อหา HTML โดยเฉพาะฟิลด์ฟอร์มเช่นกล่องคอมโบลงในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายเมื่อใช้งาน`HtmlLoadOptions`คู่มือนี้ช่วยให้คุณมีความรู้ในการควบคุมวิธีการเรนเดอร์องค์ประกอบต่างๆ เหล่านี้ และทำให้แน่ใจว่าเอกสารของคุณตรงตามข้อกำหนดของผู้ใช้และโครงการ

## คำถามที่พบบ่อย

###  อะไรคือ`HtmlControlType` in Aspose.Words for .NET?
`HtmlControlType` กำหนดวิธีการแสดงตัวควบคุมฟอร์ม HTML ในเอกสาร Word ตัวเลือกต่างๆ ได้แก่`StructuredDocumentTag`, `InlineText`และอื่นๆ

### ฉันสามารถปรับแต่งกล่องคอมโบหลังการเรนเดอร์ได้หรือไม่
ใช่ คุณสามารถจัดการกล่องคอมโบได้โดยใช้ API ของ Aspose.Words เช่นการเพิ่มตัวเลือกใหม่หรือเปลี่ยนคุณสมบัติ

### Aspose.Words รองรับองค์ประกอบ HTML ขั้นสูงหรือไม่
ใช่ Aspose.Words รองรับ HTML ได้อย่างแข็งแกร่ง รวมถึงตาราง แบบฟอร์ม มัลติมีเดีย และการจัดรูปแบบที่ซับซ้อน

### ฉันสามารถหาแหล่งข้อมูลเพิ่มเติมได้ที่ไหน
 เยี่ยมชม[Aspose.Words สำหรับเอกสาร .NET](https://reference.aspose.com/words/net/) สำหรับตัวอย่างโดยละเอียดและการอ้างอิง API

### มีรุ่นทดลองใช้งานฟรีไหม?
 ใช่คุณสามารถทำได้[ดาวน์โหลดทดลองใช้งานฟรี](https://releases.aspose.com/) เพื่อสำรวจ Aspose.Words สำหรับ .NET