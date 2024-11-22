---
title: .NET için Aspose.PSD'de Bradley Eşiklemeyi Uygulayın
linktitle: Bradley Eşiklemeyi Uygula
second_title: Aspose.PSD .NET API
description: PSD dosyalarının nasıl yükleneceğini, eşikleme tekniklerinin nasıl uygulanacağını ve sonuçlarınızın çeşitli formatlarda nasıl kaydedileceğini adım adım öğrenerek, farklı uygulamalar için görüntü segmentasyon görevlerinizi geliştirin.
type: docs
weight: 15
url: /tr/net/tutorials/psd/guide-image-processing/apply-bradley-thresholding/
---
## giriiş

Bradley Threshold tekniğini Aspose.PSD for .NET kullanarak uygulama eğitimimize hoş geldiniz. Bu güçlü kütüphane, .NET uygulamaları içinde Photoshop dosyalarının sorunsuz bir şekilde işlenmesini sağlar. Bradley Thresholding, nesneleri arka planlarından ayırt etmeye yardımcı olan görüntü ikilileştirme için etkili bir yöntemdir.

## Ön koşullar

İşleme başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

-  Aspose.PSD for .NET Kütüphanesi: En son sürümü indirin ve yükleyin[belgeleme](https://reference.aspose.com/psd/net/).
- Belge Dizini: Kaynak PSD dosyanızı ve çıktı ikili görüntüsünü depolamak için bir çalışma dizini oluşturun.

## Gerekli Ad Alanlarını İçe Aktar

Aspose.PSD işlevlerine erişmek için ilgili ad alanlarını içe aktararak projenize başlayın:

```csharp
// Aspose.PSD ad alanlarını içe aktar
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## Adım 1: Kaynak Görüntünüzü Yükleyin

Belge dizininize giden yolu, kaynak PSD dosyasını ve çıktı dosyasının adını tanımlayın:

```csharp
// Belgelerinizin dizinine giden yolu belirtin
string dataDir = "Your Document Directory";

string sourceFile = Path.Combine(dataDir, "sample.psd");
string outputFile = Path.Combine(dataDir, "binarized_out.png");
```

## Adım 2: Bradley Eşiğini Uygulayın

Daha sonra PSD görüntüsünü yükleyin, eşik değerinizi seçin, Bradely eşikleme yöntemini uygulayın ve sonuçları kaydedin:

```csharp
// PSD görüntüsünü yükleyin
using (PsdImage image = (PsdImage)Image.Load(sourceFile))
{
    // Eşik değerini ayarlayın (gerektiğinde bu değerle denemeler yapın)
    double threshold = 0.15;

    // Bradley yöntemini kullanarak görüntüyü ikili hale getirin
    image.BinarizeBradley(threshold);

    // İkili hale getirilmiş görüntüyü PNG formatında kaydedin
    image.Save(outputFile, new PngOptions());
}
```

## Çözüm

Tebrikler! Bradley Threshold tekniğini Aspose.PSD for .NET kullanarak başarıyla uyguladınız. Bu yöntem, belge analizinden grafik tasarımına kadar çeşitli uygulamalar için görüntü segmentasyonunu büyük ölçüde iyileştirebilir.

## SSS

### Bradley Threshold'u her türlü görüntüye uygulayabilir miyim?

Kesinlikle! Bradley Eşikleme çok yönlüdür ve segmentasyonu geliştirmek için çoğu görüntü türüne uygulanabilir.

### Aspose.PSD hakkında daha fazla bilgiyi nerede bulabilirim?

 Ayrıntılı belgeler ve kaynaklar için şu adresi ziyaret edin:[Aspose.PSD belgeleri](https://reference.aspose.com/psd/net/).

### Deneme sürümü mevcut mu?

 Evet! Aspose.PSD for .NET'i ücretsiz deneme sürümüyle deneyebilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.PSD için nasıl destek alabilirim?

 Topluluk desteği ve tartışmaları için şuraya göz atın:[Aspose.PSD forumu](https://forum.aspose.com/c/psd/34).

### Aspose.PSD için lisansı nasıl satın alabilirim?

 Lisansı doğrudan satın alabilirsiniz[Burada](https://purchase.conholdate.com/buy).