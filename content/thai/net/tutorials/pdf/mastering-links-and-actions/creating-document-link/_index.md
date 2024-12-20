---
title: การสร้างลิงก์เอกสาร
linktitle: การสร้างลิงก์เอกสาร
second_title: เอกสารอ้างอิง Aspose.PDF สำหรับ API ของ .NET
description: ค้นพบวิธีการปรับปรุงประสบการณ์ผู้ใช้ในเอกสาร PDF ของคุณโดยการสร้างลิงก์แบบโต้ตอบโดยใช้ Aspose.PDF สำหรับ .NET คู่มือฉบับสมบูรณ์นี้จะแนะนำคุณตลอดขั้นตอนต่างๆ
type: docs
weight: 30
url: /th/net/tutorials/pdf/mastering-links-and-actions/creating-document-link/
---
## การแนะนำ

การนำทางผ่านเอกสาร PDF ที่มีเนื้อหายาวๆ มักจะรู้สึกเหมือนกำลังเดินอยู่ในเขาวงกต การสร้างลิงก์ภายใน PDF สามารถปรับปรุงประสบการณ์การใช้งานของผู้ใช้ได้อย่างมากโดยทำให้การนำทางราบรื่นขึ้น ในคู่มือนี้ เราจะมาสำรวจวิธีการสร้างลิงก์เอกสารโดยใช้ Aspose.PDF สำหรับ .NET ซึ่งเป็นไลบรารีที่มีประสิทธิภาพที่ออกแบบมาเพื่อการจัดการ PDF อย่างมีประสิทธิภาพ ไม่ว่าคุณจะกำลังพัฒนารายงาน อีบุ๊ก หรือเนื้อหาแบบโต้ตอบใดๆ การเพิ่มลิงก์จะช่วยเพิ่มการใช้งานได้อย่างมาก

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด ให้แน่ใจว่าคุณมีสิ่งสำคัญต่อไปนี้:

- Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio สำหรับการพัฒนาแอปพลิเคชัน .NET
-  Aspose.PDF สำหรับ .NET: ดาวน์โหลดเวอร์ชันล่าสุดของไลบรารี Aspose.PDF จาก[ที่นี่](https://releases.aspose.com/pdf/net/).
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับ C# จะช่วยให้คุณนำทางผ่านตัวอย่างต่างๆ ได้อย่างง่ายดาย

### การติดตั้ง Aspose.PDF สำหรับ .NET

หากต้องการติดตั้ง Aspose.PDF สำหรับ .NET ให้ทำตามขั้นตอนเหล่านี้:

1. เปิดโปรเจ็กต์ของคุณ: เปิด Visual Studio และสร้างโปรเจ็กต์ใหม่หรือเปิดโปรเจ็กต์ที่มีอยู่
2. เข้าถึงตัวจัดการแพ็กเกจ NuGet: คลิกขวาที่โครงการของคุณใน Solution Explorer
3. จัดการแพ็คเกจ NuGet: เลือก “จัดการแพ็คเกจ NuGet”
4. ค้นหา Aspose.PDF: ในแท็บ Browse ให้พิมพ์ “Aspose.PDF” และติดตั้งเวอร์ชันล่าสุด
5. ตรวจสอบการติดตั้ง: ให้แน่ใจว่า Aspose.PDF ปรากฏในข้อมูลอ้างอิงโครงการของคุณ

เมื่อทุกอย่างพร้อมแล้ว มาเริ่มกันเลย!

## นำเข้าเนมสเปซที่จำเป็น

ในการทำงานกับ Aspose.PDF คุณจำเป็นต้องนำเข้าเนมสเปซที่จำเป็นในไฟล์ C# ของคุณ:

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
```

เนมสเปซเหล่านี้ให้คลาสและฟังก์ชันที่จำเป็นสำหรับการจัดการเอกสาร PDF และคำอธิบายประกอบ

## คู่มือทีละขั้นตอนในการสร้างลิงก์เอกสาร

การสร้างลิงก์เอกสารก็เหมือนกับการสร้างเส้นทางใน PDF ของคุณ มาทำให้ผู้ใช้นำทางได้อย่างง่ายดายกันเถอะ!

### ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสารของคุณ

เริ่มต้นโดยระบุไดเรกทอรีที่จัดเก็บไฟล์ PDF ของคุณ:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` ด้วยเส้นทางไปยังไฟล์ PDF ของคุณ เช่น`"C:\\Documents\\"`.

### ขั้นตอนที่ 2: เปิดเอกสาร PDF

โหลดเอกสาร PDF ที่คุณต้องการใช้งาน:

```csharp
Document document = new Document(dataDir + "CreateDocumentLink.pdf");
```

 ให้แน่ใจว่า`CreateDocumentLink.pdf` มีอยู่ในไดเร็กทอรีที่ระบุเพื่อหลีกเลี่ยงข้อผิดพลาด

### ขั้นตอนที่ 3: ระบุหน้าสำหรับการสร้างลิงค์

กำหนดว่าหน้าใดจะโฮสต์ลิงก์ ตัวอย่างเช่น หากคุณต้องการเพิ่มลิงก์ไปยังหน้าแรก:

```csharp
Page page = document.Pages[1]; // หน้าถูกจัดทำดัชนี 1 ใน Aspose
```

### ขั้นตอนที่ 4: สร้างคำอธิบายลิงก์

 ตอนนี้เรามาสร้างกัน`LinkAnnotation` ที่ผู้ใช้จะคลิก:

```csharp
LinkAnnotation link = new LinkAnnotation(page, new Aspose.Pdf.Rectangle(100, 100, 300, 300));
```

 สี่เหลี่ยมผืนผ้าจะกำหนดพื้นที่ที่สามารถคลิกได้ด้วย`(100, 100, 300, 300)` แสดงพิกัด (ซ้าย, ล่าง, ขวา, บน) ปรับค่าเหล่านี้ตามต้องการ

### ขั้นตอนที่ 5: ปรับแต่งรูปลักษณ์ของลิงก์

ทำให้ลิงก์ของคุณน่าสนใจและกำหนดการดำเนินการของมัน:

```csharp
link.Color = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Green);
link.Action = new GoToRemoteAction(dataDir + "RemoveOpenAction.pdf", 1);
```

 ที่นี่ เราตั้งค่าสีลิงก์เป็นสีเขียว และระบุว่าการคลิกลิงก์จะนำทางไปยัง`RemoveOpenAction.pdf` ที่หน้า 1.

### ขั้นตอนที่ 6: เพิ่มคำอธิบายลิงก์ลงในหน้า

แนบคำอธิบายลิงค์ไปที่หน้า:

```csharp
page.Annotations.Add(link);
```

นี่จะเพิ่มลิงก์ที่สามารถคลิกได้ไปยังหน้าที่ระบุ

### ขั้นตอนที่ 7: บันทึกเอกสารที่อัปเดตของคุณ

บันทึกเอกสารด้วยลิงก์ที่เพิ่มใหม่:

```csharp
dataDir = dataDir + "CreateDocumentLink_out.pdf";
document.Save(dataDir);
```

เอกสารที่แก้ไขจะถูกบันทึกด้วยชื่อไฟล์ใหม่ ซึ่งระบุว่าเป็นเวอร์ชันที่มีการเปลี่ยนแปลง

### ขั้นตอนที่ 8: การยืนยันคอนโซล

ให้คำยืนยันว่าการสร้างลิงค์สำเร็จ:

```csharp
Console.WriteLine("\nDocument link created successfully.\nFile saved at " + dataDir);
```

คำติชมนี้ช่วยให้คุณทราบว่ากระบวนการเสร็จสิ้นโดยไม่มีปัญหา

## บทสรุป

ขอแสดงความยินดี! คุณได้สร้างลิงก์เอกสารแบบโต้ตอบในไฟล์ PDF สำเร็จแล้วโดยใช้ Aspose.PDF สำหรับ .NET หากทำตามขั้นตอนง่ายๆ เหล่านี้ คุณจะสามารถปรับปรุงการโต้ตอบและการนำทางของเอกสารได้ ทำไมจึงต้องยอมรับ PDF แบบคงที่ในขณะที่ประสบการณ์การคลิกสามารถทำได้ในโค้ดเพียงไม่กี่บรรทัด?

## คำถามที่พบบ่อย

### Aspose.PDF สำหรับ .NET ใช้ทำอะไร?
Aspose.PDF สำหรับ .NET เป็นไลบรารีที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงเอกสาร PDF ด้วยโปรแกรมได้

### ฉันสามารถสร้างลิงค์ไปยังเว็บไซต์ภายนอกได้หรือไม่
 ใช่ คุณสามารถสร้างลิงก์ไปยังเว็บไซต์ภายนอกได้โดยใช้`GoToRemoteAction` ด้วย URL ที่ต้องการ

### มีการทดลองใช้ฟรีหรือไม่?
 แน่นอน! คุณทำได้[ดาวน์โหลดรุ่นทดลองใช้ฟรีได้ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนได้ที่ไหนหากประสบปัญหา?
 คุณสามารถติดต่อเราได้ที่[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/pdf/10) เพื่อขอความช่วยเหลือ

### ฉันจะได้รับใบอนุญาตชั่วคราวได้อย่างไร?
 คุณสามารถขอใบอนุญาตชั่วคราวได้ผ่านทาง[หน้าใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/).

---

## การแนะนำ

การสร้างลิงก์ภายในเอกสาร PDF จะช่วยปรับปรุงประสบการณ์ของผู้ใช้ได้อย่างมาก ทำให้การนำทางราบรื่นและใช้งานง่ายขึ้น หากคุณเคยพบว่าตัวเองหลงทางใน PDF และพยายามค้นหาหน้าที่ถูกต้องอย่างบ้าคลั่ง คุณจะเข้าใจถึงความสำคัญของลิงก์ ในคู่มือนี้ เราจะเจาะลึกถึงวิธีการสร้างลิงก์เอกสารโดยใช้ Aspose.PDF สำหรับ .NET ซึ่งเป็นไลบรารีที่มีประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถจัดการไฟล์ PDF ได้อย่างง่ายดาย ไม่ว่าคุณจะกำลังสร้างรายงาน อีบุ๊ก หรือเนื้อหาแบบโต้ตอบ การสามารถสร้างลิงก์ดังกล่าวได้จะช่วยยกระดับการใช้งานเอกสารของคุณได้

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเข้าสู่โลกของการจัดการ PDF ด้วย Aspose.PDF สำหรับ .NET ให้แน่ใจว่าคุณมีสิ่งสำคัญบางอย่างอยู่:

- Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio แล้วเพื่อสร้างและเรียกใช้แอปพลิเคชัน .NET
-  Aspose.PDF สำหรับ .NET: คุณต้องมีไลบรารี Aspose.PDF ไว้ใช้งาน คุณสามารถ[ดาวน์โหลดได้ที่นี่](https://releases.aspose.com/pdf/net/).
- ความเข้าใจพื้นฐานเกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# จะช่วยให้คุณนำทางผ่านชิ้นส่วนโค้ดได้อย่างง่ายดาย

### การติดตั้ง Aspose.PDF สำหรับ .NET

หากต้องการติดตั้ง Aspose.PDF สำหรับ .NET คุณสามารถใช้ตัวจัดการแพ็กเกจ NuGet ใน Visual Studio ได้ ดังต่อไปนี้:

1. เปิดโครงการของคุณ: เริ่ม Visual Studio และเปิดโครงการที่มีอยู่ของคุณหรือสร้างโครงการใหม่
   
2. ตัวจัดการแพ็กเกจ NuGet: คลิกขวาที่โครงการใน Solution Explorer
   
3. จัดการแพ็คเกจ NuGet: เลือกตัวเลือก “จัดการแพ็คเกจ NuGet”

4. ค้นหา Aspose.PDF: ในแท็บ Browse ให้พิมพ์ “Aspose.PDF” และติดตั้งเวอร์ชันล่าสุด

5. ตรวจสอบการติดตั้ง: ตรวจสอบให้แน่ใจว่าปรากฏในข้อมูลอ้างอิงโครงการของคุณ

เมื่อคุณเตรียมทุกอย่างเสร็จเรียบร้อยแล้ว คุณก็พร้อมที่จะลงมือทำได้เลย!

## แพ็คเกจนำเข้า

ในการเริ่มทำงานกับ Aspose.PDF สำหรับ .NET ขั้นตอนแรกคือการนำเข้าเนมสเปซที่จำเป็นลงในไฟล์ C# ของคุณ:

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
```

เนมสเปซเหล่านี้ประกอบด้วยคลาสและฟังก์ชันที่จำเป็นสำหรับการจัดการเอกสาร PDF และคำอธิบายประกอบ ตอนนี้ มาแบ่งงานในการสร้างลิงก์เอกสารออกเป็นขั้นตอนที่สามารถดำเนินการได้

การสร้างลิงก์เอกสารก็เหมือนการปูถนนระหว่างสองจุด มาทำให้มั่นใจว่าผู้ที่เปิดดู PDF ของคุณจะทำได้อย่างง่ายดาย!

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอกสารของคุณ

สิ่งสำคัญในการเขียนโปรแกรมคือการจัดระเบียบ เริ่มจากการระบุว่าเอกสารของคุณอยู่ที่ไหน วิธีนี้จะช่วยให้เส้นทางของคุณชัดเจนและไฟล์ของคุณสามารถเข้าถึงได้

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 แทนที่`"YOUR DOCUMENT DIRECTORY"` โดยมีเส้นทางไปยังไดเรกทอรีที่จัดเก็บไฟล์ PDF ของคุณ อาจเป็นอะไรทำนองนี้`"C:\\Documents\\"`ขึ้นอยู่กับการตั้งค่าของคุณ

## ขั้นตอนที่ 2: เปิดเอกสาร PDF

ตอนนี้ถึงเวลาเปิดเอกสาร PDF ที่คุณต้องการใช้งาน นี่คือจุดเริ่มต้นของการเดินทางของคุณ!

```csharp
Document document = new Document(dataDir + "CreateDocumentLink.pdf");
```

 ในบรรทัดนี้ เรากำลังสร้างอินสแตนซ์ของ`Document` คลาสและกำลังโหลดไฟล์ PDF เป้าหมายของเรา ตรวจสอบให้แน่ใจว่ามีไฟล์ "CreateDocumentLink.pdf" อยู่ในไดเร็กทอรีที่ระบุ มิฉะนั้น คุณจะพบกับอุปสรรคเล็กน้อย

## ขั้นตอนที่ 3: ระบุหน้าสำหรับการสร้างลิงค์

ขั้นต่อไป คุณต้องกำหนดว่าหน้าใดในเอกสารของคุณที่จะโฮสต์ลิงก์ สมมติว่าคุณต้องการให้ลิงก์นี้อยู่ในหน้าแรก

```csharp
Page page = document.Pages[1];
```

หน้าเพจต่างๆ จะถูกจัดทำดัชนีเป็นศูนย์ใน Aspose ซึ่งหมายความว่าคุณจะเริ่มนับจาก 1 สำหรับผู้ใช้ ขั้นตอนนี้จะช่วยเตรียมขั้นตอนสำหรับการเพิ่มลิงก์ของคุณ

## ขั้นตอนที่ 4: สร้างคำอธิบายลิงก์

 การคลิกลิงก์ควรนำไปยังที่ใดที่หนึ่ง! มาสร้าง...`LinkAnnotation` ที่ผู้ใช้จะคลิก นี่คือช่วงเวลาที่ลิงก์ของคุณเริ่มเป็นรูปเป็นร่าง

```csharp
LinkAnnotation link = new LinkAnnotation(page, new Aspose.Pdf.Rectangle(100, 100, 300, 300));
```

 ที่นี่ สี่เหลี่ยมผืนผ้าจะกำหนดพื้นที่ที่สามารถคลิกได้สำหรับลิงก์ พารามิเตอร์`(100, 100, 300, 300)` แสดงพิกัดของรูปสี่เหลี่ยมผืนผ้า (ซ้าย ล่าง ขวา บน) ปรับตัวเลขเหล่านี้ตามขนาดพื้นที่ลิงก์ที่คุณต้องการ

## ขั้นตอนที่ 5: ปรับแต่งรูปลักษณ์ของลิงก์

มาทำให้ลิงก์นั้นโดดเด่นขึ้นมาหน่อยดีกว่า คุณสามารถปรับแต่งสีและลักษณะเมื่อคลิกได้

```csharp
link.Color = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Green);
link.Action = new GoToRemoteAction(dataDir + "RemoveOpenAction.pdf", 1);
```

ที่นี่ เรากำหนดสีของลิงก์เป็นสีเขียว และกำหนดการดำเนินการสำหรับลิงก์นั้น: นำทางไปยังเอกสาร PDF อื่นที่ชื่อ "RemoveOpenAction.pdf" โดยเริ่มต้นที่หน้า 1 คุณสามารถแทนที่ชื่อไฟล์และหมายเลขหน้าด้วยเป้าหมายที่คุณต้องการได้

## ขั้นตอนที่ 6: เพิ่มคำอธิบายลิงก์ลงในหน้า

เมื่อคุณเตรียมลิงก์ไว้พร้อมแล้ว ก็ถึงเวลาที่จะแนบลิงก์เข้ากับหน้าเหมือนกับด้ายกับเข็ม 

```csharp
page.Annotations.Add(link);
```

บรรทัดนี้ทำหน้าที่เพียงเพิ่มคำอธิบายลิงก์ที่เราสร้างใหม่ลงในหน้าที่ระบุ ทำให้เป็นองค์ประกอบแบบโต้ตอบภายใน PDF ของคุณ

## ขั้นตอนที่ 7: บันทึกเอกสารที่อัปเดตของคุณ

สิ่งดีๆ ทั้งหมดย่อมต้องสิ้นสุดลง และถึงเวลาที่จะบันทึกเอกสารโดยมีลิงก์ใหม่รวมอยู่ด้วย 

```csharp
dataDir = dataDir + "CreateDocumentLink_out.pdf";
document.Save(dataDir);
```

ที่นี่เราระบุชื่อไฟล์ใหม่ (“-“out.pdf” ระบุว่าเป็นสำเนาที่แก้ไข และบันทึกเอกสาร เพื่อให้แน่ใจว่าผลงานทั้งหมดของคุณได้รับการเก็บรักษาไว้

## ขั้นตอนที่ 8: การยืนยันคอนโซล

สุดท้ายนี้ การยืนยันเล็กๆ น้อยๆ ก็ไม่เสียหาย! ให้เราแจ้งตัวเองว่ากระบวนการสร้างลิงก์สำเร็จแล้ว

```csharp
Console.WriteLine("\nDocument link created successfully.\nFile saved at " + dataDir);
```

การดำเนินตามแนวทางนี้แสดงให้เห็นชัดเจนว่าทุกอย่างดำเนินไปโดยไม่มีสะดุด

## บทสรุป

และแล้วคุณก็จะได้มันมา! การใช้ Aspose.PDF สำหรับ .NET ช่วยให้คุณสร้างลิงก์เอกสารที่ใช้งานได้จริงและน่าสนใจในไฟล์ PDF ได้อย่างง่ายดาย เพียงทำตามขั้นตอนง่ายๆ เหล่านี้ คุณก็สามารถเพิ่มการโต้ตอบของเอกสารได้ ทำให้ผู้อ่านสามารถนำทางได้ง่ายขึ้น แล้วทำไมถึงต้องใช้ PDF แบบคงที่ ในเมื่อคุณสามารถคลิกได้โดยใช้โค้ดเพียงไม่กี่บรรทัด? 

## คำถามที่พบบ่อย

### Aspose.PDF สำหรับ .NET ใช้ทำอะไร?
Aspose.PDF สำหรับ .NET เป็นไลบรารีที่ช่วยให้นักพัฒนาสามารถสร้าง จัดการ และแปลงเอกสาร PDF ได้ด้วยโปรแกรม

### ฉันสามารถสร้างลิงค์ไปยังเว็บไซต์ภายนอกได้หรือไม่
ใช่ คุณสามารถสร้างลิงก์ไปยังเว็บไซต์ภายนอกได้โดยเปลี่ยนการดำเนินการลิงก์เป็น`GoToRemoteAction` พร้อม URL

### มีการทดลองใช้ฟรีหรือไม่?
 แน่นอน! คุณทำได้[ดาวน์โหลดรุ่นทดลองใช้ฟรีได้ที่นี่](https://releases.aspose.com/).

### ฉันจะได้รับการสนับสนุนได้ที่ไหนหากประสบปัญหา?
 คุณสามารถติดต่อเราได้ที่[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/pdf/10) เพื่อขอความช่วยเหลือ

### ฉันจะได้รับใบอนุญาตชั่วคราวได้อย่างไร?
 คุณสามารถขอใบอนุญาตชั่วคราวได้ผ่านทาง[หน้าใบอนุญาตชั่วคราว](https://purchase.aspose.com/temporary-license/).