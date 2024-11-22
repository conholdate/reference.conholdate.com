---
title: โมเดล AI แบบเปิดเพื่อการสรุปเอกสารอย่างมีประสิทธิภาพ
linktitle: โมเดล AI แบบเปิดเพื่อการสรุปเอกสารอย่างมีประสิทธิภาพ
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีสรุปเอกสารขนาดใหญ่ได้อย่างรวดเร็วและแม่นยำด้วยบทช่วยสอนที่ครอบคลุมนี้ ซึ่งครอบคลุมถึงข้อกำหนดเบื้องต้น การตั้งค่า และตัวอย่างการเขียนโค้ด
type: docs
weight: 10
url: /th/net/tutorials/words/advanced-ai-document-processing/efficient-document-summarization-openai-model/
---
## การแนะนำ

การจัดการเอกสารที่มีประสิทธิภาพกลายเป็นสิ่งที่ขาดไม่ได้ในโลกดิจิทัลทุกวันนี้ ด้วย Aspose.Words สำหรับ .NET การสรุปเอกสารจะง่ายขึ้นและมีประสิทธิผลมากขึ้น โดยเฉพาะอย่างยิ่งเมื่อจับคู่กับความสามารถของโมเดล OpenAI คู่มือนี้จะแนะนำคุณทีละขั้นตอนในการใช้ Aspose.Words สำหรับ .NET และโมเดล OpenAI เพื่อสรุปเอกสารโดยอัตโนมัติ ช่วยประหยัดเวลาและให้ข้อมูลเชิงลึกอย่างรวดเร็ว ไม่ว่าคุณจะสรุปรายงาน เอกสารวิชาการ หรือเอกสารจำนวนมาก คู่มือนี้จะช่วยให้คุณได้รับประโยชน์สูงสุดจากเครื่องมือของคุณ

## ข้อกำหนดเบื้องต้น

### การตั้งค่าสภาพแวดล้อม .NET
ตรวจสอบให้แน่ใจว่าคุณมีเวอร์ชัน .NET framework ที่เข้ากันได้ บทช่วยสอนนี้เข้ากันได้กับ .NET 5.0 ขึ้นไป

