---
title: عرض عرض بانورامي لمشهد ثلاثي الأبعاد باستخدام Aspose.3D لـ .NET
linktitle: تقديم عرض بانورامي لمشهد ثلاثي الأبعاد
second_title: واجهة برمجة تطبيقات Aspose.3D .NET
description: تعرف على كيفية تقديم عرض بانورامي مذهل لمشهد ثلاثي الأبعاد في تطبيقات .NET الخاصة بك باستخدام Aspose.3D. اتبع دليلنا خطوة بخطوة لتقديم مشهد غامر.
type: docs
weight: 13
url: /ar/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## مقدمة

إن إنشاء مشاهد ثلاثية الأبعاد بانورامية غامرة يعد بمثابة تغيير كبير للمطورين الذين يتطلعون إلى الارتقاء بتطبيقاتهم بتأثيرات بصرية مذهلة. سواء كنت تعمل على محرك ألعاب أو تصور معماري أو تجارب ويب غامرة، فإن عرض المشاهد ثلاثية الأبعاد كصور بانورامية يسمح للمستخدمين بتجربة عرض ديناميكي من جميع الزوايا. يعد Aspose.3D for .NET الأداة المثالية لدمج هذه الميزة بسلاسة في مشاريع .NET الخاصة بك. سيرشدك هذا الدليل الشامل خلال عملية عرض صورة بانورامية من مشهد ثلاثي الأبعاد باستخدام Aspose.3D for .NET.

## المتطلبات الأساسية

قبل الخوض في عملية العرض، تأكد من توفر العناصر التالية:

