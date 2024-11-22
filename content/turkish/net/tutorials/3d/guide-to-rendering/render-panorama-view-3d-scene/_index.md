---
title: Aspose.3D for .NET Kullanarak 3B Sahnenin Panorama Görünümünü Oluşturun
linktitle: 3B Sahnenin Panorama Görünümünü Oluşturun
second_title: Aspose.3D .NET API
description: Aspose.3D kullanarak .NET uygulamalarınızda 3B sahnenin çarpıcı panoramik görüntüsünü nasıl oluşturacağınızı öğrenin. Sürükleyici sahne oluşturma için adım adım kılavuzumuzu izleyin.
type: docs
weight: 13
url: /tr/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## giriiş

Sürükleyici, panoramik 3B sahneler oluşturmak, uygulamalarını çarpıcı görsel efektlerle yükseltmek isteyen geliştiriciler için oyunun kurallarını değiştiriyor. İster bir oyun motoru, ister mimari görselleştirme veya sürükleyici web deneyimleri üzerinde çalışıyor olun, 3B sahneleri panoramalar olarak işlemek kullanıcıların her açıdan dinamik bir görünüm deneyimlemelerini sağlar. Aspose.3D for .NET, bu özelliği .NET projelerinize sorunsuz bir şekilde entegre etmek için mükemmel bir araçtır. Bu kapsamlı kılavuz, Aspose.3D for .NET kullanarak bir 3B sahneden bir panorama işleme sürecini size anlatacaktır.

## Ön koşullar

İşleme sürecine başlamadan önce aşağıdakilerin mevcut olduğundan emin olun:

