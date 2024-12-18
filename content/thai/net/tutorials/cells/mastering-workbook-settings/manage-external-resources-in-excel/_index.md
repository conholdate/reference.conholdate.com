---
title: จัดการทรัพยากรภายนอกใน Excel ด้วย Aspose.Cells สำหรับ .NET
linktitle: จัดการทรัพยากรภายนอกใน Excel ด้วย Aspose.Cells สำหรับ .NET
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: ค้นพบวิธีการควบคุมทรัพยากรภายนอกในเวิร์กบุ๊ก Excel ได้อย่างราบรื่นโดยใช้ Aspose.Cells สำหรับ .NET คู่มือที่ครอบคลุมนี้จะแนะนำคุณในแต่ละขั้นตอน ตั้งแต่การนำผู้ให้บริการสตรีมแบบกำหนดเองไปใช้จนถึงการเรนเดอร์เวิร์กชีต
type: docs
weight: 10
url: /th/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## การแนะนำ

เมื่อทำงานกับข้อมูลใน Excel การจัดการทรัพยากรภายนอกอย่างราบรื่นสามารถเพิ่มประสิทธิภาพการทำงานของแอปพลิเคชันของคุณได้อย่างมาก หากคุณต้องการควบคุมรูปภาพและองค์ประกอบภายนอกอื่นๆ ในเวิร์กบุ๊ก Excel โดยใช้ Aspose.Cells สำหรับ .NET คุณมาถูกที่แล้ว! คู่มือนี้จะแนะนำคุณทีละขั้นตอนเพื่อให้คุณสามารถใช้โซลูชันที่ปรับแต่งได้สำหรับการจัดการทรัพยากรเหล่านี้ได้อย่างง่ายดาย

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกไปในประเด็นการเขียนโค้ด ให้แน่ใจว่าคุณได้ตั้งค่าสิ่งต่อไปนี้แล้ว:

