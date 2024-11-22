---
title: เรียนรู้การกำหนดพื้นฐานด้วย Aspose.Tasks สำหรับ .NET
linktitle: การจัดการฐานข้อมูลงานใน Aspose.Tasks
second_title: API ของ Aspose.Tasks .NET
description: เรียนรู้วิธีจัดการฐานข้อมูลพื้นฐานการมอบหมายงานอย่างมีประสิทธิภาพโดยใช้ Aspose.Tasks สำหรับ .NET คำแนะนำทีละขั้นตอนนี้ครอบคลุมถึงการโหลดโครงการ ตั้งค่าฐานข้อมูลพื้นฐาน การดึงข้อมูล การเปรียบเทียบฐานข้อมูลพื้นฐาน และอื่นๆ เพื่อเพิ่มประสิทธิภาพเวิร์กโฟลว์การจัดการโครงการ
type: docs
weight: 14
url: /th/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## การแนะนำ

การจัดการโครงการที่มีประสิทธิภาพขึ้นอยู่กับการติดตามและจัดการข้อมูลพื้นฐานการมอบหมายงานอย่างแม่นยำ ด้วย Aspose.Tasks สำหรับ .NET คุณจะได้รับชุดเครื่องมืออันแข็งแกร่งเพื่อปรับปรุงการจัดการข้อมูลพื้นฐานการมอบหมายงานเพื่อให้ได้ข้อมูลเชิงลึกเกี่ยวกับโครงการที่ดีขึ้น ในบทความนี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการจัดการข้อมูลพื้นฐานการมอบหมายงาน เพื่อให้แน่ใจว่าโครงการของคุณยังคงดำเนินไปอย่างถูกต้อง

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มใช้งานจริง ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

- ความเชี่ยวชาญด้านการเขียนโปรแกรม: มีความคุ้นเคยเบื้องต้นกับ C#
- สภาพแวดล้อมการพัฒนา: ติดตั้งและกำหนดค่า Visual Studio
-  Aspose.Tasks สำหรับไลบรารี .NET: ดาวน์โหลดจาก[การเปิดตัว Aspose.Tasks](https://releases.aspose.com/tasks/net/).
- ไฟล์โครงการ: การเข้าถึงไฟล์โครงการในรูปแบบ MPP

## นำเข้าเนมสเปซที่จำเป็น

ในการใช้ฟังก์ชันการทำงานของ Aspose.Tasks ให้รวมเนมสเปซต่อไปนี้ในไฟล์โปรเจ็กต์ของคุณ:

```csharp
using Aspose.Tasks;
using System;
```

## ขั้นตอนที่ 1: โหลดโครงการและตั้งค่าพื้นฐาน

การโหลดโครงการและกำหนดค่าพื้นฐานถือเป็นพื้นฐานในการจัดการค่าพื้นฐานการมอบหมายงาน โค้ดต่อไปนี้จะสาธิตวิธีการโหลดโครงการและกำหนดค่าพื้นฐาน

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// การกำหนดเส้นฐานของโครงการ
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## ขั้นตอนที่ 2: ดึงข้อมูลพื้นฐานของการมอบหมาย

คุณสามารถดึงข้อมูลพื้นฐานโดยละเอียดสำหรับการมอบหมายทรัพยากรแต่ละรายการได้ โดยดำเนินการดังนี้:

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## ขั้นตอนที่ 3: เปรียบเทียบข้อมูลพื้นฐานระหว่างงานที่ได้รับมอบหมาย

Aspose.Tasks ช่วยให้คุณสามารถเปรียบเทียบค่าพื้นฐานด้วยโปรแกรมเพื่อประเมินความแตกต่างระหว่างการกำหนดทรัพยากร

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## ขั้นตอนที่ 4: แก้ไขรายละเอียดพื้นฐานตามโปรแกรม

คุณสามารถปรับเปลี่ยนข้อมูลพื้นฐานโดยการเขียนโปรแกรมเพื่อตอบสนองความต้องการของโครงการที่เปลี่ยนแปลงไป:

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // การปรับต้นทุนพื้นฐาน
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // การเพิ่มชั่วโมงการทำงาน

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## บทสรุป

การจัดการฐานข้อมูลการมอบหมายงานอย่างมีประสิทธิผลถือเป็นสิ่งสำคัญในการควบคุมกำหนดการและงบประมาณของโครงการ Aspose.Tasks สำหรับ .NET ช่วยให้คุณมีเครื่องมือที่จำเป็นในการจัดการฐานข้อมูลอย่างแม่นยำ ซึ่งช่วยให้สามารถตัดสินใจโดยอิงตามข้อมูลได้

## คำถามที่พบบ่อย

### Aspose.Tasks สามารถจัดการฐานข้อมูลพื้นฐานหลายรายการสำหรับโครงการเดียวได้หรือไม่  
ใช่ Aspose.Tasks รองรับฐานข้อมูลพื้นฐานหลายรายการ ซึ่งให้ความยืดหยุ่นในการติดตามเวอร์ชันต่างๆ ของโครงการ

### Aspose.Tasks เข้ากันได้กับไฟล์โปรเจ็กต์ที่ไม่ใช่ MPP ได้หรือไม่  
แน่นอน Aspose.Tasks รองรับรูปแบบเช่น XML, MPX และอื่นๆ

### ฉันสามารถอัปเดตข้อมูลพื้นฐานแบบอัตโนมัติได้หรือไม่  
ใช่ API อนุญาตให้ปรับเปลี่ยนพื้นฐานแบบไดนามิกและอัตโนมัติผ่านโปรแกรมได้

### Aspose.Tasks ให้ข้อมูลพื้นฐานแบบแบ่งตามเวลาหรือไม่  
ใช่ สามารถเรียกค้นและวิเคราะห์ข้อมูลพื้นฐานแบบแบ่งช่วงเวลาโดยละเอียดได้

### ฉันสามารถเข้าถึงการสนับสนุนและเอกสารได้ที่ไหน  
 เยี่ยม[เอกสารประกอบ Aspose.Tasks](https://reference.aspose.com/words/net/) หรือเข้าร่วม[ฟอรั่มสนับสนุน Aspose](https://forum.aspose.com/c/words/8) เพื่อขอความช่วยเหลือ 