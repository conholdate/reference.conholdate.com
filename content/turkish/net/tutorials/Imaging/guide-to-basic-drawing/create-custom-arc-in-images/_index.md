---
title: Aspose.Imaging for .NET Kullanarak Görüntülerde Özel Yaylar Oluşturma
linktitle: Aspose.Imaging for .NET Kullanarak Görüntülerde Özel Yaylar Oluşturma
second_title: Aspose.Imaging .NET Görüntü İşleme API'si
description: Aspose.Imaging for .NET kullanarak resimlerde özel yaylar çizmeyi öğrenin. Resminizi kurmak, grafik bağlamını başlatmak, yay parametrelerini tanımlamak ve son çıktıyı kaydetmek için adım adım talimatları izleyin.
type: docs
weight: 10
url: /tr/net/tutorials/imaging/guide-to-basic-drawing/create-custom-arc-in-images/
---
## giriiş

Aspose.Imaging for .NET, geliştiricilere görüntüleri etkili bir şekilde işlemek ve oluşturmak için gerekli araçları sağlayan, görüntü işleme görevleri için tasarlanmış gelişmiş bir kütüphanedir. Bu eğitimde, bu güçlü kütüphaneyi kullanarak bir görüntüye yay çizme sürecinde size rehberlik edeceğiz. Bu kılavuzun sonunda, projelerinize sorunsuz bir şekilde yaylar dahil edebileceksiniz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Imaging for .NET: Eğer henüz yüklemediyseniz, şu adresten indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/imaging/net/).

2. Geliştirme Ortamı: C# kodu yazıp çalıştırabileceğiniz çalışan bir .NET geliştirme ortamı (örneğin Visual Studio).

Bu ön koşullar sağlandıktan sonra, bir yay çizmeye başlayabiliriz!

## Gerekli Ad Alanlarını İçe Aktar

 Öncelikle, Aspose.Imaging tarafından sağlanan işlevselliğe erişmek için gerekli ad alanlarını içe aktarmanız gerekir. Aşağıdakileri ekleyin`using` C# dosyanızın en üstündeki ifadeler:

```csharp
using Aspose.Imaging;
using Aspose.Imaging.Brushes;
using Aspose.Imaging.FileFormats.Bmp;
using Aspose.Imaging.Sources;
using System;
using System.Drawing;
using System.IO;
```

## Adım 1: Görüntüyü Oluşturun ve Akışı Kaydedin

```csharp
// Görüntünün kaydedileceği dizini tanımlayın
string dataDir = "Your Document Directory"; // Bunu tercih ettiğiniz yola güncelleyin

// BMP görüntüsünü kaydetmek için bir akış oluşturun
using (FileStream stream = new FileStream(Path.Combine(dataDir, "DrawingArc_out.bmp"), FileMode.Create))
{
    // BmpOptions'ı örneklendirin ve yapılandırın
    BmpOptions saveOptions = new BmpOptions
    {
        BitsPerPixel = 32,
        Source = new StreamSource(stream)
    };

    // Belirtilen seçeneklerle bir görüntü oluşturun
    using (Image image = Image.Create(saveOptions, 100, 100))
    {
```

- Oluşturulan görselin kaydedileceği yolu belirtiyoruz.
- 32 bit renk derinliğine sahip bir BMP görüntüsü oluşturuyoruz.

## Adım 2: Grafik Bağlamını Başlatın

Daha sonra, görüntüyü düzenlemek için grafik bağlamını başlatıyoruz:

```csharp
        // Graphics nesnesini başlatın ve bir arka plan rengi ayarlayın
        using (Graphics graphic = new Graphics(image))
        {
            graphic.Clear(Color.Yellow); // Sarı arka planlı görüntüyü temizleyin
```

Bu kısımda görünürlüğü arttırmak için görüntü yüzeyini sarı renkle temizliyoruz.

## Adım 3: Yayı çizin

Şimdi yayın parametrelerini tanımlayalım ve çizelim:

```csharp
            // Ark için parametreleri tanımlayın
            int width = 100;   // Sınırlayıcı dikdörtgenin genişliği
            int height = 200;  // Sınırlayıcı dikdörtgenin yüksekliği
            int startAngle = 45;  // Başlangıç açısı derece cinsinden
            int sweepAngle = 270; // Derece cinsinden tarama açısı

            // Yayı çiz
            graphic.DrawArc(new Pen(Color.Black), 0, 0, width, height, startAngle, sweepAngle);
```

Bu kod, yay için boyutları ve açıları ayarlar ve onu çizmek için siyah bir kalem kullanır.

## Adım 4: Görüntüyü Kaydedin

Son olarak görselde yaptığımız değişiklikleri kaydediyoruz:

```csharp
            // Çizilen yayla görüntüyü kaydedin
            image.Save();
        } // Grafik nesnesi otomatik olarak elden çıkarılır
    } // FileStream otomatik olarak atılır
}
```

Resim artık üzerine çizilen yay ile birlikte kaydedilmiştir.

## Çözüm

Aspose.Imaging for .NET kullanarak bir görüntüde yay çizen basit bir uygulamayı başarıyla oluşturdunuz. Sadece birkaç adımla, artık yaylar ve diğer şekilleri uygulayabilir, görüntü işleme görevlerinize yaratıcı bir hava katabilirsiniz.

## SSS

### Aspose.Imaging for .NET için özel belgeleri nerede bulabilirim?

 Kapsamlı dokümantasyon mevcuttur[Burada](https://reference.aspose.com/imaging/net/).

### Aspose.Imaging for .NET'i nasıl indirebilirim?

 Kütüphaneyi şu adresten indirebilirsiniz:[bu bağlantı](https://releases.aspose.com/imaging/net/).

### Aspose.Imaging for .NET için ücretsiz deneme sürümü mevcut mu?

 Evet, ücretsiz deneme sürümüne erişebilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Imaging for .NET için geçici lisansı nasıl alabilirim?

 Geçici lisans talebinde bulunabilirsiniz[Burada](https://purchase.conholdate.com/temporary-license/).

### Aspose.Imaging for .NET ile ilgili sorularımı nereye sorabilirim veya destek alabilirim?

 Destek ve topluluk tartışmaları için Aspose.Imaging forumunu ziyaret edin[Burada](https://forum.aspose.com/).
