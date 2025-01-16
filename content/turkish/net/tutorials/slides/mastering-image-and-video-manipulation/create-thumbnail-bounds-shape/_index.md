---
title: Aspose.Slides'ta Şekil için Sınırlarla Küçük Resim Oluşturma
linktitle: Aspose.Slides'ta Şekil için Sınırlarla Küçük Resim Oluşturma
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: PowerPoint sunumlarındaki şekiller için tanımlanmış sınırlara sahip küçük resim görüntüleri oluşturmak için Aspose.Slides for .NET'i nasıl kullanacağınızı öğrenin. Bu kapsamlı kılavuz adım adım talimatlar sağlar.
type: docs
weight: 10
url: /tr/net/tutorials/slides/mastering-image-and-video-manipulation/create-thumbnail-bounds-shape/
---
## giriiş

PowerPoint sunumlarında şekiller için sınırlar içeren küçük resim görüntüleri oluşturmanın etkili bir yolunu arayan bir .NET geliştiricisiyseniz, Aspose.Slides for .NET dikkate alınması gereken mükemmel bir araçtır. Bu sağlam kütüphane, PowerPoint dosyalarının işlenmesini basitleştirerek değerli verileri sorunsuz bir şekilde çıkarmanızı ve bunlarla çalışmanızı sağlar. Bu eğitimde, bir şekil için sınırlar içeren bir küçük resim oluşturma sürecinde size rehberlik edeceğiz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Slides for .NET Kütüphanesi: Buradan indirin ve kurun[Aspose'un sitesi](https://releases.aspose.com/slides/net/).
2.  Dosya Yolu: Değiştir`"Your Documents Directory"` Belgelerinizin gerçek yolunu içeren kodda.

## Gerekli Ad Alanlarını İçe Aktar

Aspose.Slides'ın özelliklerini kullanmak için öncelikle projenizin başlangıcında gerekli ad alanlarını içe aktarın:

```csharp
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Slides;
```

## Adım 1: Sunum Sınıfını Örneklendirin

 İlk olarak, şunu başlatmanız gerekir:`Presentation` PowerPoint dosyanızı temsil edecek sınıf:

```csharp
string dataDir = "Your Documents Directory\\";
using (Presentation presentation = new Presentation(dataDir + "HelloWorld.pptx"))
{
    // Sunum nesneniz artık düzenlenmeye hazır.
}
```

 Kullanımı`using` Buradaki ifade, işiniz bittikten sonra kaynakların uygun şekilde serbest bırakılmasını sağlar.

## Adım 2: Şekil Sınırları Olan Bir Küçük Resim Görüntüsü Oluşturun

Daha sonra, sununuzdaki bir şeklin belirtilen sınırlarla küçük resmini oluşturacaksınız:

```csharp
using (Bitmap bitmap = presentation.Slides[0].Shapes[0].GetThumbnail(ShapeThumbnailBounds.Appearance, 1, 1))
{
    // Bitmap artık tanımlanmış sınırlar içerisinde küçük resim görüntüsünü içeriyor.
}
```

 Bu kesitte,`ShapeThumbnailBounds.Appearance` şeklin görünüm sınırlarını istediğinizi belirtir. Çıkış gereksinimlerinize göre genişlik ve yükseklik için parametreleri (1, 1) gerektiği gibi ayarlayın.

## Adım 3: Küçük Resim Görüntüsünü Diske Kaydedin

Son olarak, oluşturulan küçük resim görüntüsünü PNG gibi tercih ettiğiniz bir biçimde kaydedin:

```csharp
bitmap.Save(dataDir + "Shape_thumbnail_Bound_Shape_out.png", ImageFormat.Png);
```

Burada projenizin ihtiyaçlarına göre dosya adını ve formatını özelleştirebilirsiniz.

Tebrikler! Aspose.Slides for .NET kullanarak bir şeklin sınırlarıyla birlikte bir küçük resim başarıyla oluşturdunuz. Bu işlem basittir ve .NET uygulamalarınıza kolayca entegre edilebilir.

## Çözüm

Aspose.Slides for .NET, PowerPoint sunumlarının oluşturulması ve yönetilmesi işlemini kolaylaştırır ve geliştiricilere küçük resimler ve daha fazlasını oluşturmak için güçlü araçlar sağlar. Bu kılavuzu izleyerek, bu kütüphaneyi projelerinizde verimli bir şekilde kullanmak için gerekli adımları öğrendiniz.

## SSS

### Aspose.Slides en son .NET framework ile uyumlu mu?

Evet, Aspose.Slides .NET framework'ün en son sürümlerini destekleyecek şekilde sık sık güncellenmektedir.

### Aspose.Slides'ı ticari projelerde kullanabilir miyim?

 Kesinlikle! Aspose.Slides, bireysel ve ticari kullanıma uygun çeşitli lisanslama seçenekleri sunar. Kontrol edin[Burada](https://purchase.aspose.com/buy) Daha fazla bilgi için.

### Ücretsiz deneme imkanı var mı?

 Evet! Aspose.Slides'ın özelliklerini ücretsiz deneme sürümüyle keşfedebilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Slides için nasıl destek alabilirim?

Yardım için şu adresi ziyaret edin:[Aspose.Slides forumu](https://forum.aspose.com/c/slides/11) Topluluk ve deneyimli geliştiricilerle bağlantı kurmak.

### Aspose.Slides için geçici lisans alabilir miyim?

 Evet, kısa vadeli projeler için geçici lisanslar alınabilir[Burada](https://purchase.aspose.com/temporary-license/).