---
title: สร้างแบบจำลอง 3 มิติเบื้องต้น
linktitle: สร้างแบบจำลอง 3 มิติเบื้องต้น
second_title: API ของ Aspose.3D .NET
description: เรียนรู้วิธีการสร้างและปรับแต่งโมเดล 3 มิติแบบดั้งเดิม รวมถึงกล่องและกระบอกสูบ และบันทึกในรูปแบบ FBX ได้อย่างง่ายดาย
type: docs
weight: 10
url: /th/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## การแนะนำ

ยินดีต้อนรับสู่โลกแห่งการสร้างแบบจำลอง 3 มิติโดยใช้ Aspose.3D สำหรับ .NET ในบทช่วยสอนที่ครอบคลุมนี้ เราจะแนะนำคุณตลอดขั้นตอนการสร้างแบบจำลอง 3 มิติเบื้องต้นทีละขั้นตอน ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือผู้เริ่มต้นที่อยากเรียนรู้ คู่มือนี้จะช่วยให้คุณสร้างองค์ประกอบ 3 มิติที่สวยงามสะดุดตาสำหรับโครงการของคุณได้

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเริ่มสร้างแบบจำลอง 3 มิติ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:

-  Aspose.3D สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี Aspose.3D สำหรับ .NET จาก[หน้าดาวน์โหลด](https://releases.aspose.com/3d/net/).
  
- สภาพแวดล้อมการพัฒนา .NET: ตั้งค่าสภาพแวดล้อมที่เข้ากันได้กับ Aspose.3D เช่น Visual Studio

เมื่อเตรียมทุกอย่างเรียบร้อยแล้ว เรามาเริ่มต้นการผจญภัยการสร้างแบบจำลอง 3 มิติกันเลย!

## การนำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

เนมสเปซเหล่านี้จะมอบเครื่องมือที่จำเป็นแก่คุณในการจัดการโมเดล 3 มิติและบันทึกผลงานสร้างสรรค์ของคุณ

## ขั้นตอนที่ 1: เริ่มต้นวัตถุฉาก

สร้างวัตถุฉากใหม่ที่ทำหน้าที่เป็นผืนผ้าใบสำหรับโมเดล 3 มิติของคุณ:

```csharp
// เริ่มต้นวัตถุฉาก
Scene scene = new Scene();
```

ฉากนี้จะประกอบด้วยรูปทรงดั้งเดิมที่คุณกำลังจะสร้าง

## ขั้นตอนที่ 2: สร้างแบบจำลองกล่อง

ต่อไปเรามาเพิ่มโมเดลกล่องลงในฉากของคุณกัน:

```csharp
// สร้างแบบจำลองกล่อง
scene.RootNode.CreateChildNode("box", new Box());
```

คุณสามารถปรับแต่งขนาดและคุณสมบัติของกล่องเพื่อให้เหมาะกับวิสัยทัศน์สร้างสรรค์ของคุณได้

## ขั้นตอนที่ 3: สร้างแบบจำลองกระบอกสูบ

ตอนนี้ ปรับปรุงฉากของคุณโดยการเพิ่มกระบอกสูบ:

```csharp
// สร้างแบบจำลองกระบอกสูบ
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

เช่นเดียวกับกล่อง คุณสามารถปรับพารามิเตอร์ของกระบอกสูบเพื่อให้ได้รูปลักษณ์ที่คุณต้องการ

## ขั้นตอนที่ 4: บันทึกฉากในรูปแบบ FBX

หากต้องการรักษาโมเดล 3 มิติของคุณ ให้บันทึกในรูปแบบ FBX:

```csharp
// บันทึกรูปวาดในรูปแบบ FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

ตรวจสอบให้แน่ใจว่าคุณเลือกไดเร็กทอรีเอาต์พุตและชื่อไฟล์ที่เหมาะสมกับโมเดลของคุณ

## ขั้นตอนที่ 5: แสดงข้อความแสดงว่าสำเร็จ

สุดท้ายนี้ เฉลิมฉลองความสำเร็จของคุณโดยแสดงข้อความ:

```csharp
// แสดงข้อความความสำเร็จ
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

ฉาก 3 มิติของคุณที่ประกอบด้วยโมเดลดั้งเดิมเสร็จสมบูรณ์และบันทึกแล้ว!

## บทสรุป

 ขอแสดงความยินดีกับการสร้างโมเดล 3 มิติที่น่าทึ่งโดยใช้ Aspose.3D สำหรับ .NET! บทช่วยสอนนี้ครอบคลุมพื้นฐานของการสร้างแบบจำลองเบื้องต้น แต่ความเป็นไปได้นั้นไม่มีที่สิ้นสุด สำรวจเพิ่มเติมเกี่ยวกับคุณลักษณะและเทคนิคขั้นสูงใน[เอกสารประกอบ](https://reference.aspose.com/3d/net/).

## คำถามที่พบบ่อย

### ฉันสามารถใช้ Aspose.3D สำหรับ .NET กับภาษาการเขียนโปรแกรมอื่นนอกเหนือจาก .NET ได้หรือไม่

Aspose.3D รองรับ .NET เป็นหลัก แต่ก็มีเวอร์ชันสำหรับ Java และแพลตฟอร์มอื่นๆ ด้วย

### มีรุ่นทดลองใช้งานฟรีไหม?

 ใช่ คุณสามารถทดลองใช้ความสามารถของ Aspose.3D ได้ด้วย[ทดลองใช้งานฟรี](https://releases.aspose.com/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับ Aspose.3D สำหรับ .NET ได้ที่ไหน

หากต้องการการสนับสนุนจากชุมชน โปรดไปที่[ฟอรั่ม Aspose.3D](https://forum.aspose.com/c/3d/18).

### ฉันจะได้รับใบอนุญาตชั่วคราวได้อย่างไร?

 คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.conholdate.com/temporary-license/).

### มีบทช่วยสอนเพิ่มเติมหรือไม่

 ใช่! สำรวจบทช่วยสอนและตัวอย่างเพิ่มเติมใน[เอกสารประกอบ](https://reference.aspose.com/3d/net/).