- Aspose.3D لـ .NET: للبدء، تحتاج إلى تثبيت Aspose.3D، الذي يوفر لك جميع الأدوات اللازمة للتعامل مع الأصول ثلاثية الأبعاد والرسم.[تنزيل Aspose.3D لـ .NET](https://releases.aspose.com/3d/net/) للبدء.
- بيئة تطوير .NET: يلزم توفر بيئة تطوير .NET مهيأة بالكامل. تأكد من توفر Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة.
-  ملف مشهد ثلاثي الأبعاد: يمكنك استخدام أي مشهد ثلاثي الأبعاد بتنسيقات مثل`.glb`, `.fbx` ، أو`.obj`في هذا البرنامج التعليمي، سنستخدم ملف "VirtualCity.glb" البسيط.

بمجرد أن تغطي هذه المتطلبات الأساسية، يمكننا الانتقال إلى إعداد المشهد.

## استيراد المساحات الاسمية الضرورية

للعمل مع Aspose.3D، سنحتاج إلى استيراد عدة مساحات أسماء إلى مشروعنا. تتيح لك هذه المساحات الأسماء التعامل مع الكائنات ثلاثية الأبعاد وإعدادات الكاميرا وخيارات العرض بكفاءة.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

تُعد هذه المساحات الأساسية ضرورية لتحميل المشهد ثلاثي الأبعاد، وتكوين الكاميرا، والإضاءة، وإعداد أنسجة العرض التي تشكل العرض البانورامي.

## الخطوة 1: قم بتحميل المشهد ثلاثي الأبعاد إلى تطبيقك

 الخطوة الأولى هي تحميل المشهد ثلاثي الأبعاد إلى تطبيقك. ويمكن تحقيق ذلك باستخدام`Scene` تم توفير الفئة بواسطة Aspose.3D. استبدل`"VirtualCity.glb"` مع المسار إلى ملف المشهد ثلاثي الأبعاد الخاص بك.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 ال`Scene` يقوم الكائن بتحميل المشهد ثلاثي الأبعاد في الذاكرة، مما يسمح لك بالتفاعل معه وتطبيق تقنيات العرض.

## الخطوة 2: إعداد الكاميرا والأضواء

لضمان التقاط المشهد ثلاثي الأبعاد بشكل صحيح، ستحتاج إلى إعداد كاميرا وإضاءة مناسبة. تتيح لك الكاميرا التحكم في منظور المشهد، بينما تساعد الأضواء في إضاءة الكائنات.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- إعداد الكاميرا: يتم ضبط المستويات القريبة والبعيدة للكاميرا لتحديد النطاق المرئي في المشهد ثلاثي الأبعاد.
- إعداد الإضاءة: تمت إضافة ضوءين - نقطة ضوء واحدة وضوء آخر بلون محدد لإضافة العمق والواقعية إلى المشهد.

## الخطوة 3: إعداد برنامج العرض وتحديد أهداف العرض

الآن بعد أن تم ضبط المشهد والكاميرا والأضواء، فإن الخطوة التالية هي إنشاء برنامج العرض وتحديد أهداف العرض. برنامج العرض مسؤول عن إنشاء الصور ثلاثية الأبعاد، وتحدد أهداف العرض مكان تخزين الناتج النهائي.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- نسيج عرض المكعب: يستخدم هذا النسيج لعرض خريطة مكعب لعرض بانورامي. نحدد نسيجًا بحجم 512x512 هنا.
- الملمس النهائي: هذا هو الملمس الذي سيحمل المنظر البانورامي المستطيلي النهائي.

## الخطوة 4: تكوين Viewport وعرض المشهد

بعد إنشاء أنسجة العرض، نحتاج إلى تكوين منفذ العرض، الذي يحدد منطقة المشهد ثلاثي الأبعاد التي ستلتقطها الكاميرا.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 يقوم هذا الكود بتعيين منفذ العرض لخريطة المكعب ويعرض المشهد في`rt` تقديم الملمس.

## الخطوة 5: تطبيق المعالجة اللاحقة للإسقاط المستطيلي المتساوي الأضلاع

في هذه المرحلة، نحتاج إلى تطبيق المعالجة اللاحقة لتحويل خريطة المكعب إلى عرض بانورامي مستطيل الشكل. يضمن هذا التحويل أن الصورة النهائية ستكون بانوراما مناسبة.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- إسقاط مستطيل الشكل: يأخذ هذا التأثير بعد المعالجة خريطة المكعب ويحولها إلى إسقاط بانورامي مستطيل الشكل، مما يوفر رؤية سلسة بزاوية 360 درجة.

## الخطوة 6: احفظ الصورة البانورامية المرسومة

بمجرد اكتمال عملية العرض والمعالجة اللاحقة، تكون الخطوة الأخيرة هي حفظ الصورة البانورامية النهائية في ملف صورة، مثل PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

يؤدي هذا إلى حفظ الصورة البانورامية في الدليل المحدد، مما يسمح لك بدمجها في تطبيقك أو عرضها على موقع ويب.

## خاتمة

لم يكن عرض المناظر البانورامية للمشاهد ثلاثية الأبعاد أسهل من أي وقت مضى مع Aspose.3D for .NET. باتباع الخطوات الموضحة أعلاه، يمكنك بسهولة تحميل مشهد ثلاثي الأبعاد، وتكوين الكاميرا والأضواء، وعرض المشهد، وتطبيق تأثيرات ما بعد المعالجة لتوليد صور بانورامية غامرة. يوفر Aspose.3D for .NET القوة والمرونة لإضفاء الحيوية على التصورات ثلاثية الأبعاد ودمجها بسلاسة في تطبيقاتك.

## الأسئلة الشائعة

### هل يمكنني استخدام المشهد ثلاثي الأبعاد الخاص بي لتقديم الصور البانورامية؟
بالتأكيد. ما عليك سوى استبدال مسار ملف المشهد النموذجي بموقع المشهد ثلاثي الأبعاد المخصص.

### هل هناك أي تأثيرات إضافية متاحة بعد المعالجة؟
نعم، يوفر Aspose.3D مجموعة من تأثيرات ما بعد المعالجة، مثل عمق المجال، والازدهار، والمزيد، والتي يمكن تطبيقها لتحسين الصور المقدمة.

### كيف يمكنني تحسين أداء العرض؟
يمكن تحسين أداء العرض عن طريق ضبط المعلمات مثل حجم نسيج العرض والدقة، بالإضافة إلى تعديل المستويات القريبة والبعيدة للكاميرا.

### هل يمكنني دمج هذا في تطبيق ويب؟
نعم، يمكن دمج Aspose.3D for .NET في تطبيقات الويب .NET الخاصة بك لعرض الصور البانورامية ثلاثية الأبعاد بشكل ديناميكي.

### هل يوجد منتدى مجتمعي لدعم Aspose.3D؟
 نعم يمكنك الزيارة[منتدى Aspose.3D](https://forum.aspose.com/c/3d/18) للحصول على الدعم والمناقشات المجتمعية.