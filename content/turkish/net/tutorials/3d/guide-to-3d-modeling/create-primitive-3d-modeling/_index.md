---
title: İlkel 3B Modelleme Oluşturun
linktitle: İlkel 3B Modelleme Oluşturun
second_title: Aspose.3D .NET API
description: Kutular ve silindirler de dahil olmak üzere ilkel 3B modelleri nasıl oluşturacağınızı ve özelleştireceğinizi ve bunları FBX formatında zahmetsizce nasıl kaydedeceğinizi öğrenin.
type: docs
weight: 10
url: /tr/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## giriiş

Aspose.3D for .NET kullanarak 3B modellemenin sürükleyici dünyasına hoş geldiniz! Bu kapsamlı eğitimde, ilkel 3B modeller oluşturma sürecinde adım adım size rehberlik edeceğiz. İster deneyimli bir geliştirici olun, ister öğrenmeye hevesli bir acemi, bu rehber projeleriniz için görsel olarak çarpıcı 3B öğeler oluşturmanıza olanak tanıyacak.

## Ön koşullar

3D modellemeye başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

-  Aspose.3D for .NET: Aspose.3D for .NET kitaplığını şu adresten indirin ve yükleyin:[indirme sayfası](https://releases.aspose.com/3d/net/).
  
- .NET Geliştirme Ortamı: Visual Studio gibi Aspose.3D ile uyumlu bir ortam kurun.

Her şeyi hazırladıktan sonra 3D modelleme maceramıza başlayalım!

## Gerekli Ad Alanlarını İçe Aktarma

Aspose.3D işlevlerine erişmek için gerekli ad alanlarını içe aktararak başlayın:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Bu ad alanları, 3B modelleri düzenlemek ve yarattıklarınızı kaydetmek için gerekli araçları size sağlayacaktır.

## Adım 1: Bir Sahne Nesnesini Başlatın

3B modelleriniz için tuval görevi görecek yeni bir sahne nesnesi oluşturun:

```csharp
// Bir Sahne nesnesini başlatın
Scene scene = new Scene();
```

Bu sahne, yaratmak üzere olduğunuz ilkel şekilleri içerecektir.

## Adım 2: Bir Kutu Modeli Oluşturun

Şimdi sahnenize bir kutu modeli ekleyelim:

```csharp
// Bir Kutu modeli oluşturun
scene.RootNode.CreateChildNode("box", new Box());
```

Kutunun boyutlarını ve özelliklerini yaratıcı vizyonunuza uyacak şekilde özelleştirebilirsiniz.

## Adım 3: Bir Silindir Modeli Oluşturun

Şimdi sahnenizi bir silindir ekleyerek geliştirin:

```csharp
// Bir Silindir modeli oluşturun
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Kutuda olduğu gibi, silindirin parametrelerini istediğiniz görünüme kavuşacak şekilde ayarlayabilirsiniz.

## Adım 4: Sahneyi FBX Formatında Kaydedin

3D modelinizi korumak için onu FBX formatında kaydedin:

```csharp
// Çizimi FBX formatında kaydet
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Modeliniz için uygun bir çıktı dizini ve dosya adı seçtiğinizden emin olun.

## Adım 5: Başarılı Mesajını Göster

Son olarak, şu mesajı görüntüleyerek başarınızı kutlayın:

```csharp
// Başarı mesajını görüntüle
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

İlkel modellerden oluşan 3 boyutlu sahneniz artık tamamlandı ve kaydedildi!

## Çözüm

 .NET için Aspose.3D kullanarak çarpıcı 3B modeller oluşturduğunuz için tebrikler! Bu eğitim ilkel modellemenin temellerini kapsıyordu, ancak olasılıklar sınırsız. Gelişmiş özellikler ve teknikler hakkında daha fazlasını keşfedin[belgeleme](https://reference.aspose.com/3d/net/).

## SSS

### Aspose.3D for .NET'i .NET dışındaki programlama dilleriyle kullanabilir miyim?

Aspose.3D esas olarak .NET'i destekler, ancak Java ve diğer platformlar için de sürümleri mevcuttur.

### Ücretsiz deneme imkanı var mı?

 Evet, Aspose.3D'nin yeteneklerini şu şekilde deneyebilirsiniz:[ücretsiz deneme](https://releases.aspose.com/).

### Aspose.3D for .NET desteğini nerede bulabilirim?

Topluluk desteği için şu adresi ziyaret edin:[Aspose.3D forumu](https://forum.aspose.com/c/3d/18).

### Geçici ehliyet nasıl alabilirim?

 Geçici lisans talebinde bulunabilirsiniz[Burada](https://purchase.conholdate.com/temporary-license/).

### Ek eğitimler mevcut mu?

 Evet! Daha fazla öğretici ve örneği keşfedin[belgeleme](https://reference.aspose.com/3d/net/).