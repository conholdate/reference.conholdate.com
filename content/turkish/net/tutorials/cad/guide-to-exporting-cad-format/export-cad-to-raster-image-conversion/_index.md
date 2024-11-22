---
title: Aspose.CAD for .NET ile CAD'yi Raster Görüntüye Dönüştürme
linktitle: CAD'yi Raster Görüntü Dönüşümüne Aktarma
second_title: Aspose.CAD .NET - CAD ve BIM Dosya Biçimi
description: Aspose.CAD for .NET kullanarak CAD düzenlerini çeşitli raster görüntü biçimlerine nasıl verimli bir şekilde dönüştüreceğinizi öğrenin. Bu kapsamlı kılavuz, sizi net kodla süreçte yönlendirir.
type: docs
weight: 10
url: /tr/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## giriiş

Aspose.CAD for .NET kullanarak CAD düzenlerini zahmetsizce raster görüntü biçimlerine dönüştürmeyi mi düşünüyorsunuz? Bu adım adım kılavuz, sorunsuz bir deneyim için özlü kod parçacıklarıyla süreci yönetmenize yardımcı olmak için tasarlanmıştır. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu eğitim tüm beceri seviyeleri için değerli içgörüler sağlar.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.CAD for .NET Kütüphanesi: Kütüphaneyi şu adresten indirin ve yükleyin:[Aspose.CAD web sitesi](https://releases.aspose.com/cad/net/).
-  CAD Çizim Dosyası: CAD çizim dosyanızı (örneğin,`conic_pyramid.dxf`) dönüşüme hazır.

## Gerekli Ad Alanlarını İçe Aktar

.NET projenizde, Aspose.CAD fonksiyonlarını kullanmak için gerekli ad alanlarını içe aktarmanız gerekecektir. Aşağıdakileri kodunuzun en üstüne ekleyin:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Adım 1: CAD Çiziminizi Yükleyin

Öncelikle dizini belirtin ve CAD dosyanızı bir Image örneğine yükleyin:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// CAD çizimini yükleyin
using (var image = Image.Load(sourceFilePath))
{
    // Sonraki adımlara geçin
}
```

## Adım 2: Rasterleştirme Seçenekleri Oluşturun

Daha sonra, çıktı görüntüsü için istenen boyutları tanımlayarak rasterleştirme seçeneklerini ayarlayın:

```csharp
// CadRasterizationOptions'ı Başlat
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Adım 3: Dönüştürme için Katmanları Belirleyin

Belirli katmanları dönüştürmek istiyorsanız, bunları rasterleştirme seçeneklerinize ekleyin:

```csharp
// Dönüştürülecek katmanı belirtin
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Adım 4: JPEG Dışa Aktarma Seçeneklerini Ayarlayın

Şimdi, dışa aktarmak istediğiniz resim formatına (bu durumda JPEG) ilişkin seçenekler oluşturun:

```csharp
// Dışa aktarma için JpegOptions oluşturun
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Adım 5: JPEG Formatına Aktar

Son olarak dönüştürülen görüntüyü kaydedin:

```csharp
// Çıktı dosyası yolunu tanımlayın ve görüntüyü kaydedin
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Ek Özellik: Tüm Katmanları Dönüştür

CAD çiziminizdeki tüm katmanları dönüştürmek için şu şekilde bir yöntem uygulayabilirsiniz:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Katmanlar arasında gezinin ve her birini ayrı bir JPEG dosyası olarak kaydedin
    // Uygulama kodunuz burada
}
```

## Çözüm

Tebrikler! Aspose.CAD for .NET kullanarak CAD düzenlerini raster görüntü biçimlerine etkili bir şekilde nasıl dönüştüreceğinizi öğrendiniz. Bu kılavuz, verimli CAD dönüşümleri hedefleyen geliştiriciler için uygun, basit bir yaklaşım sunar.

## SSS

### Farklı resim formatlarına aktarım yapabilir miyim?

 Kesinlikle! Sadece takas edin`JpegOptions` diğer biçim seçenekleriyle, örneğin`PngOptions` veya`BmpOptions`, ihtiyaçlarınıza bağlı olarak.

### Deneme sürümü mevcut mu?

 Evet, işlevselliği keşfetmek için şu adımları izleyerek deneme sürümünü indirebilirsiniz:[bağlantı](https://releases.aspose.com/cad/net/).

### Aspose.CAD için desteği nereden bulabilirim?

 Topluluk desteği için Aspose.CAD'e göz atın[forum](https://forum.aspose.com/c/cad/19)veya daha özel bir yardım için lisans satın almayı düşünün.

### Geçici lisanslar mümkün müdür?

 Evet, geçici lisanslar mevcuttur; bir tane talep edebilirsiniz[Burada](https://purchase.conholdate.com/temporary-license/).

### Ayrıntılı dokümanlara nereden ulaşabilirim?

 Kapsamlı belgeleri ziyaret edin[Burada](https://reference.aspose.com/cad/net/) Daha fazla bilgi için.