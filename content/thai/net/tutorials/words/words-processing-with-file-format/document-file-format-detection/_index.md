---
title: การตรวจจับรูปแบบไฟล์เอกสาร
linktitle: การตรวจจับรูปแบบไฟล์เอกสาร
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีการตรวจจับและจัดการไฟล์เอกสารรูปแบบต่างๆ ได้อย่างราบรื่นโดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำโดยละเอียดของเราซึ่งมีตัวอย่างที่เป็นประโยชน์ เคล็ดลับ และคำถามที่พบบ่อย
type: docs
weight: 10
url: /th/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## การแนะนำ

การจัดการและจัดระเบียบรูปแบบเอกสารต่างๆ อย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญในโลกดิจิทัลในปัจจุบัน Aspose.Words for .NET นำเสนอโซลูชันที่มีประสิทธิภาพในการตรวจจับและประมวลผลไฟล์ประเภทต่างๆ ในคู่มือนี้ เราจะเจาะลึกกระบวนการตรวจจับรูปแบบเอกสารทีละขั้นตอน เพื่อให้มั่นใจถึงความถูกต้องแม่นยำ และประหยัดเวลาอันมีค่า

## ข้อกำหนดเบื้องต้นสำหรับการตรวจจับเอกสาร

ก่อนที่จะเริ่มต้น โปรดตรวจสอบให้แน่ใจว่าได้ปฏิบัติตามข้อกำหนดต่อไปนี้:

1. Aspose.Words สำหรับไลบรารี .NET  
    ดาวน์โหลดห้องสมุดได้จาก[การเปิดตัวคำศัพท์ Aspose](https://releases.aspose.com/words/net/) และเปิดใช้งานโดยใช้ใบอนุญาตที่ถูกต้อง สำหรับใบอนุญาตชั่วคราว โปรดไปที่[ใบอนุญาตชั่วคราว Aspose](https://purchase.aspose.com/temporary-license/).

2. สภาพแวดล้อมการพัฒนา  
   ใช้ Visual Studio (เวอร์ชันใดๆ ล่าสุด) พร้อมติดตั้ง .NET Framework

3. การตั้งค่าไฟล์พื้นฐาน  
   จัดระเบียบไฟล์อินพุตของคุณและเตรียมไดเร็กทอรีสำหรับการเรียงลำดับรูปแบบที่ตรวจพบ

## นำเข้าเนมสเปซที่จำเป็น

รวมเนมสเปซเหล่านี้ไว้ในตอนเริ่มต้นโปรแกรมของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

การนำเข้าเหล่านี้ช่วยให้สามารถเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการตรวจจับรูปแบบไฟล์

## ขั้นตอนที่ 1: เริ่มต้นไดเรกทอรีสำหรับผลลัพธ์ที่จัดระเบียบ

สร้างไดเร็กทอรีสำหรับจัดเก็บไฟล์ตามรูปแบบที่ตรวจพบ

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

// ให้แน่ใจว่ามีไดเร็กทอรีอยู่
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

โครงสร้างนี้ช่วยให้การจัดการไฟล์ง่ายขึ้น

## ขั้นตอนที่ 2: ดึงข้อมูลรายการไฟล์

กรองเอกสารที่เสียหายหรือไม่ได้รับการสนับสนุนออกเพื่อปรับปรุงการประมวลผล

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

รายการที่กรองจะช่วยให้คุณแน่ใจว่าจะทำงานเฉพาะกับไฟล์ที่ถูกต้องเท่านั้น

## ขั้นตอนที่ 3: ตรวจจับและจัดหมวดหมู่รูปแบบไฟล์

วนซ้ำผ่านแต่ละไฟล์เพื่อระบุรูปแบบและย้ายไปยังไดเร็กทอรีที่เหมาะสม

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    // รูปแบบเอาท์พุตที่ตรวจพบ
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

 การ`FileFormatUtil.DetectFileFormat` วิธีการนี้เป็นศูนย์กลางในการระบุคุณลักษณะของเอกสาร

## บทสรุป

การใช้ประโยชน์จาก Aspose.Words สำหรับ .NET ช่วยให้การตรวจจับรูปแบบไฟล์เอกสารกลายเป็นงานที่ง่ายดาย ความสามารถในการระบุและจัดหมวดหมู่รูปแบบต่างๆ ช่วยให้การจัดการเอกสารเป็นไปอย่างราบรื่น เพิ่มประสิทธิภาพการทำงานและประสิทธิภาพเวิร์กโฟลว์

## คำถามที่พบบ่อย

### จุดประสงค์หลักของการตรวจจับรูปแบบเอกสารคืออะไร  
การตรวจจับรูปแบบจะช่วยปรับปรุงการจัดการเอกสารโดยจัดหมวดหมู่ไฟล์สำหรับเวิร์กโฟลว์หรือแอปพลิเคชันเฉพาะ

### Aspose.Words รองรับไฟล์เข้ารหัสหรือไม่  
ใช่ สามารถตรวจจับการเข้ารหัสและประมวลผลเอกสารที่เข้ารหัสได้อย่างเหมาะสม

### ฉันสามารถขยายโซลูชันนี้สำหรับประเภทไฟล์อื่นได้หรือไม่  
ใช่ คุณสามารถปรับเปลี่ยนโค้ดเพื่อรวมรูปแบบเพิ่มเติมหรือรวมไลบรารี Aspose อื่นๆ ได้

### ฉันจะจัดการกับรูปแบบที่ไม่รู้จักได้อย่างไร  
จัดเก็บรูปแบบที่ไม่รู้จักแยกต่างหากสำหรับการตรวจสอบด้วยตนเองหรือการประมวลผลเพิ่มเติมด้วยเครื่องมือเฉพาะทาง

### ฉันสามารถหาเอกสารเพิ่มเติมได้ที่ไหน  
 เยี่ยมชม[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) สำหรับคำแนะนำและตัวอย่างที่ครอบคลุม