1. Visual Studio: IDE สำหรับการเขียนและทดสอบแอปพลิเคชัน .NET ขอแนะนำ Visual Studio เนื่องจากมีการสนับสนุนที่ครอบคลุมและอินเทอร์เฟซที่ใช้งานง่าย
2.  Aspose.Cells สำหรับ .NET: ดาวน์โหลดไลบรารีจาก[หน้าการเปิดตัว Aspose Cells](https://releases.aspose.com/cells/net/).
3. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับแนวคิด C# และ .NET จะช่วยให้คุณเข้าใจการใช้งานได้ดีขึ้น
4. ตั้งค่าโครงการของคุณ: ตรวจสอบให้แน่ใจว่าโครงการของคุณอ้างอิงถึงไลบรารี Aspose.Cells ซึ่งคุณสามารถเพิ่มได้ผ่านตัวจัดการแพ็กเกจ NuGet ใน Visual Studio
5. ไฟล์ตัวอย่าง: เตรียมไฟล์ Excel ตัวอย่างที่ประกอบด้วยทรัพยากรภายนอก (เช่น รูปภาพที่เชื่อมโยง) เพื่อวัตถุประสงค์ในการสาธิต

เมื่อคุณมีข้อกำหนดเบื้องต้นทั้งหมดนี้แล้ว เรามาเริ่มจัดการทรัพยากรภายนอกด้วย Aspose.Cells กันเลย

## แพ็คเกจนำเข้า
ในการเริ่มต้นเขียนโค้ด คุณจะต้องนำเข้าแพ็คเกจที่จำเป็นลงในไฟล์ C# ของคุณ นี่คือสิ่งที่คุณต้องการ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรี

ขั้นแรก ให้ระบุไดเร็กทอรีแหล่งที่มาและเอาต์พุตที่จัดเก็บไฟล์ของคุณ และตำแหน่งที่คุณต้องการบันทึกไฟล์เอาต์พุต

```csharp
// กำหนดไดเรกทอรีแหล่งที่มา
static string sourceDir = @"C:\Path\To\Your\Documents\"; // ปรับแต่งเส้นทาง
// กำหนดไดเรกทอรีเอาท์พุต
static string outputDir = @"C:\Path\To\Your\Output\";
```

ตรวจสอบให้แน่ใจว่าคุณได้แทนที่เส้นทางด้วยไดเร็กทอรีจริงบนเครื่องของคุณ

### ขั้นตอนที่ 2: นำอินเทอร์เฟซ IStreamProvider มาใช้

 ขั้นตอนต่อไป ให้สร้างคลาสแบบกำหนดเองที่ใช้งาน`IStreamProvider` อินเทอร์เฟซ คลาสนี้จะจัดการวิธีการเข้าถึงทรัพยากรภายนอก เช่น รูปภาพ

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // ทำความสะอาดทรัพยากรหากจำเป็น
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // เปิดสตรีมไฟล์สำหรับทรัพยากรภายนอก
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 ใน`InitStream` วิธีการนี้เราเปิดไฟล์ที่ทำหน้าที่เป็นทรัพยากรภายนอกของคุณและกำหนดให้กับ`Stream` คุณสมบัติ.

### ขั้นตอนที่ 3: โหลดไฟล์ Excel

ตอนนี้เรามาโหลดเวิร์กบุ๊ก Excel ที่รวมทรัพยากรภายนอกกัน

```csharp
public static void Execute()
{
    // โหลดไฟล์ Excel
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // กำหนดผู้ให้บริการสตรีมแบบกำหนดเอง
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

สไนปเป็ตนี้จะโหลดไฟล์ Excel ของคุณและกำหนดผู้ให้บริการสตรีมแบบกำหนดเองเพื่อจัดการทรัพยากรภายนอก

### ขั้นตอนที่ 4: เข้าถึงแผ่นงาน

หลังจากโหลดเวิร์กบุ๊กแล้ว สามารถเข้าถึงเวิร์กชีตที่ต้องการได้อย่างง่ายดาย

```csharp
    // เข้าถึงแผ่นงานแรก
    Worksheet worksheet = workbook.Worksheets[0];
```

คุณสามารถเข้าถึงเวิร์กชีตใดๆ ได้โดยการระบุดัชนี

### ขั้นตอนที่ 5: กำหนดค่าตัวเลือกภาพและการพิมพ์

กำหนดว่าคุณต้องการให้รูปภาพเอาท์พุตมีลักษณะอย่างไรโดยการกำหนดค่าตัวเลือกภาพหรือการพิมพ์

```csharp
    // ระบุตัวเลือกภาพหรือการพิมพ์
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

การเลือกใช้ PNG จะทำให้ได้ผลลัพธ์ที่คมชัด

### ขั้นตอนที่ 6: เรนเดอร์แผ่นงานเป็นรูปภาพ

ตอนนี้มาถึงส่วนที่น่าตื่นเต้นแล้ว นั่นก็คือการเรนเดอร์เวิร์กชีตเป็นไฟล์รูปภาพ!

```csharp
    // สร้างการเรนเดอร์แผ่นงานและแปลงแผ่นงานเป็นรูปภาพ
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

โค้ดนี้จะแปลงเวิร์กชีตทั้งหมดเป็นภาพ PNG ซึ่งจะถูกบันทึกไว้ในไดเร็กทอรีเอาต์พุตที่คุณระบุ

## บทสรุป

ขอแสดงความยินดี! ตอนนี้คุณได้เรียนรู้วิธีการควบคุมทรัพยากรภายนอกในไฟล์ Excel โดยใช้ Aspose.Cells สำหรับ .NET แล้ว ฟังก์ชันนี้ไม่เพียงแต่ช่วยเพิ่มความสามารถของแอปพลิเคชันของคุณเท่านั้น แต่ยังช่วยลดความซับซ้อนในการจัดการชุดข้อมูลและการนำเสนออีกด้วย คุณสามารถปรับโซลูชันนี้ให้เหมาะกับความต้องการเฉพาะของโครงการของคุณได้ด้วยการทำตามขั้นตอนที่ระบุไว้ข้างต้น

## คำถามที่พบบ่อย

### Aspose.Cells คืออะไร?
Aspose.Cells เป็นไลบรารีที่แข็งแกร่งที่ออกแบบมาสำหรับนักพัฒนา .NET เพื่อสร้าง จัดการ และจัดการไฟล์ Excel โดยไม่ต้องใช้ Microsoft Excel

### ฉันจะดาวน์โหลด Aspose.Cells สำหรับ .NET ได้อย่างไร?
 คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์อาโพส](https://releases.aspose.com/cells/net/).

### มีการทดลองใช้ฟรีหรือไม่?
 ใช่! Aspose เสนอให้ทดลองใช้ Aspose.Cells ฟรี ซึ่งมีให้ใช้งานบน[หน้าวางจำหน่าย](https://releases.aspose.com/cells/net/).

### Aspose.Cells รองรับไฟล์ประเภทใดบ้าง
Aspose.Cells รองรับรูปแบบ Excel ต่างๆ รวมถึง XLS, XLSX, CSV และอื่นๆ

### ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.Cells ได้ที่ไหน
 เยี่ยมชม[ฟอรั่ม Aspose](https://forum.aspose.com/c/cells/9) เพื่อความช่วยเหลือและการสนับสนุนจากชุมชน