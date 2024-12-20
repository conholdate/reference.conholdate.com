---
title: Bradley Binarizasyon Algoritması
linktitle: Bradley Binarizasyon Algoritması
second_title: Aspose.PDF for .NET API Referansı
description: Aspose.PDF for .NET'te bradley binarizasyon algoritmasını kullanarak PDF sayfalarını yüksek kaliteli ikili TIFF görüntülerine nasıl dönüştüreceğinizi öğrenin. Bu adım adım kılavuz kod örneği içerir.
type: docs
weight: 30
url: /tr/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## giriiş

Bu eğitimde, Bradley Binarization Algoritması'nı kullanarak bir PDF sayfasını TIFF görüntüsüne dönüştürme sürecinde size rehberlik edeceğiz. Aspose.PDF for .NET bu görevi basitleştirerek belge iş akışlarınızı kolaylıkla otomatikleştirmenize ve düzenlemenize olanak tanır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  .NET için Aspose.PDF: Kütüphaneyi şu adresten indirin:[Burada](https://releases.aspose.com/pdf/net/).
- Visual Studio (veya herhangi bir C# IDE).
- Temel C# bilgisi.
-  Geçerli bir lisans veya[geçici lisans](https://purchase.aspose.com/temporary-license/) Aspose'dan.

## Adım 1: Projenizi Kurun

Öncelikle IDE'nizde yeni bir C# projesi oluşturun ve gerekli ad alanlarını içe aktarın:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Adım 2: Belge Dizinini Tanımlayın

PDF belgenizin bulunduğu dizinin yolunu ve TIFF görüntüleri için çıktı yollarını belirtin:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // PDF dosyanıza giden yol
```

Bu dizin hem kaynak PDF'i hem de dönüştürülmüş TIFF dosyalarını saklayacaktır.

## Adım 3: PDF Belgesini Yükleyin

Dönüştürmek istediğiniz PDF belgesini açın:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Yer değiştirmek`PageToTIFF.pdf` PDF dosyanızın adıyla.

## Adım 4: Çıktı Yollarını Belirleyin

Oluşturulan TIFF dosyaları için çıktı yollarını tanımlayın:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Adım 5: Görüntü Çözünürlüğünü Ayarlayın

TIFF görüntüleri için çözünürlüğü ayarlayın. Daha yüksek bir DPI daha iyi görüntü kalitesi sağlayacaktır:

```csharp
Resolution resolution = new Resolution(300);
```

## Adım 6: TIFF Ayarlarını Yapılandırın

Sıkıştırma ve renk derinliği dahil olmak üzere TIFF görüntüsü için ayarları yapılandırın:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

1bpp (piksel başına 1 bit) kullanımı görüntüyü ikili çıktı için hazırlar.

## Adım 7: TIFF Aygıtını Oluşturun

Dönüştürmeyi gerçekleştirecek bir TIFF aygıtı oluşturun:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Adım 8: PDF Sayfasını TIFF'e Dönüştürün

PDF'in ilk sayfasını TIFF görüntüsüne dönüştürün:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Adım 9: Bradley İkilileştirme Algoritmasını Uygulayın

Şimdi, gri tonlamalı TIFF görüntüsünü ikili görüntüye dönüştürmek için Bradley Algoritmasını uygulayın:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 The`BinarizeBradley` yöntem iki dosya akışı (giriş ve çıkış) ve bir eşik değeri alır. En iyi sonuçlar için eşik değerini gerektiği gibi ayarlayın.

## Adım 10: Başarılı Dönüşümü Onaylayın

Son olarak dönüşümün başarılı olduğunu doğrulayın:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Çözüm

Tebrikler! Bir PDF sayfasını TIFF görüntüsüne başarıyla dönüştürdünüz ve Aspose.PDF for .NET kullanarak Bradley İkilileştirme Algoritmasını uyguladınız. Bu işlem belge arşivleme, OCR ve diğer profesyonel uygulamalar için olmazsa olmazdır. Yüksek kaliteli çözünürlük ve etkili sıkıştırma ile belge görüntüleriniz net ve boyut olarak yönetilebilir olacaktır.

## SSS

### Bradley Algoritması Nedir?
Bradley Algoritması, her piksel için çevresine bağlı olarak uyarlanabilir bir eşik değeri belirleyerek gri tonlamalı görüntüleri ikili görüntülere dönüştüren bir ikilileştirme tekniğidir.

### Bu yöntemi kullanarak birden fazla PDF sayfasını TIFF'e dönüştürebilir miyim?
 Evet, değiştirebilirsiniz`Process` Dönüştürme için belgedeki tüm sayfalarda döngü oluşturma yöntemi.

### PDF'leri TIFF'e dönüştürmek için en uygun çözünürlük nedir?
Yüksek kaliteli görüntüler için genellikle 300 DPI çözünürlük önerilir, ancak bunu özel ihtiyaçlarınıza göre ayarlayabilirsiniz.

### Renk derinliğinde 1bpp ne anlama geliyor?
1bpp (piksel başına 1 bit), görüntünün siyah beyaz olacağını ve her pikselin ya tamamen siyah ya da tamamen beyaz olacağını belirtir.

### Bradley Algoritması OCR için uygun mudur?
Evet, Bradley Algoritması taranan belgelerdeki metinlerin kontrastını artırarak tanıma doğruluğunu iyileştirdiği için OCR ön işlemede sıklıkla kullanılır.