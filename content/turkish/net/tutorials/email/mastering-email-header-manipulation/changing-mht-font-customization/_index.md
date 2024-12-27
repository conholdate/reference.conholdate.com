---
title: C# kullanarak MHT Yazı Tipi Özelleştirmesini Değiştirme
linktitle: C# kullanarak MHT Yazı Tipi Özelleştirmesini Değiştirme
second_title: Aspose.Email .NET E-posta İşleme API'si
description: Aspose.Email for .NET kullanarak MHT dönüşümü sırasında yazı tiplerini nasıl değiştireceğinizi öğrenin. Kolay özelleştirme için bu adım adım kılavuzu izleyin.
type: docs
weight: 11
url: /tr/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## giriiş

Web iletişimi dünyasında, MHT (MHTML) dosyaları, görseller, bağlantılar ve stiller ile birlikte web içeriğini depolamak ve paylaşmak için kullanışlı bir yoldur. Peki, yazı tiplerini değiştirerek bu MHT dosyalarını güzelleştirmeniz gerektiğinde ne olur? Aspose.Email for .NET sayesinde, bu görev çocuk oyuncağı haline geliyor. Bu eğitimde, MHT dönüşümü sırasında yazı tiplerini değiştirme sürecini adım adım anlatacağız. E-posta biçimlendirmesini işleyen bir uygulama geliştiriyor veya yalnızca işletmeniz için belgeleri özelleştirmek istiyorsanız, bu kılavuz size ihtiyacınız olan bilgiyi sağlayacaktır.

## Ön koşullar

Koda dalmadan önce hazırlamanız gereken birkaç temel şey var:

1. Visual Studio: C# projeniz üzerinde çalışmak için entegre bir geliştirme ortamına (IDE) ihtiyacınız olacak.
2.  Aspose.Email for .NET Library: Kütüphanenin kurulu olduğundan emin olun. Bunu şuradan indirebilirsiniz:[bağlantı](https://releases.aspose.com/email/net/).
3. .NET Framework: Projeniz .NET Framework ile uyumlu olmalıdır; genellikle .NET Core veya sonraki sürümler iyi çalışır.

Bunları sıraladınız mı? Harika! Başlayalım.

## Paketleri İçe Aktarma

Öncelikle, projenizin gerekli ad alanlarını kullanacak şekilde ayarlandığından emin olun. C# dosyanızın en üstüne şunları eklemek isteyeceksiniz:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

Bu paketler, MHT dosyalarıyla çalışmak ve içeriklerini değiştirmek için gereken işlevselliğe erişmenizi sağlayacaktır.

Şimdi, MHT dönüşümü sırasında yazı tiplerini değiştirmenin adımlarını inceleyelim.

## Adım 1: MHT Dosyasını Yükleyin

 Yapmanız gereken ilk şey MHT dosyanızı bir`MailMessage` nesne. İçeriğine erişebileceğiniz ve onu düzenleyebileceğiniz yer burasıdır.

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 Açıklama: Burada,`"input.mht"` MHT dosyanızın yoludur.`MhtmlLoadOptions()`dosyanın nasıl yükleneceğini, örneğin ekleri veya bağlantılı kaynakları farklı şekilde işlemeyi yapılandırmanıza olanak tanır.

## Adım 2: Alternatif Görünümler Arasında Yineleme Yapın

MHT dosyaları genellikle birden fazla alternatif görünüme sahiptir, özellikle de HTML içeriği içeriyorlarsa. Değiştirmek istediğinizi bulmak için bu görünümler arasında döngü yapmanız gerekir.

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 Açıklama: Her birini kontrol ediyorsunuz`AlternateView` HTML türünde olup olmadığını görmek için. Eğer öyleyse, erişebilirsiniz`LinkedResources`HTML'de bağlantılı olan tüm yazı tiplerinin genellikle saklandığı yer.

## Adım 3: Yazı Tiplerini Tanımlayın ve Özelleştirin

Artık bağlantılı kaynaklara erişebildiğinize göre, hangi kaynakların yazı tipi olduğunu belirleyebilir ve bunları gerektiği gibi özelleştirebilirsiniz.

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // İstediğiniz yazı tipine geçin
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // Doğru şekilde kodlandığından emin olun
    }
}
```

 Açıklama: Bu döngü, bağlantılı kaynağın içerik türünün TrueType yazı tipi olup olmadığını kontrol eder. Eşleşirse, yazı tipinin adını istediğiniz şekilde değiştirebilirsiniz (bu örnekteki "Arial" gibi).`TransferEncoding`Ayrıca, belge kaydedildiğinde yazı tipi verilerinin doğru şekilde kodlanmasını sağlamak için ayarlanmalıdır.

## Adım 4: Güncellenen MHT Dosyasını Kaydedin

Yazı tiplerini özelleştirdikten sonra, değiştirilmiş MHT dosyanızı kaydetme zamanı geldi. Dosyanızın bütünlüğünü korumak için doğru kaydetme seçeneklerini kullandığınızdan emin olmak isteyeceksiniz.

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 Açıklama: Bu kod satırında,`"output.mht"` güncellenen içeriği kaydetmek istediğiniz dosyanın adıdır.`SaveOptions.DefaultMhtml` yeni dosyanın MHT formatını korumasını sağlar.

## Çözüm

MHT dosyalarındaki yazı tiplerini değiştirmek belgelerinizin görünümünü ve hissini önemli ölçüde iyileştirebilir. Aspose.Email for .NET'i kullanarak MHT dosyalarını kolayca yükleyebilir, içeriklerini değiştirebilir ve değişiklikleri yalnızca birkaç satır kod kullanarak kaydedebilirsiniz. İster kişisel bir proje ister daha büyük bir uygulama üzerinde çalışıyor olun, bu becerilerde ustalaşmak bilgileri sunma şeklinizi iyileştirebilir.

## SSS

### MHT formatı nedir?
MHT, HTML belgelerini, resimleri ve diğer kaynakları tek bir dosyada depolayan bir web sayfası arşiv biçimidir.

### Aspose kullanarak MHT dosyalarının diğer yönlerini değiştirebilir miyim?
Kesinlikle! Aspose.Email, ekler, başlıklar ve daha fazlası dahil olmak üzere MHT dosyalarının hemen hemen her yönünü değiştirmenize olanak tanır.

### Aspose.Email for .NET ücretsiz mi?
 Aspose ücretsiz deneme sunuyor ancak tam sürüm için lisans gerekiyor. Geçici bir lisansı şuradan alabilirsiniz:[Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.Email hakkında daha fazla dokümanı nerede bulabilirim?
 Kapsamlı dokümanları ve örnekleri şu adreste bulabilirsiniz:[Aspose E-posta dokümantasyon sayfası](https://reference.aspose.com/email/net/).

### Aspose kullanırken sorunlarla karşılaşırsam ne olur?
 Herhangi bir sorunla karşılaşırsanız, destek almak için bize ulaşabilirsiniz.[Aspose destek forumu](https://forum.aspose.com/c/email/12/).