-  .NET için Aspose.3D: Başlamak için, 3B varlıkları işleme ve işleme için gerekli tüm araçları sağlayan Aspose.3D'yi yüklemeniz gerekir.[.NET için Aspose.3D'yi indirin](https://releases.aspose.com/3d/net/) Başlamak için.
- .NET Geliştirme Ortamı: Tamamen yapılandırılmış bir .NET geliştirme ortamı gereklidir. Visual Studio veya başka bir uyumlu IDE'ye sahip olduğunuzdan emin olun.
- Örnek 3D Sahne Dosyası: Aşağıdaki formatlarda herhangi bir 3D sahneyi kullanabilirsiniz:`.glb`, `.fbx` , veya`.obj`Bu eğitim için basit bir "VirtualCity.glb" dosyasını kullanacağız.

Bu ön koşulları yerine getirdikten sonra sahneyi kurmaya geçebiliriz.

## Gerekli Ad Alanlarını İçe Aktar

Aspose.3D ile çalışmak için projemize birkaç ad alanı aktarmamız gerekecek. Bu ad alanları 3B nesneleri, kamera ayarlarını ve işleme seçeneklerini verimli bir şekilde düzenlemenize olanak tanır.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Bu ad alanları, 3B sahneyi yüklemek, kamerayı, aydınlatmayı yapılandırmak ve panoramik görünümü oluşturan render dokularını ayarlamak için gereklidir.

## Adım 1: 3B Sahneyi Uygulamanıza Yükleyin

 İlk adım, 3B sahneyi uygulamanıza yüklemektir. Bu, şu şekilde gerçekleştirilebilir:`Scene` Aspose.3D tarafından sağlanan sınıf. Değiştir`"VirtualCity.glb"` 3D sahne dosyanızın yolunu belirtin.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 The`Scene` nesne 3B sahneyi belleğe yükler, böylece onunla etkileşime girebilir ve işleme teknikleri uygulayabilirsiniz.

## Adım 2: Kamerayı ve Işıkları Ayarlayın

3B sahnenizin doğru şekilde çekildiğinden emin olmak için bir kamera ve uygun aydınlatma ayarlamanız gerekir. Kamera sahnenin perspektifini kontrol etmenizi sağlarken, ışıklar nesneleri aydınlatmaya yardımcı olur.

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

- Kamera Kurulumu: Kameranın yakın ve uzak düzlemleri, 3B sahnedeki görünür aralığı tanımlayacak şekilde ayarlanır.
- Işık Kurulumu: Sahneye derinlik ve gerçekçilik katmak için bir nokta ışığı ve belirli bir renkte bir ışık olmak üzere iki ışık eklenir.

## Adım 3: Renderer'ı Ayarlayın ve Render Hedeflerini Tanımlayın

Artık sahneniz, kameranız ve ışıklarınız ayarlandığına göre, bir sonraki adım render aracını oluşturmak ve render hedeflerini tanımlamaktır. Render aracı 3B görüntüleri oluşturmaktan sorumludur ve render hedefleri son çıktının nerede saklanacağını tanımlar.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Cube Render Texture: Bu, panoramik görünüm için bir küp haritasının render edilmesinde kullanılır. Burada 512x512'lik bir doku tanımlıyoruz.
- Son Render Dokusu: Bu, son dikdörtgen panoramik görünümü tutacak dokudur.

## Adım 4: Görünüm Penceresini Yapılandırın ve Sahneyi İşleyin

Render dokularını oluşturduktan sonra, kameranın 3B sahnenin hangi bölgesini yakalayacağını tanımlayan görünüm alanını yapılandırmamız gerekiyor.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Bu kod, küp haritası için görünüm alanını ayarlar ve sahneyi şu şekilde işler:`rt` dokuyu işle.

## Adım 5: Eşdikdörtgensel Projeksiyon için Son İşlemi Uygulayın

Bu noktada, küp haritasını eşkenar dörtgen panoramik görünüme dönüştürmek için son işlemeyi uygulamamız gerekir. Bu dönüşüm, son görüntünün düzgün bir panorama olmasını sağlar.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Eşkenar Dörtgen Projeksiyon: Bu son işlem efekti küp haritasını alır ve onu eşkenar dörtgen panoramik projeksiyona dönüştürerek kusursuz 360 derecelik bir görünüm sağlar.

## Adım 6: İşlenen Panoramayı Kaydedin

İşleme ve son işlem tamamlandıktan sonra, son adım nihai panoramayı PNG gibi bir görüntü dosyasına kaydetmektir.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Bu, panoramik görüntüyü belirtilen dizine kaydeder ve bunu uygulamanıza entegre etmenize veya bir web sitesinde görüntülemenize olanak tanır.

## Çözüm

3B sahnelerin panoramik görünümlerini işlemek Aspose.3D for .NET ile hiç bu kadar kolay olmamıştı. Yukarıda özetlenen adımları izleyerek, kolayca bir 3B sahne yükleyebilir, kamerayı ve ışıkları yapılandırabilir, sahneyi işleyebilir ve sürükleyici panoramik görüntüler oluşturmak için son işlem efektleri uygulayabilirsiniz. Aspose.3D for .NET, 3B görselleştirmelerinizi hayata geçirmek ve bunları uygulamalarınıza sorunsuz bir şekilde entegre etmek için güç ve esneklik sağlar.

## SSS

### Panoramaları oluştururken kendi 3D sahnemi kullanabilir miyim?
Kesinlikle. Örnek sahne dosya yolunu özel 3D sahnenizin konumuyla değiştirmeniz yeterlidir.

### Herhangi bir ek son işlem efekti mevcut mu?
Evet, Aspose.3D, işlenmiş görüntülerinizi geliştirmek için uygulanabilen alan derinliği, parlaklık ve daha fazlası gibi bir dizi son işlem efekti sunar.

### Render performansını nasıl optimize edebilirim?
Render performansı, render doku boyutu ve çözünürlük gibi parametrelerin ayarlanması ve kameranın yakın ve uzak düzlemlerinin ayarlanmasıyla optimize edilebilir.

### Bunu bir web uygulamasına entegre edebilir miyim?
Evet, Aspose.3D for .NET, 3 boyutlu panoramaları dinamik olarak oluşturmak için .NET web uygulamalarınıza entegre edilebilir.

### Aspose.3D desteği için bir topluluk forumu var mı?
 Evet, ziyaret edebilirsiniz[Aspose.3D forumu](https://forum.aspose.com/c/3d/18) destek ve topluluk tartışmaları için.