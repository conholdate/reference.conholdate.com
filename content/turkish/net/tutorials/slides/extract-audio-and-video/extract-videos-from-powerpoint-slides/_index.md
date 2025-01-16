---
title: Aspose.Slides ile PowerPoint Slaytlarından Videoları Çıkarın
linktitle: PowerPoint Slaytlarından Videoları Çıkarın
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: Aspose.Slides for .NET kullanarak PowerPoint sunumlarından gömülü video dosyalarını nasıl kolayca çıkaracağınızı keşfedin. Bu kapsamlı adım adım kılavuz, ortamınızı kurmaktan çıkarılan videoları kaydetmeye kadar her şeyi kapsar.
type: docs
weight: 14
url: /tr/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## giriiş

Aspose.Slides for .NET, geliştiricilerin PowerPoint sunumlarıyla programatik olarak etkileşim kurmasını sağlayan güçlü bir kütüphanedir. Bu kılavuzda, Aspose.Slides for .NET kullanarak PowerPoint slaytlarına gömülü videoları çıkarma sürecinde size yol göstereceğiz. 

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Slides for .NET: Kütüphaneyi şuradan edinin ve yükleyin:[Aspose web sitesi](https://purchase.aspose.com/buy).
-  PowerPoint Sunumu: Bir PowerPoint dosyası hazırlayın (örneğin,`Video.pptx`) çıkarmak istediğiniz video ile birlikte.

## Gerekli Ad Alanları

.NET için Aspose.Slides ile çalışmak için uygun ad alanlarını içe aktarmanız gerekir. Kodunuza şunları ekleyin:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Adım 1: Belge Dizinini Belirleyin

Öncelikle PowerPoint sunumunuza giden yolu tanımlayın:

```csharp
string dataDir = "Your Document Directory";
```

 Yer değiştirmek`"Your Document Directory"` PowerPoint dosyanızın bulunduğu dizinin gerçek yolunu belirtin.

## Adım 2: Sunumu Yükleyin

 PowerPoint sunumunu bir`Presentation` nesne:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Bu, şunu başlatır:`Presentation` Belirtilen PowerPoint dosyanızla nesneyi oluşturun.

## Adım 3: Slaytlar ve Şekiller Arasında Gezinin

Daha sonra sunumdaki her slaydı inceleyin ve video karelerini kontrol edin:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Videoyu çıkarmaya devam edin
        }
    }
}
```

## Adım 4: Video Verilerini Çıkarın

Bir video karesi bulduğunuzda, onun özelliklerini ve ikili verilerini çıkarın:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Şekli bir video karesi olarak sakla
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Dosya uzantısını al
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Adım 5: Videoyu Kaydedin

Son olarak çıkarılan video verilerini bir dosyaya yazın:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Bu kod belirttiğiniz dizinde yeni bir dosya oluşturur ve video verilerini bu dosyanın içine yazar.

## Çözüm

Aspose.Slides for .NET ile PowerPoint slaytlarından video çıkarmak basit bir işlemdir. Bu kılavuzu izleyerek, .NET uygulamalarınızdaki multimedya içeriklerini kolayca yönetebilir, kullanıcı deneyimini ve işlevselliğini zenginleştirebilirsiniz.

## SSS

### Aspose.Slides for .NET nedir?
Aspose.Slides for .NET, PowerPoint sunumlarıyla çalışmak üzere tasarlanmış bir kütüphanedir ve kullanıcıların sunum dosyalarını programlı bir şekilde oluşturmasına, düzenlemesine ve değiştirmesine olanak tanır.

### Aspose.Slides for .NET'in belgelerini nerede bulabilirim?
 Tam dokümantasyona erişebilirsiniz[Burada](https://reference.aspose.com/slides/net/).

### Aspose.Slides for .NET ücretsiz deneme için mevcut mu?
 Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[bu bağlantı](https://releases.aspose.com/).

### Aspose.Slides for .NET için geçici lisansı nasıl alabilirim?
 Geçici lisans talepleri yapılabilir[Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.Slides for .NET için desteği nereden alabilirim?
 Destek şu şekilde mevcuttur:[Aspose.Slides forumu](https://forum.aspose.com/).