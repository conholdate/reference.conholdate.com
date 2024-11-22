---
title: XPS'i Aspose.Page for .NET ile PDF'ye dönüştürme
linktitle: XPS'i PDF'e dönüştürme
second_title: Aspose.Page .NET API
description: Güçlü Aspose.Page for .NET kütüphanesini kullanarak XPS (XML Kağıt Spesifikasyonu) belgelerini sorunsuz bir şekilde PDF'ye (Taşınabilir Belge Biçimi) nasıl dönüştüreceğinizi keşfedin.
type: docs
weight: 11
url: /tr/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## giriiş

Bu eğitimde, çok yönlü Aspose.Page for .NET kütüphanesini kullanarak XPS (XML Paper Specification) belgelerini PDF'ye (Portable Document Format) nasıl dönüştüreceğinizi inceleyeceğiz. Bu güçlü kütüphane, belge dönüşümünü basitleştirir ve çeşitli özelleştirme seçenekleri sunarak onu geliştiriciler için mükemmel bir seçim haline getirir.

## Ön koşullar

Başlamadan önce aşağıdakilerin mevcut olduğundan emin olun:

-  Aspose.Page for .NET Kitaplığı: Aspose.Page for .NET kitaplığını şu adresten indirin ve yükleyin:[Aspose.Page belgeleri](https://reference.aspose.com/page/net/).
  
- Geliştirme Ortamı: Visual Studio veya uyumlu başka bir IDE kullanarak bir .NET geliştirme ortamı kurun.

- XPS Belgesi: Dönüştürmek istediğiniz XPS dosyasını hazır bulundurun ve belirlenmiş bir dizinde saklayın.

## Adım 1: Gerekli Ad Alanlarını İçe Aktarın

Aspose.Page işlevlerine erişmek için gerekli ad alanını içe aktararak başlayın:

```csharp
using Aspose.Page.XPS;
```

## Adım 2: Belge Dizinini Başlatın

Belgelerinizin saklandığı dizin yolunu tanımlayın:

```csharp
string dataDir = "Your Document Directory";
```

 Değiştirdiğinizden emin olun`"Your Document Directory"` XPS belgenizi içeren dizinin gerçek yolu ile.

### Adım 3: PDF ve XPS Akışlarını Açın

Sonra, hem giriş XPS dosyası hem de çıkış PDF dosyası için akışları başlatın:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Dosyalarınız için doğru yolu ayarladığınızdan emin olun.

### Adım 4: XPS Belgesini Yükleyin

Şimdi Aspose.Page kütüphanesini kullanarak XPS belgenizi yükleyin:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Adım 5: PDF Kaydetme Seçeneklerini Yapılandırın

PDF'niz için görüntü kalitesi ve sıkıştırma parametreleri dahil olmak üzere kaydetme seçeneklerini ayarlayın:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // JPEG kalite seviyesini ayarlayın
    ImageCompression = PdfImageCompression.Jpeg, // Görüntüler için JPEG sıkıştırmasını kullanın
    TextCompression = PdfTextCompression.Flate, // Metin için Flate sıkıştırmayı uygula
    PageNumbers = new int[] { 1, 2, 6 } // Dahil edilecek sayfa numaralarını belirtin
};
```

İhtiyaçlarınıza göre bu parametreleri ayarlamaktan çekinmeyin.

### Adım 6: PDF İşleme Aygıtını Oluşturun

PDF formatı için bir işleme aygıtı oluşturun:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Adım 7: Belgeyi PDF olarak kaydedin

Son olarak, XPS belgesini belirtilen aygıt ve seçenekleri kullanarak PDF'e kaydedin:

```csharp
document.Save(device, options);
```

## Çözüm

Tebrikler! Aspose.Page for .NET kullanarak bir XPS belgesini PDF'ye başarıyla dönüştürdünüz. Bu kütüphane yalnızca belge dönüşümünü basitleştirmekle kalmaz, aynı zamanda çeşitli biçimleri işlemek için kapsamlı yetenekler de sunar.

## SSS

### Birden fazla XPS dosyasını tek bir PDF'ye dönüştürebilir miyim?

Kesinlikle! Birden fazla XPS dosyası arasında geçiş yapabilir ve aynı dönüştürme adımlarını izleyerek bunları tek bir PDF belgesinde birleştirebilirsiniz.

### Aspose.Page for .NET hangi diğer çıktı biçimlerini destekler?

Aspose.Page for .NET, PDF'nin yanı sıra TIFF, JPEG ve PNG gibi çeşitli formatları da destekler.

### Dönüştürülen PDF'in görünümünü nasıl özelleştirebilirim?

 Parametreleri şurada ayarlayabilirsiniz:`PdfSaveOptions` İstediğiniz görünümü elde etmek için nesneyi JPEG kalitesi ve sıkıştırma ayarları gibi ayarlara göre ayarlayın.

### Aspose.Page for .NET için deneme sürümü mevcut mu?

Evet, .NET için Aspose.Page'i ücretsiz deneme sürümüyle deneyebilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Page for .NET için topluluk desteğini nerede bulabilirim?

 Topluluk tartışmaları ve desteği için şu adresi ziyaret edin:[Aspose.Page forumu](https://forum.aspose.com/c/page/39).