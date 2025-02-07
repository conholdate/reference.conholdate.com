---
title: การแปลงไฟล์ Metafile เป็น SVG
linktitle: แปลงไฟล์ Metafile เป็น SVG
second_title: API การประมวลผลเอกสาร Aspose.Words
description: ค้นพบวิธีการปรับปรุงเอกสาร Word ของคุณโดยการแปลงเมตาไฟล์เป็น SVG โดยใช้ไลบรารี Aspose.Words for .NET ที่ทรงพลัง บทช่วยสอนที่ครอบคลุมนี้จะแนะนำคุณในแต่ละขั้นตอนตั้งแต่การเริ่มต้นเอกสารจนถึงการแทรกกราฟิก SVG
type: docs
weight: 10
url: /th/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-svg/
---
## การแนะนำ

สวัสดีผู้ชื่นชอบการเขียนโค้ด! คุณเคยอยากปรับปรุงเอกสาร Word ของคุณด้วยกราฟิกเวกเตอร์ที่ปรับขนาดได้หรือไม่? ถ้าเป็นเช่นนั้น คุณมาถูกที่แล้ว! ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการแปลงเมตาไฟล์เป็น SVG ในเอกสาร Word ของคุณโดยใช้ไลบรารี Aspose.Words for .NET ที่ทรงพลัง เมื่ออ่านจบ คุณจะมีทักษะในการสร้างเอกสารให้ดูน่าสนใจและใช้งานได้หลากหลาย เริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึก เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

1.  Aspose.Words สำหรับ .NET: ดาวน์โหลดจาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework แล้ว
3. สภาพแวดล้อมการพัฒนา: คุณสามารถใช้ IDE ใดๆ เช่น Visual Studio
4. ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# จะเป็นประโยชน์ แต่ไม่ต้องกังวลหากคุณเป็นมือใหม่ เราจะแนะนำคุณในแต่ละขั้นตอน

## การนำเข้าเนมสเปซ

ก่อนอื่น ให้ทำการอิมพอร์ตเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ ขั้นตอนนี้มีความสำคัญมากในการเข้าถึงฟังก์ชันการทำงานของ Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

เมื่อเราได้จัดเตรียมข้อกำหนดเบื้องต้นและเนมสเปซเรียบร้อยแล้ว มาดูคำแนะนำทีละขั้นตอนในการแปลงเมตาไฟล์เป็น SVG กัน

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

 เราจะเริ่มต้นด้วยการสร้างเอกสาร Word ใหม่และเริ่มต้นใช้งาน`DocumentBuilder` วัตถุซึ่งจะช่วยให้เราเพิ่มเนื้อหาได้

```csharp
// กำหนดเส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 รหัสนี้จะเริ่มต้นเอกสารใหม่และตัวสร้างเอกสาร`dataDir` ตัวแปรเก็บเส้นทางที่คุณจะบันทึกไฟล์ของคุณ

## ขั้นตอนที่ 2: เพิ่มข้อความลงในเอกสาร

ต่อไปเราจะเพิ่มบริบทลงในเอกสารของเราด้วยคำอธิบายเป็นข้อความ

```csharp
builder.Write("Here is an SVG image: ");
```

บรรทัดนี้จะเพิ่มข้อความ "นี่คือรูปภาพ SVG: " ลงในเอกสารของคุณ เพื่อให้มีบริบทสำหรับ SVG ที่คุณกำลังจะแทรก

## ขั้นตอนที่ 3: แทรกภาพ SVG

ตอนนี้มาถึงส่วนที่น่าตื่นเต้นแล้ว! เราจะแทรกภาพ SVG ลงในเอกสารของเราโดยใช้`InsertHtml` วิธี.

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg>");
```

สไนปเป็ตนี้จะแทรกรูปหลายเหลี่ยม SVG แบบง่าย ๆ พร้อมจุดและรูปแบบที่กำหนดไว้ คุณสามารถปรับแต่งโค้ด SVG ให้เหมาะกับความต้องการของคุณได้ตามต้องการ!

## ขั้นตอนที่ 4: กำหนด HtmlSaveOptions

 เพื่อให้แน่ใจว่าเมตาไฟล์ของเราได้รับการบันทึกเป็น SVG เราจะกำหนด`HtmlSaveOptions` และตั้งค่า`MetafileFormat` ทรัพย์สินที่จะ`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

การกำหนดค่านี้จะแจ้งให้ Aspose.Words แปลงไฟล์เมตาใดๆ ในเอกสารเป็นรูปแบบ SVG เมื่อส่งออกเป็น HTML

## ขั้นตอนที่ 5: บันทึกเอกสาร

 สุดท้ายเรามาบันทึกเอกสารของเราโดยใช้`Save` วิธีการของ`Document` ระดับ.

```csharp
doc.Save(dataDir + "ConvertMetafilesToSvg.html", saveOptions);
```

 บรรทัดนี้จะบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุโดยมีชื่อไฟล์`ConvertMetafilesToSvg.html` , การประยุกต์ใช้`saveOptions` เพื่อให้แน่ใจว่าเมตาไฟล์ถูกแปลงเป็น SVG

## บทสรุป

ขอแสดงความยินดี! คุณได้แปลงไฟล์เมตาเป็น SVG ในเอกสาร Word สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ด้วยโค้ดเพียงไม่กี่บรรทัด คุณสามารถปรับปรุงเอกสารของคุณด้วยกราฟิกเวกเตอร์ที่ปรับขนาดได้ ทำให้เอกสารดูมีชีวิตชีวาและดึงดูดสายตามากขึ้น ลองใช้ในโปรเจ็กต์ของคุณ และสนุกกับการเขียนโค้ด!

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่แข็งแกร่งที่ช่วยให้คุณสามารถสร้าง แก้ไข และแปลงเอกสาร Word ด้วยโปรแกรมโดยใช้ C#

### ฉันสามารถใช้ Aspose.Words สำหรับ .NET กับ .NET Core ได้หรือไม่
แน่นอน! Aspose.Words สำหรับ .NET รองรับ .NET Core ทำให้มีความยืดหยุ่นสำหรับแอปพลิเคชัน .NET ต่างๆ

### ฉันจะได้รับรุ่นทดลองใช้งาน Aspose.Words สำหรับ .NET ฟรีได้อย่างไร
 คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีได้จาก[หน้าวางจำหน่าย Aspose](https://releases.aspose.com/).

### ฉันสามารถแปลงไฟล์รูปภาพรูปแบบอื่นเป็น SVG โดยใช้ Aspose.Words ได้หรือไม่
ใช่ Aspose.Words รองรับการแปลงไฟล์รูปภาพต่างๆ รวมถึงเมตาไฟล์ เป็น SVG

### ฉันสามารถค้นหาเอกสารสำหรับ Aspose.Words สำหรับ .NET ได้ที่ไหน
 เอกสารรายละเอียดสามารถดูได้ที่[หน้าเอกสาร Aspose](https://reference.aspose.com/words/net/).