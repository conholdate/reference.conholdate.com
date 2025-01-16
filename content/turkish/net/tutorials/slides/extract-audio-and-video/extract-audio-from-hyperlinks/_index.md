---
title: Aspose.Slides Kullanarak PowerPoint'teki Köprülerden Ses Çıkarma
linktitle: Köprülerden Sesi Çıkar
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: Aspose.Slides for .NET ile PowerPoint sunumlarındaki köprülerden ses çıkarmayı öğrenin. Bu adım adım kılavuz net talimatlar sağlar.
type: docs
weight: 12
url: /tr/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## giriiş

Multimedya sunumlarında, ses slaytlarınızın etkisini önemli ölçüde artırır. Ses köprüleri olan bir PowerPoint sunumuyla karşılaştıysanız ve bu sesi başka kullanımlar için nasıl çıkaracağınızı merak ettiyseniz, doğru yerdesiniz. Bu kılavuz, Aspose.Slides for .NET kitaplığını kullanarak bir PowerPoint sunumundaki köprülerden ses çıkarma sürecinde size yol gösterecektir.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

### Aspose.Slides .NET Kütüphanesi için

 Aspose.Slides for .NET kütüphanesinin yüklü olduğundan emin olun. Eğer henüz yapmadıysanız, şuradan indirebilirsiniz:[Aspose.Slides .NET Belgeleri için](https://reference.aspose.com/slides/net/).

### Sesli Bağlantılı PowerPoint Sunumu

İlişkili sese sahip köprüler içeren bir PowerPoint sunumuna (PPTX) ihtiyacınız olacak. Bu sunum ses çıkarma kaynağınız olacak.

## Gerekli Ad Alanlarını İçe Aktarma

Aspose.Slides for .NET'i etkili bir şekilde kullanmak için, aşağıdaki ad alanlarını C# projenize aktarmanız gerekir:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Artık her şey yerli yerinde olduğuna göre, çıkarma işlemini kolay adımlara bölelim.

## Adım 1: Belge Dizinini Tanımlayın

 PowerPoint sunumunuzun bulunduğu dizini belirterek başlayın. Değiştir`"Your Document Directory"` gerçek yol ile.

```csharp
string dataDir = "Your Document Directory";
```

## Adım 2: PowerPoint Sunumunu Yükleyin

 Sonra, ses bağlantısını içeren PowerPoint sunumunu (PPTX) yükleyin. Değiştir`"HyperlinkSound.pptx"` gerçek sunum dosya adınızla.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Bir sonraki adıma geçin.
}
```

## Adım 3: Köprü Sesi'ne erişin

İlk slayttaki ilk şekilden köprü metnini alın. Bu köprü metninin ilişkili bir sesi varsa, onu çıkarmaya devam edebiliriz.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Bir sonraki adıma geçin.
}
```

## Adım 4: Köprü metninden Sesi Çıkarın

Eğer köprü metni ses içeriyorsa, bunu bayt dizisi olarak çıkarıp medya dosyası olarak kaydedebiliriz.

```csharp
// Köprü sesini bir bayt dizisi olarak çıkarın
byte[] audioData = link.Sound.BinaryData;

// Çıkarılan sesi kaydetmek istediğiniz yolu belirtin
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Çıkarılan sesi bir medya dosyasına kaydedin
File.WriteAllBytes(outMediaPath, audioData);
```

Tebrikler! Aspose.Slides for .NET kullanarak bir PowerPoint sunumundaki bir köprü metninden sesi başarıyla çıkardınız. Artık bu sesi multimedya projelerinizde kullanabilirsiniz.

## Çözüm

Aspose.Slides for .NET, PowerPoint sunumlarındaki köprülerden ses çıkarmak için güçlü ve kullanıcı dostu bir yol sunar. Bu kılavuzda özetlenen adımlarla, projelerinizi geliştirmek için sunumlarınızdaki ses içeriğini kolayca yeniden kullanabilirsiniz.

## SSS

### Aspose.Slides for .NET ücretsiz bir kütüphane midir?
 Hayır, Aspose.Slides for .NET ticari bir kütüphanedir, ancak özelliklerini keşfetmek için ücretsiz deneme sürümünü indirebilirsiniz.[Burada](https://releases.aspose.com/).

### PPT gibi eski PowerPoint formatlarından ses çıkarabilir miyim?
Evet, Aspose.Slides for .NET ses ayıklama için hem PPTX hem de PPT formatlarını destekler.

### Aspose.Slides desteği için bir topluluk forumu var mı?
 Kesinlikle! Yardım alabilir ve deneyimlerinizi paylaşabilirsiniz.[Aspose.Slides topluluk forumu](https://forum.aspose.com/).

### Kısa süreli bir proje için Aspose.Slides için geçici bir lisans satın alabilir miyim?
Evet, kısa vadeli proje ihtiyaçlarınız için geçici lisansı şu adresi ziyaret ederek alabilirsiniz:[bu bağlantı](https://purchase.aspose.com/temporary-license/).

### MPG dışında çıkarma için desteklenen başka ses formatları var mı?
Evet, Aspose.Slides for .NET çeşitli ses formatlarında çıkarma işlemine izin verir. Çıkardıktan sonra sesi tercih ettiğiniz formata dönüştürebilirsiniz.