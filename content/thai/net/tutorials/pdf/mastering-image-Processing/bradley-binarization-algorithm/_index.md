---
title: อัลกอริธึมการไบนารีของแบรดลีย์
linktitle: อัลกอริธึมการไบนารีของแบรดลีย์
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: เรียนรู้วิธีแปลงหน้า PDF เป็นภาพ TIFF ไบนารีคุณภาพสูงโดยใช้อัลกอริทึมการแปลงไบนารีของ Bradley ใน Aspose.PDF สำหรับ .NET คำแนะนำทีละขั้นตอนนี้ประกอบด้วยตัวอย่างโค้ด
type: docs
weight: 30
url: /th/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## การแนะนำ

ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับขั้นตอนการแปลงหน้า PDF เป็นภาพ TIFF โดยใช้อัลกอริทึม Bradley Binarization Aspose.PDF สำหรับ .NET ช่วยลดความซับซ้อนของงานนี้ ช่วยให้คุณสามารถจัดการและปรับกระบวนการทำงานเอกสารของคุณให้เป็นระบบอัตโนมัติได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.PDF สำหรับ .NET: ดาวน์โหลดไลบรารีจาก[ที่นี่](https://releases.aspose.com/pdf/net/).
- Visual Studio (หรือ C# IDE ใดๆ)
- ความรู้พื้นฐานเกี่ยวกับ C#
-  ใบอนุญาตที่ถูกต้องหรือ[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) จาก Aspose

## ขั้นตอนที่ 1: ตั้งค่าโครงการของคุณ

ขั้นแรก ให้สร้างโครงการ C# ใหม่ใน IDE ของคุณและนำเข้าเนมสเปซที่จำเป็น:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## ขั้นตอนที่ 2: กำหนดไดเรกทอรีเอกสาร

ระบุเส้นทางไปยังไดเร็กทอรีที่เอกสาร PDF ของคุณตั้งอยู่ รวมทั้งเส้นทางเอาต์พุตสำหรับภาพ TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // เส้นทางไปยังไฟล์ PDF ของคุณ
```

ไดเร็กทอรีนี้จะจัดเก็บทั้งไฟล์ PDF ต้นฉบับและไฟล์ TIFF ที่แปลงแล้ว

## ขั้นตอนที่ 3: โหลดเอกสาร PDF

เปิดเอกสาร PDF ที่คุณต้องการแปลง:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 แทนที่`PageToTIFF.pdf` พร้อมชื่อไฟล์ PDF ของคุณ

## ขั้นตอนที่ 4: ระบุเส้นทางผลลัพธ์

กำหนดเส้นทางเอาต์พุตสำหรับไฟล์ TIFF ที่สร้างขึ้น:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## ขั้นตอนที่ 5: ตั้งค่าความละเอียดของภาพ

ตั้งค่าความละเอียดสำหรับภาพ TIFF DPI ที่สูงขึ้นจะทำให้ได้คุณภาพของภาพที่ดีขึ้น:

```csharp
Resolution resolution = new Resolution(300);
```

## ขั้นตอนที่ 6: กำหนดค่าการตั้งค่า TIFF

กำหนดค่าการตั้งค่าสำหรับภาพ TIFF รวมถึงการบีบอัดและความลึกของสี:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

การใช้ 1bpp (1 บิตต่อพิกเซล) จะเตรียมภาพสำหรับเอาต์พุตแบบไบนารี

## ขั้นตอนที่ 7: สร้างอุปกรณ์ TIFF

สร้างอุปกรณ์ TIFF ที่จะจัดการการแปลง:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## ขั้นตอนที่ 8: แปลงหน้า PDF เป็น TIFF

แปลงหน้าแรกของ PDF เป็นภาพ TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## ขั้นตอนที่ 9: ใช้อัลกอริทึม Bradley Binarization

ตอนนี้ ให้ใช้อัลกอริทึม Bradley เพื่อแปลงภาพ TIFF ระดับสีเทาเป็นภาพไบนารี:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 การ`BinarizeBradley` วิธีนี้ใช้สตรีมไฟล์สองสตรีม (อินพุตและเอาต์พุต) และค่าขีดจำกัด ปรับค่าขีดจำกัดตามต้องการเพื่อให้ได้ผลลัพธ์ที่ดีที่สุด

## ขั้นตอนที่ 10: ยืนยันการแปลงสำเร็จ

สุดท้ายยืนยันว่าการแปลงสำเร็จ:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## บทสรุป

ขอแสดงความยินดี! คุณได้แปลงหน้า PDF เป็นไฟล์ภาพ TIFF สำเร็จแล้ว และใช้อัลกอริทึม Bradley Binarization กับ Aspose.PDF สำหรับ .NET กระบวนการนี้มีความสำคัญสำหรับการเก็บถาวรเอกสาร OCR และแอปพลิเคชันระดับมืออาชีพอื่นๆ ด้วยความละเอียดคุณภาพสูงและการบีบอัดที่มีประสิทธิภาพ รูปภาพเอกสารของคุณจะชัดเจนและมีขนาดที่จัดการได้

## คำถามที่พบบ่อย

### แบรดลีย์อัลกอริทึมคืออะไร
อัลกอริทึมของแบรดลีย์เป็นเทคนิคการแปลงภาพเป็นไบนารีซึ่งจะแปลงภาพระดับสีเทาให้เป็นภาพไบนารีด้วยการกำหนดค่าเกณฑ์การปรับตัวสำหรับแต่ละพิกเซลตามสภาพแวดล้อมโดยรอบ

### ฉันสามารถแปลงไฟล์ PDF หลายหน้าเป็น TIFF ด้วยวิธีนี้ได้หรือไม่?
 ใช่ คุณสามารถปรับเปลี่ยนได้`Process` วิธีการวนซ้ำผ่านหน้าทั้งหมดในเอกสารเพื่อการแปลง

### ความละเอียดที่เหมาะสมที่สุดในการแปลงไฟล์ PDF เป็น TIFF คือเท่าใด
โดยทั่วไปขอแนะนำให้ใช้ความละเอียด 300 DPI สำหรับภาพคุณภาพสูง แต่คุณสามารถปรับเปลี่ยนได้ตามความต้องการเฉพาะของคุณ

### 1bpp หมายถึงอะไรในความลึกสี?
1bpp (1 บิตต่อพิกเซล) หมายถึงภาพจะเป็นสีขาวดำ โดยแต่ละพิกเซลจะเป็นสีดำสนิทหรือสีขาวสนิท

### อัลกอริทึมของ Bradley เหมาะกับ OCR หรือไม่
ใช่ อัลกอริทึม Bradley มักใช้ในการประมวลผล OCR ก่อนการประมวลผล เนื่องจากช่วยเพิ่มความคมชัดของข้อความในเอกสารที่สแกน ทำให้ความแม่นยำในการจดจำเพิ่มขึ้น