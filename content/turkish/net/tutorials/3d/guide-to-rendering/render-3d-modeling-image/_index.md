---
title: Aspose.3D for .NET ile 3D Modelleme Görüntüsünü Oluşturun
linktitle: Kameradan 3D Model Görüntüsünün Oluşturulması
second_title: Aspose.3D .NET API
description: Kutular ve silindirler dahil olmak üzere ilkel 3B modelleri nasıl oluşturacağınızı ve özelleştireceğinizi ve bunları zahmetsizce FBX formatında nasıl kaydedeceğinizi öğrenin. İster acemi ister deneyimli bir geliştirici olun, bu adım adım öğretici.
type: docs
weight: 11
url: /tr/net/tutorials/3d/guide-to-rendering/render-3d-modeling-image/
---
## giriiş

3B modelleri çarpıcı görsellere dönüştürmek, özellikle .NET için Aspose.3D gibi güçlü kütüphanelerden yararlanıldığında, yazılım geliştirmede kritik bir beceridir. Bu makalede, bir 3B model görüntüsünü kamera perspektifinden oluşturma sürecinin tamamında size rehberlik edeceğiz. Sonunda, oldukça ayrıntılı 3B oluşturmalar oluşturma, kamera açılarını ayarlama ve daha iyi görsel çıktı için gelişmiş aydınlatma uygulama bilgisine sahip olacaksınız.

## Ön koşullar

Başlamadan önce, Aspose.3D for .NET kullanarak 3B görüntüleri başarıyla işlemek için aşağıdaki ön koşulların mevcut olduğundan emin olun:

