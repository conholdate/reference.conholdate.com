---
title: คิวรีพื้นที่เซลล์ที่แมปกับเส้นทางแมปข้อมูล XML โดยใช้ Aspose.Cells
linktitle: คิวรีพื้นที่เซลล์ที่แมปกับเส้นทางแมปข้อมูล XML โดยใช้ Aspose.Cells
second_title: API การประมวลผล Excel ของ Aspose.Cells .NET
description: ค้นพบวิธีการทำงานกับข้อมูล XML ใน Excel ได้อย่างราบรื่นโดยใช้ Aspose.Cells สำหรับ .NET บทช่วยสอนที่ครอบคลุมนี้จะแนะนำคุณตลอดกระบวนการสอบถามพื้นที่เซลล์ที่แมปกับเส้นทาง XML ช่วยให้คุณสามารถดึงข้อมูลโดยอัตโนมัติและสร้างรายงานแบบไดนามิกได้อย่างง่ายดาย
type: docs
weight: 12
url: /th/net/tutorials/cells/master-xml-map-operations/query-cell-areas-mapped-to-xml-data-map-path/
---
## การแนะนำ

คุณเคยต้องการทำงานอย่างมีประสิทธิภาพกับข้อมูล XML ใน Excel โดยใช้ .NET หรือไม่? ด้วย Aspose.Cells สำหรับ .NET ซึ่งเป็นไลบรารีที่มีประสิทธิภาพสำหรับการจัดการสเปรดชีต การโต้ตอบกับแผนที่ XML ในไฟล์ Excel จะกลายเป็นเรื่องราบรื่น ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการสอบถามพื้นที่เฉพาะที่แมปกับเส้นทาง XML ในไฟล์ Excel ซึ่งเหมาะสำหรับการสร้างรายงานแบบไดนามิกหรือการดึงข้อมูลอัตโนมัติ มาเจาะลึกกระบวนการทีละขั้นตอนกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มเขียนโค้ด เราต้องเตรียมสิ่งต่อไปนี้:

1.  Aspose.Cells สำหรับ .NET: ดาวน์โหลด[ที่นี่](https://releases.aspose.com/cells/net/) หรือติดตั้งผ่าน NuGet
2. ไฟล์ Excel ที่แมปด้วย XML: คุณจะต้องมีไฟล์ Excel (.xlsx) ที่มีแมป XML อยู่แล้ว
3. สภาพแวดล้อมการพัฒนา: คู่มือนี้ได้รับการปรับแต่งสำหรับ Visual Studio แต่ตัวแก้ไข C# อื่นๆ ก็สามารถใช้งานได้เช่นกัน
4.  ใบอนุญาต Aspose: คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/) หากคุณต้องการอันหนึ่ง

## การตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในไฟล์โค้ดของคุณ:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;
using System.Collections;
```

การนำเข้าแพ็กเกจเหล่านี้ คุณกำลังตั้งค่าสภาพแวดล้อมของคุณเพื่อเข้าถึงและจัดการเวิร์กบุ๊กและเวิร์กชีตของเวิร์กบุ๊กนั้น

## ขั้นตอนที่ 1: โหลดไฟล์ Excel ของคุณ

ขั้นแรก คุณจะต้องโหลดไฟล์ Excel ที่มีการแมป XML:

```csharp
// กำหนดไดเรกทอรีสำหรับไฟล์ต้นฉบับ
string sourceDir = "Your Document Directory"; // อัปเดตเส้นทางให้เหมาะสม

