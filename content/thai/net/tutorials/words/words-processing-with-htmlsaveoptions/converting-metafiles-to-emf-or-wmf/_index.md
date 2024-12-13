---
title: การแปลงเมตาไฟล์เป็น EMF หรือ WMF
linktitle: การแปลงเมตาไฟล์เป็น EMF หรือ WMF
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการแปลงภาพ SVG เป็นรูปแบบ EMF หรือ WMF ในเอกสาร Word ได้อย่างราบรื่นโดยใช้ Aspose.Words สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ดเพื่อให้ได้ผลลัพธ์ที่แม่นยำและเข้ากันได้
type: docs
weight: 10
url: /th/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## การแนะนำ

การจัดการและแปลงรูปแบบภาพอย่างมีประสิทธิภาพถือเป็นส่วนสำคัญในการสร้างเอกสาร Word ระดับมืออาชีพ ในคู่มือนี้ เราจะเจาะลึกการใช้ Aspose.Words สำหรับ .NET เพื่อแปลงภาพ SVG เป็นรูปแบบ EMF (Enhanced Metafile) หรือ WMF (Windows Metafile) เพื่อการผสานรวมที่ราบรื่น บทช่วยสอนนี้ให้คำแนะนำแบบทีละขั้นตอนที่ชัดเจนเพื่อช่วยให้นักพัฒนาสามารถใช้งานการแปลงได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้นสำหรับการแปลง SVG เป็น EMF หรือ WMF

เพื่อให้แน่ใจว่าประสบการณ์การพัฒนาจะราบรื่น โปรดยืนยันว่ามีการปฏิบัติตามข้อกำหนดเบื้องต้นต่อไปนี้:

-  Aspose.Words สำหรับ .NET: รับเวอร์ชันล่าสุดจาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: ตรวจสอบการติดตั้ง .NET Framework (หรือ .NET Core/5/6 ขึ้นอยู่กับสภาพแวดล้อมของคุณ)
- สภาพแวดล้อมการพัฒนา: แนะนำให้ใช้ Visual Studio เนื่องจากมีคุณลักษณะที่แข็งแกร่ง
- ความสามารถด้าน C#: ความคุ้นเคยพื้นฐานกับการเขียนโปรแกรม C# ถือเป็นสิ่งจำเป็น

## การนำเข้าเนมสเปซที่จำเป็น

ในโครงการของคุณ นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสาร

ตั้งค่าเส้นทางไดเรกทอรีที่จะเก็บเอกสาร Word ของคุณ ซึ่งเป็นสิ่งสำคัญสำหรับการจัดการไฟล์เอาต์พุตอย่างมีประสิทธิภาพ

```csharp
string dataDir = @"C:\MyDocuments\";
```

 แทนที่`@"C:\MyDocuments\"` ตามเส้นทางที่คุณต้องการ

## ขั้นตอนที่ 2: เตรียมสตริง HTML ที่มี SVG

สร้างสตริง HTML ที่ฝังเนื้อหา SVG ของคุณ ซึ่งจะทำให้ Aspose.Words สามารถแสดงผลและประมวลผล SVG ได้

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' ความกว้าง='300' ความสูง='100' viewBox='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการโหลด HTML

 เพื่อให้แน่ใจว่าการจัดการการแปลง SVG เหมาะสม ให้กำหนดค่า`HtmlLoadOptions` กับ`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## ขั้นตอนที่ 4: โหลด HTML ลงในเอกสาร Word

 ใช้ตัวเลือกโหลดที่กำหนดค่าไว้เพื่อสร้าง`Document` วัตถุจากสตริง HTML

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## ขั้นตอนที่ 5: กำหนดค่าตัวเลือกการบันทึกสำหรับ EMF/WMF

 ปรับแต่งตัวเลือกการบันทึกเพื่อกำหนดรูปแบบเมตาไฟล์ที่ต้องการ ที่นี่เราเลือก`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## ขั้นตอนที่ 6: บันทึกเอกสาร

บันทึกเอกสารโดยใช้ตัวเลือกบันทึกที่ระบุ

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

ไฟล์ผลลัพธ์จะมีเนื้อหา SVG ที่ถูกแปลงเป็นรูปแบบ EMF

## บทสรุป

บทช่วยสอนนี้ได้สาธิตวิธีการแปลงภาพ SVG เป็นรูปแบบ EMF หรือ WMF โดยใช้ Aspose.Words สำหรับ .NET โดยทำตามขั้นตอนเหล่านี้ คุณสามารถปรับปรุงความเข้ากันได้และความถูกต้องของภาพในเอกสาร Word ของคุณได้ ไม่ว่าคุณจะกำลังสร้างเอกสารอัตโนมัติหรือเตรียมรายงานคุณภาพสูง วิธีนี้จะช่วยให้ได้ผลลัพธ์ที่ราบรื่น

## คำถามที่พบบ่อย

### ฉันสามารถใช้วิธีนี้ในการประมวลผล SVG หลายไฟล์แบบแบตช์ได้หรือไม่
ใช่ คุณสามารถวนซ้ำผ่านไฟล์ HTML หลายไฟล์ที่ประกอบด้วย SVG ได้ โดยใช้กระบวนการเดียวกันในลูป

### ความแตกต่างระหว่าง EMF และ WMF คืออะไร?
EMF เป็นเวอร์ชันปรับปรุงของ WMF ซึ่งรองรับกราฟิกที่ซับซ้อนและขนาดข้อมูลที่ใหญ่ขึ้นได้ดีขึ้น

### Aspose.Words เข้ากันได้กับ .NET Core ได้หรือไม่
ใช่ Aspose.Words สำหรับ .NET รองรับ .NET Core และ .NET 5/6 จึงเหมาะกับแอปพลิเคชันข้ามแพลตฟอร์มสมัยใหม่

### ฉันสามารถเก็บรูปแบบ SVG ต้นฉบับไว้ในผลลัพธ์ได้หรือไม่
ไม่ วิธีนี้แปลง SVG เป็น EMF/WMF โดยเฉพาะ อย่างไรก็ตาม คุณสามารถเก็บ SVG ต้นฉบับไว้ได้โดยฝังลงในเอกสารโดยตรงโดยไม่ต้องแปลง

### ฉันสามารถดาวน์โหลด Aspose.Words แบบทดลองใช้ฟรีได้ที่ไหน
 คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/).