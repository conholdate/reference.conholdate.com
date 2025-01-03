---
title: การเรียนรู้การสรุปเอกสารด้วยโมเดล Google AI
linktitle: การเรียนรู้การสรุปเอกสารด้วยโมเดล Google AI
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีสรุปเอกสาร Word แบบทีละขั้นตอนด้วย Aspose.Words และ Google AI ใน .NET ปฏิบัติตามคู่มือนี้เพื่อปรับปรุงกระบวนการแยกเนื้อหา ข้อมูลเชิงลึกของเอกสาร และการทำงานอัตโนมัติ
type: docs
weight: 10
url: /th/net/tutorials/words/advanced-ai-document-processing/mastering-document-summarization-google-ai-model/
---
## การแนะนำ

การปรับปรุงข้อมูลจากเอกสารขนาดใหญ่ไม่เคยง่ายอย่างนี้มาก่อน คู่มือนี้จะอธิบายวิธีใช้ประโยชน์จาก Aspose.Words สำหรับ .NET และโมเดล AI ของ Google เพื่อสรุปเอกสาร Word ได้อย่างแม่นยำและมีประสิทธิภาพ ไม่ว่าคุณจะต้องสร้างบทสรุปสั้นๆ สำหรับรายงาน ดึงข้อมูลสำคัญจากการวิจัย หรือประมวลผลเอกสารหลายฉบับ บทช่วยสอนที่ครอบคลุมนี้จะแนะนำคุณในทุกขั้นตอน

## ข้อกำหนดเบื้องต้น

ในการเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