// โหลดไฟล์ Excel
Workbook workbook = new Workbook(sourceDir + "sampleXmlMapQuery.xlsx");
```

 ที่นี่,`Workbook` แสดงไฟล์ Excel ทั้งหมดของคุณ ซึ่งคุณโหลดโดยใช้เส้นทางไฟล์

## ขั้นตอนที่ 2: เข้าถึงแผนที่ XML

เมื่อโหลดไฟล์ของคุณแล้ว ให้เข้าถึงแผนที่ XML ภายในเวิร์กบุ๊ก:

```csharp
// เข้าถึงแผนที่ XML แรกในเวิร์กบุ๊ก
XmlMap xmlMap = workbook.Worksheets.XmlMaps[0];
```

การดำเนินการนี้จะดึงข้อมูลแผนที่ XML แรกจากเวิร์กบุ๊กของคุณ หากเวิร์กบุ๊กของคุณมีแผนที่หลายรายการ ให้ปรับดัชนีตามต้องการ

## ขั้นตอนที่ 3: เลือกแผ่นงาน

ขั้นตอนต่อไปคือเข้าถึงเวิร์กชีตที่มีข้อมูล XML ที่แมปไว้:

```csharp
// เข้าถึงเวิร์กชีตแรกในเวิร์กบุ๊ก
Worksheet worksheet = workbook.Worksheets[0];
```

ในกรณีนี้ เราจะเลือกเวิร์กชีตแรก แต่คุณสามารถกำหนดเป้าหมายเป็นเวิร์กชีตอื่นตามความจำเป็นได้

## ขั้นตอนที่ 4: สอบถามแผนที่ XML

ตอนนี้เรามาค้นหาแผนที่ XML โดยใช้เส้นทาง XML กัน ตัวอย่างเช่น หากคุณต้องการดึงข้อมูลจาก`/MiscData` เส้นทางที่คุณจะทำ:

```csharp
// สอบถามแผนที่ XML โดยใช้เส้นทาง
Console.WriteLine("Querying XML Map from Path - /MiscData");
ArrayList results = worksheet.XmlMapQuery("/MiscData", xmlMap);
```

วิธีการนี้ใช้เส้นทาง XML และดึงข้อมูลที่เกี่ยวข้องลงใน ArrayList

## ขั้นตอนที่ 5: แสดงผลลัพธ์การค้นหา

ตอนนี้คุณมีข้อมูลที่สอบถามแล้ว ให้เราพิมพ์ผลลัพธ์ไปยังคอนโซล:

```csharp
// แสดงผลของการค้นหา
foreach (var result in results)
{
    Console.WriteLine(result);
}
```

ลูปนี้ช่วยให้คุณสามารถดูรายการทั้งหมดที่ดึงมาจากเส้นทาง XML

## ขั้นตอนที่ 6: สอบถามเส้นทาง XML แบบซ้อนกัน

 คุณสามารถปรับแต่งแบบสอบถามของคุณเพื่อกำหนดเป้าหมายข้อมูลที่เฉพาะเจาะจงยิ่งขึ้น ตัวอย่างเช่น หากคุณสนใจข้อมูลสีที่พบภายใต้`/MiscData/row/Color`คุณจะปรับแบบสอบถามของคุณดังนี้:

```csharp
// การสอบถามเส้นทาง XML แบบซ้อนกัน
Console.WriteLine("Querying XML Map from Path - /MiscData/row/Color");
results = worksheet.XmlMapQuery("/MiscData/row/Color", xmlMap);
```

## ขั้นตอนที่ 7: แสดงผลลัพธ์แบบสอบถามแบบซ้อน

สุดท้ายเรามาแสดงข้อมูลจากเส้นทางเฉพาะนี้:

```csharp
// ส่งออกผลลัพธ์ของแบบสอบถามเส้นทางซ้อนกัน
foreach (var result in results)
{
    Console.WriteLine(result);
}
```

ลูปนี้จะพิมพ์แต่ละรายการจากแบบสอบถามซ้อนกัน และแสดงข้อมูลเป้าหมายให้คุณเห็น

## บทสรุป

ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการค้นหาข้อมูล XML ที่แมปไว้ในไฟล์ Excel โดยใช้ Aspose.Cells สำหรับ .NET ความสามารถนี้มีประโยชน์อย่างยิ่งสำหรับนักพัฒนาที่ต้องการดึงข้อมูล XML เฉพาะอย่างไดนามิก ด้วยความรู้พื้นฐานนี้ ตอนนี้คุณสามารถใช้การค้นหา XML ที่ซับซ้อนยิ่งขึ้นได้ และยังทำงานกับการแมป XML หลายรายการในโครงการ Excel ของคุณได้อีกด้วย 

## คำถามที่พบบ่อย

### ฉันสามารถแมปไฟล์ XML หลายไฟล์ในเวิร์กบุ๊ก Excel เดียวได้หรือไม่  
ใช่ Aspose.Cells รองรับการจัดการแผนที่ XML หลายรายการภายในเวิร์กบุ๊กเดียว

### จะเกิดอะไรขึ้นถ้าเส้นทาง XML ไม่มีอยู่ในแผนที่?  
 หากคุณสอบถามเส้นทางที่ไม่ถูกต้อง`XmlMapQuery` วิธีการนี้จะส่งคืน ArrayList ที่ว่างเปล่า

### ต้องมีใบอนุญาตเพื่อใช้ Aspose.Cells สำหรับ .NET หรือไม่  
 ใช่ คุณต้องมีใบอนุญาตจึงจะใช้งานได้เต็มรูปแบบ[ทดลองใช้งานฟรี](https://releases.aspose.com/) และก[ใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/) มีให้เลือกใช้ได้

### ฉันสามารถบันทึกข้อมูลที่สอบถามลงในไฟล์ Excel ใหม่ได้หรือไม่  
แน่นอน! คุณสามารถดึงข้อมูลและบันทึกลงในไฟล์ Excel อื่น หรือส่งออกไปยังรูปแบบอื่นที่รองรับโดย Aspose.Cells

### การสอบถามแผนที่ XML ได้รับการสนับสนุนในรูปแบบอื่นนอกเหนือจาก Excel (.xlsx) หรือไม่  
การแมป XML ได้รับการสนับสนุนเป็นหลักในไฟล์ .xlsx และฟังก์ชันการทำงานสำหรับรูปแบบอื่นอาจมีจำกัด