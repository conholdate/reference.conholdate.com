---
title: การเพิ่ม Java Script ลงในไฟล์ PDF
linktitle: เพิ่มไฟล์ PDF สคริปต์ Java
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: เอกสารนี้ให้คำแนะนำที่ครอบคลุมเกี่ยวกับการเพิ่มองค์ประกอบแบบโต้ตอบ เช่น การแจ้งเตือนแบบป๊อปอัป หรือฟังก์ชันการพิมพ์อัตโนมัติลงในเอกสาร PDF โดยใช้ Aspose.PDF สำหรับ .NET
type: docs
weight: 10
url: /th/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## การแนะนำ
เอกสารนี้ให้คำแนะนำที่ครอบคลุมเกี่ยวกับการเพิ่มองค์ประกอบเชิงโต้ตอบ เช่น การแจ้งเตือนแบบป๊อปอัปหรือฟังก์ชันการพิมพ์อัตโนมัติลงในเอกสาร PDF โดยใช้ Aspose.PDF สำหรับ .NET ด้วยการใช้ประโยชน์จากความสามารถของไลบรารีนี้ คุณสามารถสร้าง PDF แบบไดนามิกและน่าสนใจที่ตอบสนองความต้องการต่างๆ ของผู้ใช้ได้

## ข้อกำหนดเบื้องต้น
 ก่อนดำเนินการต่อ โปรดตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลด Aspose.PDF เวอร์ชันล่าสุดสำหรับ .NET จาก[การเปิดตัว Aspose](https://releases.aspose.com/pdf/net/) หรือรับสิทธิ์ทดลองใช้ฟรีผ่านทางเว็บไซต์:[releases.aspose.com](http://releases.aspose.com).

คุณควรมีความเข้าใจพื้นฐานเกี่ยวกับ C# และคุ้นเคยกับสภาพแวดล้อมการพัฒนาที่คุณใช้ นอกจากนี้ หากคุณต้องการหลีกเลี่ยงข้อจำกัดระหว่างกระบวนการพัฒนาของคุณ โปรดพิจารณาซื้อใบอนุญาตชั่วคราวจาก Aspose

## การนำเข้าแพ็คเกจที่จำเป็น
ในการเริ่มเขียนโค้ด ให้ทำการนำเข้าเนมสเปซที่จำเป็นจากไลบรารี Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## ขั้นตอนที่ 1: โหลด PDF ที่มีอยู่
โหลดเอกสาร PDF ที่มีอยู่ซึ่งคุณต้องการเพิ่มองค์ประกอบแบบโต้ตอบ:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังไฟล์ PDF ของคุณ

## ขั้นตอนที่ 2: การเพิ่ม JavaScript ในระดับเอกสาร

 หากต้องการใช้สคริปต์ที่จะทริกเกอร์เมื่อเอกสารเปิด ให้สร้างอินสแตนซ์`JavascriptAction` วัตถุ:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## ขั้นตอนที่ 3: การเพิ่ม JavaScript ในระดับหน้า

 เพื่อเรียกใช้การดำเนินการเฉพาะตามการเปิดหรือปิดหน้า ให้สร้างอินสแตนซ์`JavascriptAction` วัตถุสำหรับแต่ละหน้า:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## ขั้นตอนที่ 4: บันทึกเอกสาร PDF

หากต้องการบันทึกเอกสาร PDF ที่แก้ไข ให้ระบุเส้นทางไฟล์เอาต์พุต:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## บทสรุป
หากปฏิบัติตามคำแนะนำนี้และใช้ Aspose.PDF สำหรับ .NET คุณจะสามารถปรับปรุง PDF ของคุณได้อย่างมีประสิทธิภาพด้วยองค์ประกอบแบบโต้ตอบ ไลบรารีนี้นำเสนอโซลูชันที่ครอบคลุมสำหรับการสร้างเอกสารแบบไดนามิกและน่าสนใจที่ตอบสนองความต้องการของผู้ใช้ที่หลากหลาย

## คำถามที่พบบ่อย

### ฉันสามารถเพิ่มการดำเนินการ JavaScript หลายรายการลงในหน้าต่างๆ ใน PDF ได้หรือไม่
ใช่ คุณสามารถกำหนดการดำเนินการ JavaScript ที่แตกต่างกันให้กับหน้าแต่ละหน้าหรือเอกสารทั้งหมดได้

### ฉันสามารถลบ JavaScript ออกจาก PDF หลังจากเพิ่มมันแล้วได้หรือไม่?
 ใช่ คุณสามารถลบหรือแก้ไขการดำเนินการ JavaScript ที่มีอยู่ได้โดยการล้าง`Actions` คุณสมบัติของเอกสารหรือหน้า

### ฉันสามารถใช้ฟังก์ชัน JavaScript ประเภทใดใน PDF ได้บ้าง?
คุณสามารถใช้ JavaScript ใดๆ ที่ได้รับการสนับสนุนโดยกลไก JavaScript ของ Adobe Acrobat เช่น การพิมพ์ การแจ้งเตือน และการจัดการแบบฟอร์ม

### JavaScript ทำงานในโปรแกรมดู PDF ทั้งหมดหรือไม่
การทำงานของ JavaScript ส่วนใหญ่จะทำงานในโปรแกรมอ่าน PDF ที่รองรับ PDF แบบโต้ตอบ เช่น Adobe Acrobat อย่างไรก็ตาม โปรแกรมอ่าน PDF พื้นฐานบางโปรแกรมอาจไม่รองรับ JavaScript