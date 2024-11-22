---
title: เรียนรู้การเปลี่ยนแปลงระดับโลกใน Aspose.Drawing สำหรับ .NET
linktitle: เรียนรู้การเปลี่ยนแปลงระดับโลกใน Aspose.Drawing
second_title: Aspose.Drawing .NET API - ทางเลือกอื่นสำหรับ System.Drawing.Common
description: เรียนรู้วิธีการใช้การเปลี่ยนแปลงกับองค์ประกอบที่วาดทั้งหมดภายในบริบทของกราฟิก ช่วยให้คุณสร้างเอฟเฟกต์ภาพอันน่าดึงดูดและจัดการรูปภาพได้อย่างมีประสิทธิภาพ
type: docs
weight: 10
url: /th/net/tutorials/drawing/transformations/mastering-global-transformations/
---
## การแนะนำ

ยินดีต้อนรับสู่โลกที่น่าตื่นเต้นของ Aspose.Drawing สำหรับ .NET ในบทช่วยสอนนี้ เราจะเจาะลึกแนวคิดของการแปลงทั่วโลก ซึ่งเป็นฟีเจอร์อันทรงพลังที่ช่วยให้คุณสามารถนำการแปลงไปใช้กับรายการที่วาดทั้งหมดภายในบริบทของกราฟิก ความสามารถนี้มีค่าอย่างยิ่งสำหรับการสร้างเอฟเฟกต์ภาพที่ซับซ้อนหรือการจัดการภาพในระดับที่ใหญ่กว่า

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มดำเนินการ ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  ไลบรารี Aspose.Drawing: ดาวน์โหลดและติดตั้งไลบรารี Aspose.Drawing คุณสามารถค้นหาไลบรารีดังกล่าวพร้อมเอกสารประกอบได้[ที่นี่](https://reference.aspose.com/drawing/net/).
  
- สภาพแวดล้อมการพัฒนา: จำเป็นต้องมีสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้สำหรับบทช่วยสอนนี้

เมื่อเตรียมเบื้องต้นเรียบร้อยแล้ว มาเริ่มกันเลย!

## การนำเข้าเนมสเปซที่จำเป็น

หากต้องการเข้าถึงฟังก์ชันการทำงานที่ Aspose.Drawing จัดเตรียมไว้ คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เพิ่มบรรทัดต่อไปนี้ลงในโค้ดของคุณ:

```csharp
using System.Drawing;
```

## ขั้นตอนที่ 1: สร้างบริบทบิตแมปและกราฟิก

ขั้นตอนแรกคือการสร้างบิตแมปและบริบทกราฟิกซึ่งจะทำหน้าที่เป็นผืนผ้าใบสำหรับการวาดภาพของคุณ

```csharp
// สร้างบิตแมปที่มีขนาดและรูปแบบพิกเซลที่กำหนด
Bitmap bitmap = new Bitmap(1000, 800, System.Drawing.Imaging.PixelFormat.Format32bppPArgb);

// สร้างวัตถุกราฟิกจากบิตแมป
Graphics graphics = Graphics.FromImage(bitmap);

// ล้างผ้าใบด้วยสีพื้นหลัง
graphics.Clear(Color.FromKnownColor(KnownColor.Gray));
```

## ขั้นตอนที่ 2: กำหนดการเปลี่ยนแปลงระดับโลก

ต่อไป เราจะใช้การแปลงทั่วโลกกับบริบทกราฟิก ในตัวอย่างนี้ เราจะหมุนบริบทกราฟิกทั้งหมด 15 องศา

```csharp
//ใช้การแปลงการหมุน (15 องศา)
graphics.RotateTransform(15);
```

## ขั้นตอนที่ 3: วาดรูปวงรี

เมื่อเกิดการเปลี่ยนแปลงระดับโลกขึ้น คุณสามารถวาดรูปทรงต่างๆ ที่ได้รับอิทธิพลจากการเปลี่ยนแปลงดังกล่าวได้ มาวาดรูปวงรีที่มีเส้นขอบสีน้ำเงินกัน

```csharp
// สร้างปากกาที่มีสีและความกว้างตามที่กำหนด
Pen pen = new Pen(Color.FromKnownColor(KnownColor.Blue), 2);

// วาดรูปวงรีโดยใช้ปากกาและพิกัดที่ระบุ
graphics.DrawEllipse(pen, 300, 300, 400, 200);
```

## ขั้นตอนที่ 4: บันทึกผลลัพธ์

หลังจากใช้การแปลงและวาดรูปทรงของคุณแล้ว ก็ถึงเวลาที่จะบันทึกรูปภาพที่ได้ ระบุไดเรกทอรีที่ต้องการและบันทึกรูปภาพที่แปลงแล้วของคุณ

```csharp
// บันทึกภาพที่แปลงแล้วไปยังไดเร็กทอรีที่ระบุ
bitmap.Save("Your Document Directory" + @"CoordinateSystemsTransformations\GlobalTransformation_out.png");
```

ขอแสดงความยินดี! คุณได้นำการแปลงทั่วโลกโดยใช้ Aspose.Drawing สำหรับ .NET มาใช้สำเร็จแล้ว อย่าลังเลที่จะทดลองใช้การแปลงและเอฟเฟกต์ต่างๆ เพื่อปลดล็อกศักยภาพทั้งหมดของไลบรารีกราฟิกอันทรงพลังนี้

## บทสรุป

ในบทช่วยสอนนี้ เราได้สำรวจความสามารถที่น่าสนใจของการแปลงทั่วโลกใน Aspose.Drawing สำหรับ .NET ฟีเจอร์นี้ไม่เพียงแต่ช่วยเพิ่มความสามารถในการสร้างกราฟิกที่สวยงามเท่านั้น แต่ยังเปิดโอกาสที่ไม่มีที่สิ้นสุดสำหรับแอปพลิเคชันของคุณอีกด้วย เมื่อคุณทำการทดลองต่อไป คุณจะค้นพบความคล่องตัวและพลังที่ Aspose.Drawing มอบให้

## คำถามที่พบบ่อย

### Aspose.Drawing เข้ากันได้กับ .NET Core ได้หรือไม่

ใช่ Aspose.Drawing เข้ากันได้อย่างสมบูรณ์กับ .NET Core และให้การสนับสนุนข้ามแพลตฟอร์มเพื่อตอบสนองความต้องการในการพัฒนาของคุณ

### ฉันสามารถใช้การแปลงทั่วโลกหลายรายการกับบริบทกราฟิกเดียวได้หรือไม่

แน่นอน! คุณสามารถเชื่อมโยงการเรียกการแปลงหลาย ๆ ครั้งเพื่อสร้างเอฟเฟกต์ภาพที่ซับซ้อนได้

### ฉันสามารถหาบทช่วยสอนและตัวอย่างเพิ่มเติมสำหรับ Aspose.Drawing ได้จากที่ไหน

 ตรวจสอบออก[ฟอรั่ม Aspose.Drawing](https://forum.aspose.com/c/diagram/17) สำหรับบทช่วยสอน ตัวอย่าง และการสนทนาของชุมชนมากมาย

### มีรุ่นทดลองใช้งานฟรีสำหรับ Aspose.Drawing หรือไม่

 ใช่ คุณสามารถทดลองใช้ Aspose.Drawing ได้ฟรี[ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ Aspose.Drawing ได้อย่างไร

 คุณสามารถขอรับใบอนุญาตชั่วคราวสำหรับ Aspose.Drawing ได้[ที่นี่](https://purchase.conholdate.com/temporary-license/).