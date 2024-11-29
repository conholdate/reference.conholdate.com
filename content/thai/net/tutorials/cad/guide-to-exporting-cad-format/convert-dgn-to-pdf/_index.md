---
title: แปลง DGN เป็น PDF ใน Aspose.CAD สำหรับ .NET
linktitle: แปลง DGN เป็น PDF ใน Aspose.CAD สำหรับ .NET
second_title: Aspose.CAD .NET - รูปแบบไฟล์ CAD และ BIM
description: เรียนรู้วิธีการแปลงไฟล์ DGN เป็น PDF ได้อย่างง่ายดายโดยใช้ไลบรารี Aspose.CAD อันทรงพลังสำหรับ .NET คำแนะนำทีละขั้นตอนนี้ได้รับการออกแบบมาสำหรับนักพัฒนาในทุกระดับ
type: docs
weight: 12
url: /th/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## การแนะนำ

การนำทางโลกของไฟล์ CAD อาจเป็นเรื่องท้าทาย แต่ด้วย Aspose.CAD สำหรับ .NET นักพัฒนาสามารถจัดการและแปลงไฟล์ CAD ต่างๆ ได้อย่างง่ายดาย ความต้องการทั่วไปอย่างหนึ่งคือการแปลงไฟล์ DGN เป็น PDF ซึ่งเราจะมาเจาะลึกทีละขั้นตอนในบทช่วยสอนนี้

## ข้อกำหนดเบื้องต้น

เพื่อติดตาม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความสามารถพื้นฐานใน C# และ .NET framework
-  ติดตั้งไลบรารี Aspose.CAD สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.aspose.com/cad/net/).
- ไฟล์ DGN ตัวอย่าง (เช่น Nikon_D90_Camera.dgn) 

## ขั้นตอนที่ 1: นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่เกี่ยวข้องในโครงการ C# ของคุณ:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## ขั้นตอนที่ 2: โหลดไฟล์ DGN

ระบุไดเร็กทอรีสำหรับไฟล์ DGN ของคุณและโหลดโดยใช้โค้ดต่อไปนี้:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // การประมวลผลเพิ่มเติมจะไปที่นี่...
}
```

## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแรสเตอร์ไรเซชัน

ขั้นตอนต่อไป ให้ตั้งค่าตัวเลือกการแรสเตอร์เพื่อกำหนดว่า DGN ของคุณจะถูกแสดงใน PDF อย่างไร:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // ปรับความกว้างได้ตามต้องการ
    PageHeight = 300, // ปรับความสูงได้ตามต้องการ
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## ขั้นตอนที่ 4: สร้างตัวเลือก PDF

กำหนดตัวเลือก PDF โดยบูรณาการการตั้งค่าการแรสเตอร์ที่กำหนดค่าไว้ก่อนหน้านี้:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## ขั้นตอนที่ 5: บันทึก DGN เป็น PDF

สุดท้าย ให้บันทึกไฟล์ DGN เป็น PDF โดยใช้ตัวเลือกที่คุณกำหนดค่าไว้:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## บทสรุป

ขอแสดงความยินดี! คุณได้แปลงไฟล์ DGN เป็น PDF สำเร็จแล้วโดยใช้ Aspose.CAD สำหรับ .NET บทช่วยสอนแบบตรงไปตรงมานี้จะแนะนำคุณตลอดกระบวนการโหลดไฟล์ DGN ตั้งค่าตัวเลือกแรสเตอร์ไรเซชัน และบันทึกผลลัพธ์เป็น PDF

## คำถามที่พบบ่อย

### ฉันจำเป็นต้องมีความรู้ CAD ก่อนจึงจะใช้ Aspose.CAD ได้หรือไม่?  
แน่นอน! Aspose.CAD ถูกออกแบบมาเพื่อลดความซับซ้อนของงาน CAD ทำให้ผู้พัฒนาสามารถเข้าถึงได้ทุกคนไม่ว่าจะมีความรู้ด้าน CAD หรือไม่ก็ตาม

### ฉันสามารถหาทรัพยากรและเอกสารเพิ่มเติมสำหรับ Aspose.CAD ได้จากที่ใด  
 คุณสามารถสำรวจคำแนะนำและตัวอย่างที่ครอบคลุมได้ใน[เอกสาร Aspose.CAD](https://reference.aspose.com/cad/net/).

### มีรุ่นทดลองใช้งาน Aspose.CAD ฟรีหรือไม่  
 ใช่ สามารถทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.CAD ได้อย่างไร  
 คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.conholdate.com/temporary-license/).

### ต้องการความช่วยเหลือหรือมีคำถามหรือไม่?  
 ร่วมสนทนาได้ใน[ฟอรั่ม Aspose.CAD](https://forum.aspose.com/c/cad/19) สำหรับการสนับสนุนและสอบถามจากชุมชน