### ติดตั้ง Aspose.Words สำหรับ .NET
 ดาวน์โหลดแพ็คเกจ Aspose.Words สำหรับ .NET จาก[เว็บไซต์อาโพส](https://releases.aspose.com/words/net/)และติดตั้งในโครงการของคุณโดยใช้ตัวจัดการแพ็กเกจ NuGet ใน Visual Studio

### รับรหัส API ของ OpenAI
 หากต้องการเข้าถึงโมเดลภาษาของ OpenAI คุณจะต้องมีคีย์ API ลงทะเบียนที่[เว็บไซต์ OpenAI](https://openai.com/)ดึงคีย์ของคุณและเก็บไว้ให้ปลอดภัยเพื่อการรวมระบบ

### สภาพแวดล้อมการพัฒนาแบบบูรณาการ
การใช้ Visual Studio เป็น IDE จะทำให้กระบวนการเขียนโค้ดและดีบักง่ายขึ้น

## การนำเข้าไลบรารีที่จำเป็น

ในโครงการของคุณ ให้ทำการนำเข้าไลบรารีที่จำเป็นเพื่อให้แน่ใจว่าคุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการจัดการและสรุปเอกสารได้

### การนำเข้าแพ็กเกจ Aspose.Words

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;
using System.Text;
```

หากใช้ไลบรารีภายนอกเพื่อจัดการการเรียก API ไปยัง OpenAI โปรดตรวจสอบให้แน่ใจว่าได้ติดตั้งและกำหนดค่าไลบรารีนั้นแล้ว ตอนนี้เรามาดูวิธีตั้งค่าการสรุปเอกสารกัน

## ขั้นตอนที่ 1: กำหนดเส้นทางเอกสาร

กำหนดไดเร็กทอรีเพื่อจัดระเบียบแหล่งเอกสารของคุณและบันทึกสรุปที่สร้างขึ้น

```csharp
string MyDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
string ArtifactsDir = "YOUR_OUTPUT_DIRECTORY_PATH";
```

## ขั้นตอนที่ 2: โหลดเอกสารที่จะสรุป

โหลดเอกสารหนึ่งฉบับหรือมากกว่านั้นลงในแอปพลิเคชันของคุณโดยใช้ Aspose.Words ตัวอย่างนี้โหลดเอกสารสองฉบับเพื่อจุดประสงค์ในการสาธิต:

```csharp
Document doc1 = new Document(MyDir + "BigDocument.docx");
Document doc2 = new Document(MyDir + "AnotherDocument.docx");
```

## ขั้นตอนที่ 3: ตั้งค่าคีย์ API ของ OpenAI

เพื่อความปลอดภัย โปรดดึงคีย์ API ของ OpenAI จากตัวแปรสภาพแวดล้อม แทนที่จะเขียนโค้ดแบบฮาร์ดโค้ด

```csharp
string apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
```

## ขั้นตอนที่ 4: เริ่มต้นโมเดล OpenAI

 สร้างอินสแตนซ์ของโมเดล OpenAI สำหรับการสรุปผล ที่นี่เราจะใช้`Gpt4OMini` เพื่อให้การสรุปสั้นกระชับแต่เข้าใจง่าย

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

## ขั้นตอนที่ 5: สรุปเอกสารเดียว

เมื่อสร้างอินสแตนซ์โมเดลแล้ว ให้สร้างสรุปของเอกสารเดียว

```csharp
Document summaryDoc = model.Summarize(doc1, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
summaryDoc.Save(ArtifactsDir + "SingleDocSummary.docx");
```

 นี่จะเป็นการบันทึกสรุปสั้นๆ ของ`doc1` ในไดเร็กทอรีเอาท์พุตที่กำหนด

## ขั้นตอนที่ 6: สรุปเอกสารหลายฉบับ

หากคุณต้องการสร้างสรุปแบบรวมจากเอกสารหลายฉบับ เพียงปรับเปลี่ยนวิธีการสรุป

```csharp
Document combinedSummary = model.Summarize(new Document[] { doc1, doc2 }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
combinedSummary.Save(ArtifactsDir + "CombinedSummary.docx");
```

แนวทางนี้เหมาะอย่างยิ่งสำหรับการสรุปจากรายงานจำนวนมากหรือเอกสารที่เกี่ยวข้องเป็นชุด

## บทสรุป

การใช้ Aspose.Words สำหรับโมเดล .NET และ OpenAI สำหรับการสรุปเอกสารช่วยให้ได้รับประโยชน์ด้านประสิทธิภาพการทำงานอย่างมหาศาล ไม่ว่าจะจัดการเอกสารเดียวหรือหลายไฟล์ การผสานรวมนี้ช่วยให้สรุปข้อมูลได้อย่างรวดเร็วและเชื่อถือได้ โดยเปลี่ยนเอกสารที่ซับซ้อนให้กลายเป็นข้อมูลเชิงลึกที่กระชับและเข้าใจง่าย

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?
Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการจัดการเอกสาร Word ด้วยโปรแกรม รองรับการสร้าง จัดการ และแปลงไฟล์ในรูปแบบต่างๆ มากมาย

### เหตุใดฉันจึงต้องใช้คีย์ API ของ OpenAI
จำเป็นต้องมีคีย์ API เพื่อเข้าถึงโมเดลภาษาของ OpenAI เพื่อสร้างสรุปหรืองานประมวลผลภาษาธรรมชาติอื่นๆ

### ฉันสามารถรวมสรุปเอกสารหลายฉบับได้หรือไม่
ใช่ Aspose.Words ช่วยให้คุณสามารถสร้างสรุปจากเอกสารหลายฉบับพร้อมกัน เหมาะอย่างยิ่งสำหรับรายงานโครงการหรือกรณีศึกษา

### ฉันจะติดตั้ง Aspose.Words สำหรับ .NET ได้อย่างไร?
ใช้ตัวจัดการแพ็คเกจ NuGet ใน Visual Studio เพื่อติดตั้ง Aspose.Words โดยค้นหาแพ็คเกจและเลือก "ติดตั้ง"

### Aspose.Words มีให้ใช้ฟรีหรือไม่?
 คุณสามารถดาวน์โหลดรุ่นทดลองใช้งานฟรีของ Aspose.Words เพื่อทดสอบความสามารถผ่านทาง[เว็บไซต์อาโพส](https://releases.aspose.com/).