-  Aspose.3D for .NET Kütüphanesi: Öncelikle Aspose.3D for .NET kütüphanesini indirin. NuGet kullanarak yükleyebilir veya doğrudan şuradan indirebilirsiniz:[Aspose sürüm sayfası](https://releases.aspose.com/3d/net/).
- 3D Model: 3D modelinizi OBJ, FBX veya 3DS gibi uyumlu bir formatta hazırlayın. Bu eğitim için bir`Aspose3D.obj` dosya.
- .NET Geliştirme Ortamı: Çalışan bir .NET geliştirme ortamınız olduğundan emin olun. Bu eğitim, Visual Studio veya benzer bir IDE kullandığınızı varsayar.

## Gerekli Ad Alanlarını İçe Aktarma

Projenizi kurmanın ilk adımı Aspose.3D için gerekli ad alanlarını eklemektir. Bu, kodunuzun modeli yüklemenize, kamerayı, aydınlatmayı ayarlamanıza ve sahneyi işlemenize yardımcı olacak Aspose.3D işlevselliğine erişmesine olanak tanır.

```csharp
using System;
using System.IO;
using System.Collections;
using Aspose.ThreeD;
using Aspose.ThreeD.Animation;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
using Aspose.ThreeD.Utilities;
using System.Drawing;
using System.Drawing.Imaging;
```

## Adım 1: 3B Sahneyi Yükleyin

Herhangi bir 3B oluşturma iş akışındaki ilk eylem, model, kamera, aydınlatma ve görüntüyü oluşturmak için gereken diğer öğelerden oluşan sahneyi yüklemektir. 3B modelinizi sahneye yüklemenin yolu şöyledir:

```csharp
Scene scene = new Scene();
var path = "YourModelPath/Aspose3D.obj";  // Model yolunuzu buraya belirtin
scene.Open(path);
```

## Adım 2: Kamerayı Kurun

İstenilen perspektiften sahneyi yakalamak için doğru kamerayı ayarlamak çok önemlidir. Bu adımda, bir Perspektif Kamerası oluşturacağız, derinlik için yakın ve uzak düzlemlerini ayarlayacağız ve kamerayı sahne içinde konumlandırarak modeli doğru şekilde yakalayacağız.

```csharp
Camera cam = new Camera(ProjectionType.Perspective);
cam.NearPlane = 1;
cam.FarPlane = 500;
scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(170, 16, 130);  // Kamerayı konumlandırın
cam.LookAt = new Vector3(28, 0, -30);  // Kamera odak noktasını ayarlayın
```

## Adım 3: Sahneye Aydınlatma Ekleyin

Aydınlatma, 3B modelin görünümünü geliştirmede önemli bir rol oynar. Aspose.3D, sahneyi aydınlatmak için nokta ışıklar, yönlü ışıklar ve spot ışıkları gibi farklı ışık türleri eklemenize olanak tanır. Bu adımda, modelin daha gerçekçi görünmesini sağlamak için bu ışıkların bir kombinasyonunu ekleyeceğiz.

```csharp
scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Point,
    ConstantAttenuation = 0.3,
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(30, 10, 10);

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Directional,
    ConstantAttenuation = 0.3,
    Direction = new Vector3(-0.3, -0.4, 0.3),
    Color = new Vector3(Color.White)
});

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Spot,
    CastShadows = true,
    LookAt = new Vector3(28, 10, -30),
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(40, 10, 50);
```

## Adım 4: Görüntü İşleme Seçeneklerini Belirleyin

Artık model, kamera ve ışıklarla sahnemiz olduğuna göre, render seçeneklerini belirtme zamanı geldi. Bu seçenekler, arka plan rengini özelleştirmenize, gölgeleri etkinleştirmenize ve daha gerçekçi bir efekt için doku dizinleri ayarlamanıza olanak tanır.

```csharp
ImageRenderOptions opt = new ImageRenderOptions();
opt.BackgroundColor = Color.AliceBlue;  // Arkaplan rengini ayarlayın
opt.AssetDirectories.Add("YourDocumentDirectory" + "textures");  // Doku dizinini ayarlayın
opt.EnableShadows = true;  //Derinlik için gölgeleri etkinleştirin
```

## Adım 5: Sahneyi Oluşturun

Her şey ayarlandıktan sonra son adım 3B modeli bir görüntü dosyasına dönüştürmektir. Görüntü boyutunu ve biçimini belirtebilirsiniz ve Aspose.3D gerisini halledecektir.

```csharp
scene.Render(cam, "YourOutputDirectory/Render3DModelImageFromCamera.png", new Size(1024, 1024), ImageFormat.Png, opt);
```

Bu, 3B model görüntüsünü PNG formatında belirtilen çıktı dizinine işleyecektir.

## Çözüm

Tebrikler! Artık Aspose.3D for .NET kullanarak bir kamera perspektifinden 3B model görüntüsünün nasıl oluşturulacağını öğrendiniz. Yukarıdaki adımları izleyerek, daha dinamik ve görsel olarak çekici 3B görselleştirmeler oluşturmak için farklı modeller, kamera konumları ve aydınlatma kurulumları deneyebilirsiniz. Aspose.3D, 3B görselleştirmelerinizi projenizin ihtiyaçlarına uyacak şekilde uyarlama esnekliği sunar.

## SSS

### Aspose.3D for .NET'i diğer 3D modelleme araçlarıyla birlikte kullanabilir miyim?

Evet, Aspose.3D OBJ, FBX ve 3DS gibi çeşitli 3D model formatlarını destekler ve bu da onu Blender, 3ds Max ve Maya gibi popüler modelleme araçlarıyla uyumlu hale getirir.

### Görüntüleme sorunlarını nasıl giderebilirim?

Sorun giderme için şunu kontrol edin:[Aspose.3D forumu](https://forum.aspose.com/c/3d/18) yaygın işleme sorunlarına çözümler için. Ayrıntılı rehberlik için belgelere de başvurabilirsiniz.

### Ücretsiz deneme imkanı var mı?

 Evet, Aspose bir[ücretsiz deneme](https://releases.aspose.com/) Aspose.3D'nin tüm özelliklerini keşfetmeniz ve satın alma işlemi yapmadan önce yeteneklerini değerlendirmeniz için.

### Kapsamlı dokümanları nerede bulabilirim?

 .NET için Aspose.3D'ye ilişkin ayrıntılı belgeleri şu adreste bulabilirsiniz:[dokümantasyon sayfası](https://reference.aspose.com/3d/net/)Kütüphanenin özelliklerini ve işlevlerini derinlemesine ele alan .

### Aspose.3D for .NET'i nasıl satın alabilirim?

 Aspose.3D for .NET'i satın almak için şu adresi ziyaret edin:[satın alma sayfası](https://purchase.conholdate.com/buy)İhtiyaçlarınıza uygun lisansı seçebileceğiniz yer.