---
title: 1Bpp Dizinli Oluştur
linktitle: 1Bpp Dizinli Oluştur
second_title: Aspose.Words Belge İşleme API'si
description: Bu kılavuz, arşivleme, yazdırma veya yerden tasarruf etme amaçlarıyla 1Bpp dizinli görüntüleri verimli bir şekilde oluşturmanıza yardımcı olacak adım adım talimatlar ve örnek kodlar sağlar.
type: docs
weight: 10
url: /tr/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## giriiş

Hiç bir Word belgesini siyah beyaz bir görüntüye dönüştürmeniz gerekti mi? İster dijital arşivleme, ister yazdırma veya sadece yerden tasarruf için olsun, belgelerinizi 1Bpp dizinli bir görüntüye dönüştürmek inanılmaz derecede faydalı olabilir. Bu kılavuzda, bunu .NET için Aspose.Words kullanarak başarmak için basit bir yöntemden bahsedeceğiz. Başlayalım!

## Ön koşullar

Koda dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: Kütüphaneyi şu adresten indirin ve kurun:[Burada](https://releases.aspose.com/words/net/).
- .NET Geliştirme Ortamı: Visual Studio popüler bir tercih olsa da, .NET'i destekleyen herhangi bir IDE çalışacaktır.
- Temel C# Bilgisi: C#'a aşina olmak faydalı olacaktır, ancak işleri basit tutacağız.
- Örnek Word Belgesi: Dönüştürülmeye hazır bir belgeniz olsun.

## Adım 1: Gerekli Ad Alanlarını İçe Aktarın

Aspose.Words'ü kullanmak için ilgili ad alanlarını içe aktarmanız gerekir. Bu, belge düzenleme için gereken sınıflara ve yöntemlere erişmek için önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 2: Belge Dizininizi Ayarlayın

Word belgenizin saklandığı dizinin yolunu ve dönüştürülen görüntüyü kaydetmek istediğiniz yeri belirtin.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Adım 3: Word Belgesini Yükleyin

Word belgenizi bir`Aspose.Words.Document` nesne. Bu nesne, belgeyi programlı olarak düzenlemenize olanak tanır.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 4: Görüntü Kaydetme Seçeneklerini Yapılandırın

 Sonra, şunu ayarlayın:`ImageSaveOptions` belgenin bir resim olarak nasıl kaydedileceğini tanımlamak için. 1Bpp dizinli renk moduyla PNG formatında kaydedilecek şekilde yapılandıracağız.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Yalnızca ilk sayfayı dönüştür
    ImageColorMode = ImageColorMode.BlackAndWhite, // Siyah ve beyaza ayarla
    PixelFormat = ImagePixelFormat.Format1bppIndexed // 1Bpp dizinli formatı kullanın
};
```

- SaveFormat.Png: Çıktı formatının PNG olacağını belirtir.
- PageSet(1): Belgenin yalnızca ilk sayfasının dönüştürüleceğini belirtir.
- ImageColorMode.BlackAndWhite: Görüntünün siyah beyaz olmasını sağlar.
- ImagePixelFormat.Format1bppIndexed: Piksel biçimini, alanı en iyi duruma getirecek şekilde 1Bpp dizinli olarak ayarlar.

## Adım 5: Belgeyi Görüntü Olarak Kaydedin

 Son olarak, şunu kullanın:`Save` yöntemi`Document` dönüştürülmüş görüntüyü kaydetmek için nesne.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak bir Word belgesini 1Bpp dizinli bir görüntüye başarıyla dönüştürdünüz. Bu yöntem yalnızca verimli olmakla kalmaz, aynı zamanda çeşitli uygulamalar için uygun yüksek kontrastlı görüntüler oluşturmanıza da yardımcı olur. Bu işlevselliği projelerinize entegre etmekten çekinmeyin. İyi kodlamalar!

## SSS

### 1Bpp indeksli görüntü nedir?
1Bpp (Piksel Başına 1 Bit) dizinli görüntü, her pikselin 0 veya 1 olmak üzere tek bir bit ile temsil edildiği siyah beyaz bir görüntü biçimidir. Bu biçim, yerden tasarruf açısından oldukça verimlidir ve arşivleme için idealdir.

### Bir Word belgesinin birden fazla sayfasını aynı anda dönüştürebilir miyim?
 Evet! Sadece şunu değiştirin:`PageSet` mülk`ImageSaveOptions` birden fazla sayfayı dahil etmek veya tüm belgeyi dönüştürmek üzere ayarlamak için.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, tam işlevsellik için bir lisans gereklidir. Bir lisans edinebilirsiniz[burada geçici lisans](https://purchase.aspose.com/temporary-license/).

### Word belgemi hangi diğer görüntü biçimlerine dönüştürebilirim?
 Aspose.Words, JPEG, BMP ve TIFF dahil olmak üzere çeşitli formatları destekler. Sadece`SaveFormat` içinde`ImageSaveOptions`İstediğiniz formata.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
 Kapsamlı dokümantasyon için şu adresi ziyaret edin:[Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/).