1. ความเชี่ยวชาญใน C# และ .NET: ความเข้าใจพื้นฐานเกี่ยวกับ C# และ .NET จะช่วยให้คุณนำทางผ่านโค้ดและแนวคิดต่างๆ ได้อย่างมีประสิทธิภาพมากขึ้น
2.  Aspose.Words สำหรับ .NET: ไลบรารีอันทรงพลังนี้มอบเครื่องมือสำหรับสร้าง แก้ไข และจัดการเอกสาร Word ในแอปพลิเคชัน .NET ดาวน์โหลดเลย[ที่นี่](https://releases.aspose.com/words/net/).
3. คีย์ API สำหรับ Google AI: จำเป็นต้องมีคีย์ API เพื่อตรวจสอบยืนยันคำขอไปยังโมเดล AI ของ Google จัดเก็บคีย์นี้ไว้อย่างปลอดภัยในตัวแปรสภาพแวดล้อมของคุณ
4. สภาพแวดล้อมการพัฒนา: จำเป็นต้องมี IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio เพื่อสร้างและรันแอปพลิเคชัน
5. ตัวอย่างเอกสาร Word: ตรวจสอบให้แน่ใจว่าคุณมีเอกสาร Word ตัวอย่างพร้อมแล้ว (เช่น "Big document.docx", "Document.docx") เพื่อทดสอบการทำงานของการสรุป

## นำเข้าเนมสเปซที่จำเป็น

เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นเพื่อรวม Aspose.Words เข้ากับ Google AI

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.AI;
```

เมื่อมีแพ็คเกจเหล่านี้แล้ว คุณก็พร้อมที่จะเริ่มสรุปเอกสารได้แล้ว

## ขั้นตอนที่ 1: ตั้งค่าเส้นทางไดเรกทอรี

เริ่มต้นด้วยการกำหนดเส้นทางไฟล์สำหรับเอกสารอินพุตของคุณและตำแหน่งที่คุณต้องการบันทึกเอกสารสรุป

```csharp
// ไดเรกทอรีสำหรับเอกสารต้นทาง
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// ไดเรกทอรีสำหรับบันทึกข้อมูลเอาท์พุต
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 แทนที่`"YOUR_DOCUMENT_DIRECTORY"` และ`"YOUR_ARTIFACTS_DIRECTORY"` ด้วยเส้นทางจริงบนระบบของคุณ ไดเร็กทอรีเหล่านี้จะทำหน้าที่เป็นข้อมูลอ้างอิงสำหรับการโหลดและบันทึกเอกสาร

## ขั้นตอนที่ 2: โหลดเอกสาร Word

 จากนั้นโหลดเอกสารที่คุณต้องการสรุปโดยใช้`Document` คลาสจาก Aspose.Words

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 ตรวจสอบให้แน่ใจว่าชื่อไฟล์ตรงกับเอกสารในไดเร็กทอรีที่คุณระบุ`Document` คลาสอนุญาตให้คุณโหลดเอกสาร Word เข้าสู่หน่วยความจำเพื่อประมวลผล

## ขั้นตอนที่ 3: ดึงรหัส Google API ของคุณ

หากต้องการเข้าถึงโมเดล AI ของ Google โปรดดึงรหัส API อย่างปลอดภัยจากตัวแปรสภาพแวดล้อมของคุณ

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

การจัดเก็บคีย์ API ของคุณเป็นตัวแปรสภาพแวดล้อมจะช่วยลดความเสี่ยงในการเปิดเผยข้อมูลที่ละเอียดอ่อนในโค้ดของคุณ

## ขั้นตอนที่ 4: ตั้งค่าอินสแตนซ์โมเดล AI

กำหนดค่าโมเดล AI โดยการสร้างอินสแตนซ์โดยใช้โมเดล GPT-4 Mini โมเดลนี้มอบความสามารถในการสรุปข้อมูลที่มีประสิทธิภาพสำหรับเอกสารของคุณ

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 อ้างถึง[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/) สำหรับรายละเอียดเพิ่มเติมเกี่ยวกับการเลือกและการกำหนดค่าแบบจำลอง

## ขั้นตอนที่ 5: สรุปเอกสารเดียว

 ในการสร้างสรุปของเอกสารเดียว ให้ใช้`Summarize` วิธีการที่จัดทำโดยอินสแตนซ์โมเดล ระบุความยาวสรุปที่ต้องการ ในกรณีนี้คือสรุปสั้น ๆ

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 โค้ดนี้จะสร้างเวอร์ชันสรุปของ`firstDoc` และบันทึกไว้ในไดเร็กทอรีของสิ่งประดิษฐ์ ปรับความยาวของบทสรุปให้ตรงตามความต้องการของคุณ ไม่ว่าจะเป็นแบบสั้น กลาง หรือยาว

## ขั้นตอนที่ 6: สรุปเอกสารหลายฉบับพร้อมกัน

 สำหรับสถานการณ์ที่คุณต้องการสรุปเอกสารหลายฉบับพร้อมกัน ให้ส่งอาร์เรย์ของเอกสารไปยัง`Summarize` วิธี.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 แนวทางนี้จะสร้างสรุปที่ครอบคลุมซึ่งบูรณาการเนื้อหาจากทั้งสอง`firstDoc` และ`secondDoc`โดยให้ภาพรวมที่กว้างขึ้นในเอกสารสรุปฉบับเดียว

## บทสรุป

ด้วยบทช่วยสอนนี้ คุณจะพร้อมสรุปเอกสารอย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับโมเดล .NET และ Google AI ตั้งแต่การกำหนดไดเรกทอรีเอกสารและการโหลดไฟล์ไปจนถึงการเรียกค้นคีย์ API และการตั้งค่าอินสแตนซ์โมเดล แต่ละขั้นตอนจะช่วยให้คุณจัดการข้อความจำนวนมากได้อย่างมีประสิทธิภาพและสร้างบทสรุปที่กระชับด้วยโค้ดเพียงไม่กี่บรรทัด

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีอเนกประสงค์สำหรับการสร้าง แก้ไข และแปลงเอกสาร Word ในแอปพลิเคชัน .NET ซึ่งมีคุณสมบัติการจัดการเอกสารอัตโนมัติขั้นสูง

### ฉันจะรับคีย์ Google API สำหรับการสรุป AI ได้อย่างไร

หากต้องการใช้บริการ AI ของ Google โปรดลงทะเบียนบน Google Cloud เปิดใช้งานบริการ API ที่เกี่ยวข้อง และรักษาความปลอดภัยคีย์ API ของคุณ

### ฉันสามารถสรุปเอกสารหลายๆ เอกสารพร้อมกันได้ไหม?

ใช่ Aspose.Words ช่วยให้คุณส่งเอกสารหลายฉบับไปยังโมเดล AI และสร้างสรุปที่ครอบคลุมจากแหล่งต่าง ๆ หลายแหล่ง

### ฉันจะควบคุมความยาวของสรุปได้อย่างไร

 ใช้`SummaryLength` ตัวเลือกภายใน`SummarizeOptions`คลาสเพื่อกำหนดความยาวสรุปที่ต้องการเป็น สั้น, กลาง, หรือ ยาว

### ฉันสามารถหาแหล่งข้อมูลเพิ่มเติมสำหรับ Aspose.Words ได้จากที่ใด

 สำหรับตัวอย่างเพิ่มเติมและรายละเอียดทางเทคนิค โปรดดูที่[เอกสารประกอบ Aspose.Words](https://reference.aspose.com/words/net/).