---
title: ถ่ายโอนแบบฟอร์มผู้ใช้ VBA และแมโครระหว่างเวิร์กบุ๊ก Excel
linktitle: ถ่ายโอนแบบฟอร์มผู้ใช้ VBA และแมโครระหว่างเวิร์กบุ๊ก Excel
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: ปลดล็อกพลังของระบบอัตโนมัติของ Excel ด้วยคู่มือที่ครอบคลุมนี้เกี่ยวกับการถ่ายโอนแบบฟอร์มผู้ใช้ VBA และแมโครระหว่างเวิร์กบุ๊กโดยใช้ Aspose.Cells สำหรับ .NET เหมาะสำหรับทั้งผู้เริ่มต้นและนักพัฒนาที่มีประสบการณ์
type: docs
weight: 11
url: /th/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## การแนะนำ

ยินดีต้อนรับสู่คู่มือฉบับสมบูรณ์สำหรับการปรับปรุงประสบการณ์การใช้ Excel ของคุณโดยใช้แมโคร VBA และแบบฟอร์มผู้ใช้ ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการถ่ายโอนแมโคร VBA UserForm Designer จากเวิร์กบุ๊กหนึ่งไปยังอีกเวิร์กบุ๊กหนึ่งโดยใช้ไลบรารี Aspose.Cells สำหรับ .NET อันทรงพลัง ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น คู่มือทีละขั้นตอนนี้จะช่วยให้คุณมีความรู้ในการจัดการไฟล์ Excel ด้วยโปรแกรม พร้อมหรือยังที่จะลงมือทำ เริ่มกันเลย!

## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มเขียนโค้ด เรามาตรวจสอบก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1. สภาพแวดล้อมการพัฒนา C#: สภาพแวดล้อมการทำงานสำหรับการพัฒนา C# โดยแนะนำให้ใช้ Visual Studio เป็นอย่างยิ่ง
2.  Aspose.Cells สำหรับไลบรารี .NET: อย่าลืมรวมไลบรารี Aspose.Cells ไว้ในโปรเจ็กต์ของคุณ คุณสามารถทำได้ง่ายๆ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/cells/net/).
3. ความรู้พื้นฐานเกี่ยวกับ VBA และแมโครของ Excel: ความคุ้นเคยกับ VBA และการทำงานของแมโครของ Excel จะช่วยเสริมความเข้าใจของคุณในบทช่วยสอนนี้
4. ไฟล์ Excel ที่มีแบบฟอร์มผู้ใช้: สร้างหรือรับเวิร์กบุ๊ก Excel ที่มีแบบฟอร์มผู้ใช้ (ควรมีการเปิดใช้งานแมโคร เช่น`.xlsm` ไฟล์)

## การนำเข้าแพ็คเกจที่จำเป็น
หากต้องการใช้ประโยชน์จากฟังก์ชันต่างๆ ที่ Aspose.Cells จัดให้ โปรดรวมเนมสเปซต่อไปนี้ไว้ที่ด้านบนของไฟล์ C# ของคุณ:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

เนมสเปซเหล่านี้จะทำให้คุณสามารถเข้าถึงเครื่องมืออันทรงพลังที่ฝังอยู่ในไลบรารี Aspose.Cells ได้

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีแหล่งที่มาและเอาต์พุตของคุณ
ขั้นแรก กำหนดตำแหน่งไฟล์ของคุณ:

```csharp
// กำหนดไดเรกทอรีแหล่งที่มาและเอาต์พุต
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

แทนที่เส้นทางตัวแทนด้วยไดเร็กทอรีจริงที่จัดเก็บไฟล์ของคุณ

## ขั้นตอนที่ 2: สร้างสมุดงานเป้าหมายที่ว่างเปล่า
ขั้นตอนต่อไป ให้สร้างเวิร์กบุ๊กใหม่ โดยคุณจะคัดลอกแบบฟอร์มผู้ใช้และแมโคร:

```csharp
// สร้างสมุดงานเป้าหมายที่ว่างเปล่า
Workbook target = new Workbook();
```

การดำเนินการนี้จะเป็นการเริ่มต้นเวิร์กบุ๊กเปล่า ซึ่งทำหน้าที่เป็นพื้นที่สำหรับการถ่ายโอนข้อมูลที่กำลังจะเกิดขึ้น

## ขั้นตอนที่ 3: โหลดเทมเพลตเวิร์กบุ๊กของคุณ
โหลดเวิร์กบุ๊กที่มีแบบฟอร์มผู้ใช้และแมโครของคุณ:

```csharp
// โหลดไฟล์ Excel ที่มีแบบฟอร์มผู้ใช้ VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

ปรับ`"sampleDesignerForm.xlsm"` เป็นชื่อไฟล์จริงของคุณ

## ขั้นตอนที่ 4: คัดลอกแผ่นงานไปยังสมุดงานเป้าหมาย
ตอนนี้เรามาคัดลอกเวิร์กชีตจากเทมเพลตไปยังเวิร์กบุ๊กเป้าหมาย:

```csharp
// คัดลอกแผ่นงานเทมเพลตทั้งหมดไปยังสมุดงานเป้าหมาย
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // เพิ่มข้อความในเซลล์ A2 ของเวิร์กชีตเป้าหมาย
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

โค้ดนี้จะวนซ้ำผ่านเวิร์กชีตแต่ละแผ่นในเทมเพลตและคัดลอกไปยังเวิร์กบุ๊กเป้าหมาย ทำให้แน่ใจได้ว่าข้อมูลทั้งหมดของคุณจะถูกถ่ายโอนอย่างราบรื่น

## ขั้นตอนที่ 5: คัดลอก VBA Macro จากเทมเพลต
ต่อไปเราจะคัดลอกแมโคร VBA รวมถึงโมดูล UserForm Designer ไปยังเวิร์กบุ๊กใหม่:

```csharp
// คัดลอกแบบฟอร์มผู้ใช้ VBA-Macro Designer จากเทมเพลตไปยังเป้าหมาย
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // คัดลอกรหัสโมดูล ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // คัดลอกโค้ดและข้อมูลของโมดูลอื่น ๆ
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // รับแบบฟอร์มการออกแบบของผู้ใช้
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // เพิ่มที่เก็บข้อมูลนักออกแบบลงในโครงการ VBA เป้าหมาย
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

โค้ดนี้จะช่วยให้แน่ใจว่าไม่เพียงแต่โค้ดเท่านั้น แต่ยังรวมถึงการออกแบบแบบฟอร์มผู้ใช้ด้วย ซึ่งจะช่วยรักษาฟังก์ชันการทำงานของแมโครของคุณเอาไว้

## ขั้นตอนที่ 6: บันทึกสมุดงานเป้าหมาย
หลังจากเสร็จสิ้นขั้นตอนการคัดลอกแล้ว ให้บันทึกสมุดงานใหม่ของคุณ:

```csharp
// บันทึกสมุดงานเป้าหมาย
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

แก้ไขชื่อไฟล์เอาท์พุตตามต้องการ ขั้นตอนนี้จะสร้างเวิร์กบุ๊กที่กำหนดเองซึ่งเต็มไปด้วยแมโครและแบบฟอร์มของผู้ใช้

## ขั้นตอนที่ 7: ยืนยันความสำเร็จ
สุดท้ายให้พิมพ์ข้อความแสดงความสำเร็จไปยังคอนโซล:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

แนวทางที่เรียบง่ายนี้ทำให้คุณมั่นใจได้ว่ากระบวนการของคุณดำเนินไปอย่างราบรื่น ซึ่งเป็นการยืนยันที่สำคัญถึงการทำงานหนักของคุณ!

## บทสรุป
ขอแสดงความยินดี! คุณได้เรียนรู้วิธีการคัดลอก VBA Macro User Form Designer จากเวิร์กบุ๊กหนึ่งไปยังอีกเวิร์กบุ๊กหนึ่งโดยใช้ Aspose.Cells สำหรับ .NET สำเร็จแล้ว แม้ว่าในตอนแรกอาจดูท้าทาย แต่การฝึกฝนจะทำให้คุณเชี่ยวชาญในการจัดการเวิร์กบุ๊กได้ โปรดจำไว้ว่าการเขียนโค้ดเป็นเรื่องของการทดลอง ดังนั้นอย่าลังเลที่จะสำรวจฟังก์ชันต่างๆ ในไฟล์ Excel ของคุณ หากคุณมีคำถามหรือต้องการความช่วยเหลือ ฟอรัมและเอกสารประกอบของ Aspose เป็นแหล่งข้อมูลที่ดีเยี่ยมสำหรับการสนับสนุน

## คำถามที่พบบ่อย

### Aspose.Cells รองรับ Excel เวอร์ชันใดบ้าง
Aspose.Cells รองรับรูปแบบ Excel ต่างๆ รวมถึง XLSX, XLSM, CSV และอื่นๆ

### ฉันสามารถใช้ Aspose.Cells ได้ฟรีหรือไม่?
 ใช่! คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรีเพื่อประเมินห้องสมุด:[ทดลองใช้งานฟรี](https://releases.aspose.com/).

### ฉันต้องมี Visual Studio เพื่อรันโค้ดนี้หรือไม่?
แม้ว่าจะแนะนำ Visual Studio เนื่องจากมีคุณลักษณะที่เป็นมิตรต่อผู้ใช้ แต่ IDE C# ใดๆ ที่รองรับการพัฒนา .NET ก็เพียงพอแล้ว

### ฉันสามารถหาตัวอย่างและเอกสารเพิ่มเติมได้ที่ไหน
 คุณสามารถสำรวจได้[เอกสารประกอบ Aspose.Cells](https://reference.aspose.com/cells/net/) เพื่อดูตัวอย่างเพิ่มเติมและคำอธิบายโดยละเอียด

### ฉันจะแก้ไขปัญหาการใช้งาน Aspose.Cells ได้อย่างไร
 คุณควรไปเยี่ยมชม[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/cells/9) เพื่อขอความช่วยเหลือจากชุมชนและเจ้าหน้าที่สนับสนุน Aspose