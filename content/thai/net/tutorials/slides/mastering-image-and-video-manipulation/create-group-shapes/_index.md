---
title: สร้างรูปร่างกลุ่มใน PowerPoint ด้วย Aspose.Slides สำหรับ .NET
linktitle: สร้างรูปร่างกลุ่มใน PowerPoint ด้วย Aspose.Slides สำหรับ .NET
second_title: API การประมวลผล PowerPoint ของ Aspose.Slides .NET
description: เรียนรู้วิธีการสร้างและจัดการรูปร่างกลุ่มโดยใช้ Aspose.Slides สำหรับ .NET คู่มือที่ครอบคลุมนี้ให้คำแนะนำแบบทีละขั้นตอนที่ชัดเจน
type: docs
weight: 11
url: /th/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## การแนะนำ

การเพิ่มความสวยงามและความเป็นระเบียบของงานนำเสนอ PowerPoint ของคุณอาจส่งผลต่อการมีส่วนร่วมของผู้ชมได้อย่างมาก วิธีหนึ่งที่มีประสิทธิภาพในการบรรลุผลดังกล่าวคือการใช้รูปทรงกลุ่ม ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีใช้ประโยชน์จาก Aspose.Slides สำหรับ .NET เพื่อสร้างและจัดการรูปทรงกลุ่มในงานนำเสนอของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

-  Aspose.Slides สำหรับ .NET: ดาวน์โหลดและติดตั้งเวอร์ชันล่าสุดของไลบรารี Aspose.Slides จาก[เว็บไซต์อาโพส](https://releases.aspose.com/slides/net/).
- สภาพแวดล้อมการพัฒนา: ตั้งค่า IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio เพื่อทำงานบนโปรเจ็กต์ของคุณ
- ความรู้พื้นฐานเกี่ยวกับ C#: ทำความคุ้นเคยกับแนวคิดพื้นฐานของ C#


## นำเข้าเนมสเปซที่จำเป็น

ในโครงการ C# ของคุณ เริ่มต้นด้วยการรวมเนมสเปซต่อไปนี้:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## ขั้นตอนที่ 1: สร้างอินสแตนซ์คลาสการนำเสนอ

 สร้างอินสแตนซ์ของ`Presentation`ชั้นเรียนที่คุณจะทำงานกับสไลด์ของคุณ ระบุไดเร็กทอรีที่จัดเก็บเอกสารของคุณ:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // ขั้นตอนในการสร้างและจัดการรูปทรงจะอยู่ที่นี่
}
```

## ขั้นตอนที่ 2: เข้าถึงสไลด์แรก

ดึงข้อมูลสไลด์แรกของการนำเสนอที่คุณสร้างขึ้นใหม่:

```csharp
ISlide slide = pres.Slides[0];
```

## ขั้นตอนที่ 3: เข้าถึงคอลเลกชันรูปร่าง

รับคอลเลกชันรูปทรงบนสไลด์:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## ขั้นตอนที่ 4: เพิ่มรูปร่างกลุ่ม

ตอนนี้ถึงเวลาเพิ่มรูปร่างกลุ่มลงในสไลด์แล้ว:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## ขั้นตอนที่ 5: เพิ่มรูปร่างภายในกลุ่ม

คุณสามารถเพิ่มรูปร่างกลุ่มด้วยรูปร่างแต่ละรูปร่าง เช่น สี่เหลี่ยมผืนผ้า:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // รูปทรงที่ 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // รูปทรงที่ 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // รูปทรงที่ 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // รูปทรงที่ 4
```

## ขั้นตอนที่ 6: กำหนดกรอบสำหรับรูปร่างกลุ่ม

การกำหนดกรอบให้กับรูปร่างกลุ่มจะทำให้มีขอบเขตที่ชัดเจน:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## ขั้นตอนที่ 7: บันทึกการนำเสนอ

สุดท้ายให้บันทึกการนำเสนอที่คุณแก้ไขแล้วไปยังไดเร็กทอรีที่ระบุ:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## บทสรุป

ขอแสดงความยินดี! คุณได้สร้างรูปร่างกลุ่มในงานนำเสนอ PowerPoint สำเร็จแล้วโดยใช้ Aspose.Slides สำหรับ .NET การจัดระเบียบรูปร่างในลักษณะนี้จะช่วยให้คุณปรับปรุงเค้าโครงภาพและความชัดเจนของเนื้อหาได้อย่างมาก ทำให้การนำเสนอของคุณมีประสิทธิภาพมากขึ้น

## คำถามที่พบบ่อย

### Aspose.Slides เข้ากันได้กับ .NET เวอร์ชันล่าสุดหรือไม่

 ใช่ Aspose.Slides ได้รับการอัปเดตเป็นประจำเพื่อให้เข้ากันได้กับเวอร์ชัน .NET ล่าสุด ตรวจสอบ[เอกสารประกอบ](https://reference.aspose.com/slides/net/) สำหรับรายละเอียดความเข้ากันได้ล่าสุด

### ฉันสามารถทดลองใช้ Aspose.Slides ก่อนซื้อได้หรือไม่?

 แน่นอน! คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีได้[ที่นี่](https://releases.aspose.com/).

### ฉันสามารถค้นหาการสนับสนุนสำหรับแบบสอบถามที่เกี่ยวข้องกับ Aspose.Slides ได้ที่ไหน

 เยี่ยมชม Aspose.Slides[ฟอรั่ม](https://forum.aspose.com/c/slides/11) สำหรับการสนับสนุนและการหารือของชุมชน

### ฉันจะขอใบอนุญาตชั่วคราวสำหรับ Aspose.Slides ได้อย่างไร

 คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).

### ฉันสามารถซื้อลิขสิทธิ์เต็มรูปแบบสำหรับ Aspose.Slides ได้จากที่ใด

 คุณสามารถซื้อใบอนุญาตได้จาก[หน้าการซื้อ](https://purchase.aspose.com/buy).